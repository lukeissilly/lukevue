<template>
  <div class="social">
    <div class="hero">
      <h1>Socials</h1>
      <p class="subtitle">Just incase you want to stalk me :p</p>
    </div>

    <div class="social-grid">
      <div v-for="(platform, index) in platforms" 
           :key="platform.name"
           class="social-card"
           :style="{ '--delay': `${index * 0.1}s`, '--color': platform.color }">
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
    
    &:nth-child(1) { animation-delay: 0.3s; }
    &:nth-child(2) { animation-delay: 0.4s; }
    &:nth-child(3) { animation-delay: 0.5s; }

    &:hover {
      transform: translateY(-10px);
      box-shadow: 0 10px 20px rgba(0,0,0,0.1);
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
  
  &:hover {
    transform: translateY(-2px);
    box-shadow: 0 0 20px var(--accent);
    
    i {
      transform: translateX(5px);
    }
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

@media (max-width: 768px) {
  .social-grid {
    grid-template-columns: 1fr;
  }
}
</style>