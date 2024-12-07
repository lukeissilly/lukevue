<template>
  <div class="about-container">
    <section class="bio-section">
      <h1>About Me</h1>
      <div class="bio-content">
        <div class="bio-text">
          <p>
            Hi, I'm Luke.
          </p>
          <p>
            Ever since I was a kid, I've been weirdly obsessed with technology and computers as a whole, which has led me down a rabbit hole of learning about almost everything related to computers.
          </p>
        </div>
        <div class="bio-skills">
          <h2>Interests</h2>
          <ul>
            <li>Programming</li>
            <li>Computer Hardware</li>
            <li>Software Development</li>
            <li>Film Making</li>
          </ul>
        </div>
      </div>
    </section>

    <h1>Projects</h1>
    <div class="projects-grid">
      <div v-for="(project, index) in projects" :key="index" class="project-card">
        <div class="card-content">
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-description">{{ project.description }}</p>
          <div class="tech-stack">
            <span v-for="tech in project.technologies" :key="tech" class="tech-tag">
              {{ tech }}
            </span>
          </div>
          <div class="project-links">
            <a v-if="project.github" :href="project.github" target="_blank" rel="noopener" class="project-link">
              GitHub <i class="pi pi-github"></i>
            </a>
            <a v-if="project.demo" :href="project.demo" target="_blank" rel="noopener" class="project-link">
                Link <i class="pi pi-external-link"></i>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const projects = [
  {
    title: 'Silly Fediverse Instance',
    description: 'A silly fediverse instance ran on Sharkey',
    technologies: ['Fediverse', 'Social Media'],
    demo: 'https://imsilly.fyi'
  },
  {
    title: 'Cat Picture Website',
    description: 'I decided to put all my cat images to good use',
    technologies: ['Web Development', 'Fun Project'],
    demo: 'https://cat.luke.tf'
  },
  {
    title: 'AI Website Showcase',
    description: 'AI is stinky',
    technologies: ['AI', 'Web Development'],
    demo: 'https://ai.luke.tf'
  },
  {
    title: 'Shitty Pepsi Minecraft Mod',
    description: 'This was when I learnt that Java is hard',
    technologies: ['Minecraft', 'Modding'],
    github: 'https://github.com/lukeisuh/Shitty-Pepsi-Mod'
  },
  {
    title: 'Number Guessing Website',
    description: 'A poorly made number guessing game.',
    technologies: ['Web Development', 'Games'],
    demo: 'https://number.luke.tf/'
  },
  {
    title: 'Nothing Website',
    description: 'A website about doing nothing.',
    technologies: ['Web Development', 'Experimental'],
    demo: 'https://nothing.luke.tf/'
  }
]
</script>

<style lang="scss" scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.about-container {
  min-height: 100vh;
  padding: 6rem 2rem 4rem;
  max-width: 1200px;
  margin: 0 auto;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards;
}

h1 {
  font-size: 2.5rem;
  font-weight: 900;
  color: var(--accent);
  text-align: center;
  margin-bottom: 2rem;
  letter-spacing: -0.05em;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.project-card {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 1rem;
  padding: 2rem;
  position: relative;
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.1);
  opacity: 0;
  animation: fadeInUp 0.6s ease forwards;
  
  &:nth-child(1) { animation-delay: 0.3s; }
  &:nth-child(2) { animation-delay: 0.4s; }
  &:nth-child(3) { animation-delay: 0.5s; }
  &:nth-child(4) { animation-delay: 0.6s; }
  &:nth-child(5) { animation-delay: 0.7s; }
  &:nth-child(6) { animation-delay: 0.8s; }
  &:nth-child(7) { animation-delay: 0.9s; }

  &:hover {
    transform: translateY(-10px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
  }
}

.card-content {
  position: relative;
  z-index: 1;
}

.project-title {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: var(--accent);
}

.project-description {
  color: var(--text);
  margin-bottom: 1.5rem;
  line-height: 1.6;
  opacity: 0.9;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  background: rgba(0, 255, 157, 0.1);
  color: var(--accent);
  padding: 0.4rem 0.8rem;
  border-radius: 2rem;
  font-size: 0.875rem;
  transition: all 0.3s ease;
  
  &:hover {
    background: rgba(0, 255, 157, 0.2);
  }
}

.project-links {
  display: flex;
  gap: 1rem;
  a {
    transition: all 0.3s ease;
    
    &:hover {
      color: var(--accent);
      transform: translateX(5px);
    }
  }
}

.bio-section {
  margin-bottom: 4rem;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards 0.2s;
}

.bio-content {
  display: flex;
  gap: 2rem;
  align-items: flex-start;

  @media (max-width: 768px) {
    flex-direction: column;
  }
}

.bio-text {
  flex: 2;
  
  p:first-child {
    text-align: center;
    font-size: 2.5rem;
    font-weight: 900;
    margin-bottom: 2rem;
    color: var(--accent);
    letter-spacing: -0.05em;
    position: relative;
    
    &::after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 50%;
      transform: translateX(-50%);
      width: 100px;
      height: 4px;
      background: var(--accent);
      opacity: 0.7;
    }
  }

  p:last-child {
    position: relative;
    font-size: 1.1rem;
    line-height: 1.8;
    color: var(--text);
    padding: 1.5rem;
    background: rgba(255, 255, 255, 0.03);
    border-radius: 12px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    transition: all 0.3s ease;
    
    &:hover {
      transform: scale(1.02);
      box-shadow: 0 10px 30px rgba(0,0,0,0.05);
    }
  }
}

.bio-skills {
  flex: 1;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 1rem;
  padding: 1.5rem;
  border: 1px solid rgba(255, 255, 255, 0.1);

  h2 {
    margin-bottom: 1rem;
    color: var(--accent);
    font-size: 1.2rem;
  }

  ul {
    list-style-type: none;
    padding: 0;

    li {
      padding: 0.5rem 0;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
      color: var(--text);
      opacity: 0.8;
      transition: all 0.3s ease;
      cursor: default;
      
      &:last-child {
        border-bottom: none;
      }

      &:hover {
        color: var(--accent);
        transform: translateX(15px);
      }
    }
  }
}

@media (max-width: 768px) {
  .about-container {
    padding: 2rem 1rem;
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .project-card {
    padding: 1.5rem;
  }
}
</style>
