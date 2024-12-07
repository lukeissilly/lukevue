<template>
  <div class="about-container">
    <h1 class="glitch" data-text="Projects">Projects</h1>
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
              Demo <i class="pi pi-external-link"></i>
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
    title: 'Portfolio Website',
    description: 'A modern, dynamic portfolio built with Vue 3 and TypeScript, featuring smooth animations and interactive elements.',
    technologies: ['Vue 3', 'TypeScript', 'SCSS'],
    github: 'https://github.com/yourusername/portfolio',
    demo: 'https://yourwebsite.com'
  },
  {
    title: 'Project Name',
    description: 'Description of your amazing project goes here. Talk about what problems it solves and its impact.',
    technologies: ['React', 'Node.js', 'MongoDB'],
    github: 'https://github.com/yourusername/project',
    demo: 'https://project-demo.com'
  },
  {
    title: 'Another Project',
    description: 'Another fantastic project description. Highlight the key features and technologies used.',
    technologies: ['Python', 'Django', 'PostgreSQL'],
    github: 'https://github.com/yourusername/another-project'
  }
]
</script>

<style lang="scss" scoped>
.about-container {
  min-height: 100vh;
  padding: 4rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.glitch {
  font-size: 4rem;
  font-weight: 900;
  color: var(--text);
  position: relative;
  text-align: center;
  margin-bottom: 3rem;
  text-shadow: 0.05em 0 0 var(--accent), 
               -0.025em -0.05em 0 rgba(255,0,0,0.75),
               0.025em 0.05em 0 rgba(0,255,255,0.75);
  animation: glitch 500ms infinite;
  
  &::before,
  &::after {
    content: attr(data-text);
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    color: var(--text);
  }
  
  &::before {
    left: 2px;
    text-shadow: -2px 0 var(--accent);
    clip: rect(24px, 550px, 90px, 0);
    animation: glitch-anim 3s infinite linear alternate-reverse;
  }
  
  &::after {
    left: -2px;
    text-shadow: -2px 0 var(--accent);
    clip: rect(85px, 550px, 140px, 0);
    animation: glitch-anim 2s infinite linear alternate-reverse;
  }
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
  
  &:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.08);
    border-color: var(--accent);
    
    .project-link {
      color: var(--accent);
    }
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
}

.project-link {
  color: var(--text);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
  font-size: 0.9rem;
  opacity: 0.8;
  
  &:hover {
    opacity: 1;
  }
  
  i {
    font-size: 1rem;
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes glitch-anim {
  0% {
    clip: rect(44px, 9999px, 99px, 0);
  }
  20% {
    clip: rect(12px, 9999px, 59px, 0);
  }
  40% {
    clip: rect(63px, 9999px, 92px, 0);
  }
  60% {
    clip: rect(23px, 9999px, 78px, 0);
  }
  80% {
    clip: rect(88px, 9999px, 44px, 0);
  }
  100% {
    clip: rect(32px, 9999px, 67px, 0);
  }
}

@keyframes glitch {
  0% {
    text-shadow: 0.05em 0 0 var(--accent), 
                -0.025em -0.05em 0 rgba(255,0,0,0.75),
                0.025em 0.05em 0 rgba(0,255,255,0.75);
  }
  14% {
    text-shadow: 0.05em 0 0 var(--accent), 
                -0.025em -0.05em 0 rgba(255,0,0,0.75),
                0.025em 0.05em 0 rgba(0,255,255,0.75);
  }
  15% {
    text-shadow: -0.05em -0.025em 0 var(--accent),
                0.025em 0.025em 0 rgba(255,0,0,0.75),
                -0.05em -0.05em 0 rgba(0,255,255,0.75);
  }
  49% {
    text-shadow: -0.05em -0.025em 0 var(--accent),
                0.025em 0.025em 0 rgba(255,0,0,0.75),
                -0.05em -0.05em 0 rgba(0,255,255,0.75);
  }
  50% {
    text-shadow: 0.025em 0.05em 0 var(--accent),
                0.05em 0 0 rgba(255,0,0,0.75),
                0 -0.05em 0 rgba(0,255,255,0.75);
  }
  99% {
    text-shadow: 0.025em 0.05em 0 var(--accent),
                0.05em 0 0 rgba(255,0,0,0.75),
                0 -0.05em 0 rgba(0,255,255,0.75);
  }
  100% {
    text-shadow: -0.025em 0 0 var(--accent),
                -0.025em -0.025em 0 rgba(255,0,0,0.75),
                -0.025em -0.05em 0 rgba(0,255,255,0.75);
  }
}

@media (max-width: 768px) {
  .about-container {
    padding: 2rem 1rem;
  }
  
  .glitch {
    font-size: 3rem;
    margin-bottom: 2rem;
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .project-card {
    padding: 1.5rem;
  }
}
</style>
