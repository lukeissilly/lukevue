<template>
   <link rel="icon" type="image/x-icon" href="pfp.ico">
   <title> luke.tf </title>
  <div class="social">
    <div class="hero">
      <h1>Socials</h1>
      <p class="subtitle">Just incase you want to stalk me :p</p>
    </div>

    <div class="social-grid">
      <div 
        v-for="platform in platforms" 
        :key="platform.name" 
        class="social-card"
        @click="openLink(platform.link)"
        @keydown.enter="openLink(platform.link)"
        tabindex="0"
        role="button"
        :aria-label="`Open ${platform.name} profile`"
      >
        <div class="card-content">
          <div class="platform-icon">
          </div>
          <h3>{{ platform.name }}</h3>
          <p>{{ platform.description }}</p>
          <a :href="platform.link" 
             target="_blank" 
             class="platform-link"
             :style="{ '--color': platform.color }">
            {{ platform.username }}
            <i class="pi pi-external-link"></i>
          </a>
        </div>
        <div class="card-glow"></div>
      </div>
    </div>

    <div class="contact-section">
      <div class="contact-content">
        <h2 class="section-title">Get in Touch</h2>
        <p class="contact-text">
          Email me if you want. I'm not sure why you would want to but you can.
        </p>
        <a href="mailto:mail@luke.tf" class="contact-button">
          Send a Message
          <i class="pi pi-send"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const platforms = [
  {
    name: 'GitHub',
    username: '@lukeissilly',
    description: 'I am planning to make some open source projects soon :)',
    link: 'https://github.com/lukeissilly',
    color: '#6e5494'
  },
  {
    name: 'Bluesky',
    username: '@luke.tf',
    description: 'Follow me if you want weird posts and stuff like that',
    link: 'https://bsky.app/profile/luke.tf',
    color: '#1DA1F2'
  },
  {
    name: 'Discord',
    username: 'luke.tf',
    description: 'I will probably never dm you but you can friend me if you like',
    link: 'https://discordlookup.com/user/385344110778908674',
    color: '#7289DA'
  }
]

function openLink(link: string) {
  window.open(link, '_blank')
}
</script>

<style lang="scss" scoped>
.social {
  min-height: 100vh;
  padding: 6rem 2rem 4rem;
  max-width: 1200px;
  margin: 0 auto;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards;
}

.hero {
  text-align: center;
  margin-bottom: 4rem;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards 0.2s;
  
  h1 {
    font-size: 2.5rem;
    font-weight: 900;
    color: var(--accent);
    text-align: center;
    margin-bottom: 1rem;
    letter-spacing: -0.05em;
    position: relative;
    display: inline-block;
    
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

.subtitle {
  color: var(--text);
  font-size: 1rem;
  opacity: 0.8;
  text-align: center;
}

.social-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  
  .social-card {
    background: rgba(255, 255, 255, 0.05);
    border-radius: 1rem;
    padding: 2rem;
    position: relative;
    overflow: hidden;
    border: 1px solid rgba(255, 255, 255, 0.1);
    transition: all 0.3s ease;
    opacity: 0;
    animation: fadeInUp 0.6s ease forwards;
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
    
    &:nth-child(1) { animation-delay: 0.3s; }
    &:nth-child(2) { animation-delay: 0.4s; }
    &:nth-child(3) { animation-delay: 0.5s; }
    
    &:hover {
      &::before {
        opacity: 1;
      }
      
      transform: translateY(-10px) rotate(1deg);
      box-shadow: 0 15px 30px rgba(0,0,0,0.2);
      
      .platform-link {
        i {
          transform: translateX(5px);
        }
      }
    }
    
    &:active {
      transform: scale(0.98);
    }
  }
}

.card-content {
  position: relative;
  z-index: 1;
}

h3 {
  color: var(--text);
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

p {
  color: var(--text);
  opacity: 0.8;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}

.platform-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--text);
  text-decoration: none;
  transition: color 0.3s ease;
  position: relative;
  overflow: hidden;
  
  &::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 2px;
    background-color: var(--accent);
    transition: width 0.3s ease;
  }
  
  &:hover::after {
    width: 100%;
  }
  
  &:hover {
    color: var(--accent);
  }
  
  i {
    transition: transform 0.3s ease;
  }
}

.contact-section {
  margin-top: 4rem;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 1rem;
  padding: 2rem;
  text-align: center;
  border: 1px solid rgba(255, 255, 255, 0.1);
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards 0.6s;
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
  }
}

.section-title {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: var(--accent);
}

.contact-text {
  color: var(--text);
  margin-bottom: 1.5rem;
  line-height: 1.6;
  opacity: 0.9;
}

.contact-button {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  background: var(--accent);
  color: var(--background);
  padding: 1rem 2rem;
  border-radius: 2rem;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      120deg, 
      transparent, 
      rgba(255,255,255,0.2), 
      transparent
    );
    transition: all 0.5s ease;
  }
  
  &:hover::before {
    left: 100%;
  }
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 0 20px var(--accent);
    
    i {
      transform: translateX(5px);
    }
  }
  
  &:active {
    transform: scale(0.95);
  }
  
  i {
    transition: transform 0.3s ease;
  }
}

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

@media (max-width: 768px) {
  .social-grid {
    grid-template-columns: 1fr;
  }
}

@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
</style>