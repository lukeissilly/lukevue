<template>
  <nav class="nav">
    <div class="nav-content">
      <RouterLink to="/" class="nav-link">HOME</RouterLink>
      <RouterLink to="/about" class="nav-link">ABOUT</RouterLink>
      <RouterLink to="/socials" class="nav-link">SOCIALS</RouterLink>
    </div>
  </nav>
  <RouterView />
</template>

<script setup lang="ts">
</script>

<style lang="scss">
@import 'primevue/resources/themes/lara-light-blue/theme.css';
@import 'primevue/resources/primevue.min.css';
@import 'primeicons/primeicons.css';

:root {
  --background: #000000;
  --text: #ffffff;
  --accent: #10924f;  /* Bright neon green */
  --secondary: #e6e3a2;  /* Electric green */
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: var(--background);
  color: var(--text);
  font-family: 'Inter', sans-serif;
  min-height: 100vh;
  overflow-x: hidden;
}

#app {
  min-height: 100vh;
}

.nav {
  position: fixed;
  top: 1rem;
  left: 50%;
  transform: translateX(-50%);
  padding: 0.75rem 1.5rem;
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(8px);
  border-radius: 2rem;
  z-index: 1000;
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.nav-content {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
}

.nav-link {
  color: var(--text);
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s ease;
  opacity: 0.7;
  letter-spacing: 1px;
  font-size: 0.9rem;
  padding: 0.25rem 0.5rem;
  
  &:hover {
    color: var(--accent);
    opacity: 1;
  }
  
  &.router-link-active {
    color: var(--accent);
    opacity: 1;
  }
}
</style>
