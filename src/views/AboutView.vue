<template>
   <link rel="icon" type="image/x-icon" href="pfp.ico">
   <title> luke.tf </title>
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

@keyframes float {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
  100% {
    transform: translateY(0);
  }
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
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
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  will-change: transform, box-shadow;
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
    transform: translateY(-8px);
    box-shadow: 0 8px 15px rgba(0,0,0,0.08);
  }
  
  &:active {
    transform: scale(0.98);
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
  transition: transform 0.2s ease;
  cursor: default;
  
  &:hover {
    transform: scale(1.05);
  }
}

.project-links {
  display: flex;
  gap: 1rem;
  a {
    transition: color 0.3s ease, transform 0.3s ease;
    position: relative;
    
    &::after {
      content: '';
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 0;
      height: 1px;
      background-color: var(--accent);
      transition: width 0.2s ease;
    }
    
    &:hover::after {
      width: 100%;
    }
    
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
      transition: padding-left 0.2s ease, color 0.2s ease;
      cursor: default;
      
      &:last-child {
        border-bottom: none;
      }

      &:hover {
        padding-left: 10px;
        color: var(--accent);
      }
    }
  }
}

.about-section {
  position: relative;
  overflow: hidden;
  
  &::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(
      circle at center, 
      rgba(16, 146, 79, 0.1), 
      transparent 70%
    );
    animation: pulse 5s infinite;
    pointer-events: none;
    z-index: -1;
  }
}

.bio-section {
  position: relative;
  
  .bio-text {
    position: relative;
    
    &::after {
      content: '';
      position: absolute;
      bottom: -5px;
      left: 0;
      width: 0;
      height: 3px;
      background-color: var(--accent);
      transition: width 0.5s ease;
    }
    
    &:hover::after {
      width: 100%;
    }
  }
}

.projects-section {
  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1.5rem;
  }
  
  .project-card {
    position: relative;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 1rem;
    padding: 1.5rem;
    transition: all 0.3s ease;
    cursor: pointer;
    
    &::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: linear-gradient(45deg, transparent, rgba(255,255,255,0.05));
      opacity: 0;
      transition: opacity 0.3s ease;
      pointer-events: none;
      border-radius: 1rem;
    }
    
    &:hover {
      transform: translateY(-15px) rotate(1deg);
      box-shadow: 0 20px 40px rgba(0,0,0,0.2);
      
      &::before {
        opacity: 1;
      }
      
      .project-link {
        color: var(--accent);
        text-decoration: underline;
      }
      
      .project-icon {
        transform: scale(1.1) rotate(5deg);
      }
    }
    
    &:active {
      transform: scale(0.98);
    }
    
    .project-icon {
      font-size: 2rem;
      transition: transform 0.3s ease;
      color: var(--accent);
      margin-bottom: 1rem;
    }
    
    .project-link {
      transition: all 0.3s ease;
      display: inline-block;
      margin-top: 1rem;
    }
  }
}

@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
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
