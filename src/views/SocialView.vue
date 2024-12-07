<template>
  <div class="social">
    <div class="hero">
      <h1 class="glitch" data-text="Connect">Connect</h1>
      <p class="subtitle">Let's build something amazing together</p>
    </div>

    <div class="social-grid">
      <div v-for="(platform, index) in platforms" 
           :key="platform.name"
           class="social-card"
           :style="{ '--delay': `${index * 0.1}s`, '--color': platform.color }">
        <div class="card-content">
          <div class="platform-icon">
            <i :class="platform.icon"></i>
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
          Whether you want to collaborate on a project, discuss technology, or just say hi,
          I'm always excited to connect with fellow developers and creators!
        </p>
        <a href="mailto:your.email@example.com" class="contact-button">
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
    username: '@lukeisuh',
    description: 'Check out my open source projects and contributions',
    link: 'https://github.com/lukeisuh',
    icon: 'pi pi-github',
    color: '#6e5494'
  },
  {
    name: 'Twitter',
    username: '@lukeisuh',
    description: 'Follow me for tech insights and random thoughts',
    link: 'https://twitter.com/lukeisuh',
    icon: 'pi pi-twitter',
    color: '#1DA1F2'
  },
  {
    name: 'Discord',
    username: 'lukeisuh',
    description: 'Join my community and let\'s chat',
    link: 'https://discord.gg/yourserver',
    icon: 'pi pi-discord',
    color: '#7289DA'
  },
  {
    name: 'LinkedIn',
    username: 'Luke',
    description: 'Connect with me professionally',
    link: 'https://linkedin.com/in/yourprofile',
    icon: 'pi pi-linkedin',
    color: '#0077B5'
  }
]
</script>

<style lang="scss" scoped>
.social {
  min-height: 100vh;
  padding: 2rem;
}

.hero {
  text-align: center;
  margin-bottom: 4rem;
  
  .glitch {
    font-size: 4rem;
    font-weight: 900;
    color: var(--text);
    position: relative;
    text-shadow: 0.05em 0 0 var(--accent), -0.025em -0.05em 0 rgba(255,0,0,0.75),
                 0.025em 0.05em 0 rgba(0,255,255,0.75);
    animation: glitch 500ms infinite;
    margin-bottom: 1rem;
    background-clip: text;
    -webkit-background-clip: text;
    
    &::before,
    &::after {
      content: attr(data-text);
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
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
}

.subtitle {
  color: var(--accent);
  font-size: 1.2rem;
  opacity: 0.8;
}

.social-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.social-card {
  position: relative;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 1rem;
  padding: 2rem;
  overflow: hidden;
  transition: transform 0.3s ease;
  animation: fadeIn 0.5s ease forwards;
  animation-delay: var(--delay);
  opacity: 0;
  
  &:hover {
    transform: translateY(-5px);
    
    .card-glow {
      opacity: 0.2;
    }
    
    .platform-link {
      color: var(--color);
      
      i {
        transform: translateX(5px);
      }
    }
  }
}

.card-content {
  position: relative;
  z-index: 1;
  background-clip: text;
  -webkit-background-clip: text;
}

.platform-icon {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: var(--color);
  
  i {
    background: linear-gradient(45deg, var(--color), transparent);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
}

.card-glow {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: var(--color);
  opacity: 0.1;
  transition: opacity 0.3s ease;
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
  font-weight: 500;
  transition: color 0.3s ease;
  
  i {
    transition: transform 0.3s ease;
  }
}

.contact-section {
  margin-top: 6rem;
  padding: 4rem 0;
  position: relative;
  text-align: center;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100vw;
    height: 100%;
    background: rgba(255, 255, 255, 0.02);
    z-index: -1;
  }
}

.contact-content {
  max-width: 600px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  background: linear-gradient(45deg, var(--text), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.contact-text {
  margin-bottom: 2rem;
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

@keyframes glitch {
  0% { text-shadow: 0.05em 0 0 var(--accent), -0.025em -0.05em 0 rgba(255,0,0,0.75),
                    0.025em 0.05em 0 rgba(0,255,255,0.75); }
  14% { text-shadow: 0.05em 0 0 var(--accent), -0.025em -0.05em 0 rgba(255,0,0,0.75),
                     0.025em 0.05em 0 rgba(0,255,255,0.75); }
  15% { text-shadow: -0.05em -0.025em 0 var(--accent), 0.025em 0.025em 0 rgba(255,0,0,0.75),
                     -0.05em -0.05em 0 rgba(0,255,255,0.75); }
  49% { text-shadow: -0.05em -0.025em 0 var(--accent), 0.025em 0.025em 0 rgba(255,0,0,0.75),
                     -0.05em -0.05em 0 rgba(0,255,255,0.75); }
  50% { text-shadow: 0.025em 0.05em 0 var(--accent), 0.05em 0 0 rgba(255,0,0,0.75),
                     0 -0.05em 0 rgba(0,255,255,0.75); }
  99% { text-shadow: 0.025em 0.05em 0 var(--accent), 0.05em 0 0 rgba(255,0,0,0.75),
                     0 -0.05em 0 rgba(0,255,255,0.75); }
  100% { text-shadow: -0.025em 0 0 var(--accent), -0.025em -0.025em 0 rgba(255,0,0,0.75),
                      -0.025em -0.05em 0 rgba(0,255,255,0.75); }
}

@keyframes glitch-anim {
  0% { clip: rect(14px, 9999px, 66px, 0); }
  5% { clip: rect(37px, 9999px, 29px, 0); }
  10% { clip: rect(85px, 9999px, 92px, 0); }
  15% { clip: rect(100px, 9999px, 23px, 0); }
  20% { clip: rect(28px, 9999px, 61px, 0); }
  25% { clip: rect(79px, 9999px, 44px, 0); }
  30% { clip: rect(16px, 9999px, 94px, 0); }
  35% { clip: rect(74px, 9999px, 71px, 0); }
  40% { clip: rect(49px, 9999px, 27px, 0); }
  45% { clip: rect(76px, 9999px, 40px, 0); }
  50% { clip: rect(15px, 9999px, 11px, 0); }
  55% { clip: rect(66px, 9999px, 5px, 0); }
  60% { clip: rect(84px, 9999px, 93px, 0); }
  65% { clip: rect(25px, 9999px, 55px, 0); }
  70% { clip: rect(39px, 9999px, 76px, 0); }
  75% { clip: rect(77px, 9999px, 61px, 0); }
  80% { clip: rect(44px, 9999px, 15px, 0); }
  85% { clip: rect(72px, 9999px, 96px, 0); }
  90% { clip: rect(12px, 9999px, 42px, 0); }
  95% { clip: rect(57px, 9999px, 34px, 0); }
  100% { clip: rect(95px, 9999px, 8px, 0); }
}

@media (max-width: 768px) {
  .hero .glitch {
    font-size: 3rem;
  }
  
  .social-grid {
    grid-template-columns: 1fr;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>