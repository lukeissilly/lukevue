<template>
   <link rel="icon" type="image/x-icon" href="pfp.ico">
   <title> luke.tf </title>
  <div class="home">
    <div class="hero">
      <div class="hero-content">
        <div class="profile-container">
          <div class="profile-wrapper">
            <img class="profile-image" src="@/assets/images/pfp.webp" alt="Profile">
            <div class="profile-glow"></div>
          </div>
        </div>
        <h1>Luke</h1>
        <div class="subtitle">
          <span class="typing">World's Worst Developer</span>
        </div>
        <Transition name="fade">
          <div v-if="showScrollIndicator" class="scroll-indicator">
            <div class="mouse">
              <div class="wheel"></div>
            </div>
          </div>
        </Transition>
      </div>
    </div>

    <div class="content">
      <div class="section">
        <div class="section-content">
          <h2 class="section-title">Welcome to my website :)</h2>
          <p class="section-text">
            In short, my name is Luke and I like doing weird computer stuff.
          </p>
          <p class="section-text">
            There's not much else to put here to have this cat gif
          </p>
          <div class="cat-container">
            <img class="cat-gif" src="https://i.ibb.co/fCVNrQj/aaaa.gif" alt="Skateboarding Cat">
            <div class="cat-overlay"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const showScrollIndicator = ref(true)

const handleScroll = () => {
  showScrollIndicator.value = window.scrollY <= 50
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style lang="scss" scoped>
.home {
  height: 100%;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards;
}

.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding-top: 4rem;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards 0.2s;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: radial-gradient(circle at center, rgba(0,255,157,0.1) 0%, transparent 70%);
    pointer-events: none;
    animation: gradientShift 8s ease-in-out infinite;
  }
}

.hero-content {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 1;
  padding: 2rem;
  animation: fadeInUp 1s ease-out;
}

.profile-container {
  margin-bottom: 2rem;
  padding-top: 2rem;
  animation: floatIn 1.5s ease-out;
}

.profile-wrapper {
  position: relative;
  width: 200px;
  height: 200px;
  margin: 0 auto;
  border-radius: 50%;
  overflow: hidden;
  transform-style: preserve-3d;
  animation: float 6s ease-in-out infinite;
  background: linear-gradient(135deg, #000000 0%, #000000 50%, #000000 100%);
  box-shadow: 0 0 30px rgba(0, 255, 157, 0.3);
  
  &::before {
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    right: -2px;
    bottom: -2px;
    border-radius: 50%;
    background: linear-gradient(45deg, var(--accent), var(--secondary));
    opacity: 0.6;
    z-index: 1;
    animation: rotateBorder 8s linear infinite;
  }
}

.profile-image {
  position: relative;
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
  z-index: 3;
  transition: transform 0.3s ease;
  background: transparent;
  mix-blend-mode: normal;
  
  &:hover {
    transform: scale(1.05);
  }
}

.profile-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 220px;
  height: 220px;
  border-radius: 50%;
  background: radial-gradient(circle, var(--accent) 0%, var(--secondary) 100%);
  filter: blur(25px);
  opacity: 0.15;
  z-index: 0;
  animation: pulseGlow 4s ease-in-out infinite;
}

h1 {
  font-size: 5rem;
  font-weight: 900;
  color: var(--text);
  text-align: center;
  margin-bottom: 1rem;
  letter-spacing: -0.05em;
}

.subtitle {
  margin-top: 1rem;
  height: 1.5em;
  background-clip: text;
  -webkit-background-clip: text;
  opacity: 0;
  animation: fadeIn 0.5s ease-out 1s forwards;
}

.typing {
  font-size: 1.25rem;
  color: var(--accent);
  border-right: 2px solid var(--accent);
  padding-right: 5px;
  animation: typing 3.5s steps(40, end),
             blink-caret .75s step-end infinite;
  white-space: nowrap;
  overflow: hidden;
  display: inline-block;
  background-clip: text;
  -webkit-background-clip: text;
}

.scroll-indicator {
  position: absolute;
  bottom: 6rem;
  left: 50%;
  transform: translateX(-50%);
  z-index: 10;
}

.mouse {
  width: 26px;
  height: 40px;
  border: 2px solid var(--accent);
  border-radius: 14px;
  position: relative;
}

.wheel {
  position: absolute;
  width: 2px;
  height: 8px;
  background: var(--accent);
  top: 1px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 3s infinite;
  opacity: 0.8;
}

.content {
  min-height: 100vh;
  padding: 4rem 2rem;
}

.section {
  max-width: 1200px;
  margin: 0 auto;
}

.section-content {
  text-align: center;
}

.section-title {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  background: linear-gradient(45deg, var(--text), var(--accent));
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.section-text {
  color: var(--text);
  opacity: 0.8;
  margin-bottom: 3rem;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards 0.3s;
}

.cat-container {
  position: relative;
  max-width: 600px;
  margin: 0 auto;
  border-radius: 1rem;
  overflow: hidden;
  opacity: 0;
  animation: fadeInUp 0.8s ease forwards 0.4s;
  transition: all 0.3s ease;
  
  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(45deg, var(--accent), transparent);
    opacity: 0.5;
    mix-blend-mode: overlay;
  }
  
  &:hover {
    transform: scale(1.02);
  }
}

.cat-gif {
  width: 100%;
  display: block;
  border-radius: 1rem;
}

.glitch {
  display: none;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes pulse {
  0% {
    opacity: 0.2;
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    opacity: 0.3;
    transform: translate(-50%, -50%) scale(1.1);
  }
  100% {
    opacity: 0.2;
    transform: translate(-50%, -50%) scale(1);
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
  0% { clip: rect(24px, 9999px, 66px, 0); }
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

@keyframes typing {
  from { width: 0 }
  to { width: 100% }
}

@keyframes blink-caret {
  from, to { border-color: transparent }
  50% { border-color: var(--accent) }
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { 
    transform: translateX(-50%) translateY(0);
  }
  40% { 
    transform: translateX(-50%) translateY(-20px);
  }
  60% { 
    transform: translateX(-50%) translateY(-10px);
  }
}

@keyframes scroll {
  0% {
    opacity: 0.8;
    transform: translateX(-50%) translateY(2px);
  }
  100% {
    opacity: 0;
    transform: translateX(-50%) translateY(10px);
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

@keyframes floatIn {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes rotateBorder {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

@keyframes pulseGlow {
  0% {
    opacity: 0.15;
    transform: translate(-50%, -50%) scale(1);
    filter: blur(25px);
  }
  50% {
    opacity: 0.2;
    transform: translate(-50%, -50%) scale(1.1);
    filter: blur(30px);
  }
  100% {
    opacity: 0.15;
    transform: translate(-50%, -50%) scale(1);
    filter: blur(25px);
  }
}

@keyframes gradientShift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes glitchText {
  0% {
    text-shadow: 0.05em 0 0 var(--accent), -0.05em -0.025em 0 #ff0000;
    transform: translate(0);
  }
  14% {
    text-shadow: 0.05em 0 0 var(--accent), -0.05em -0.025em 0 #ff0000;
    transform: translate(0);
  }
  15% {
    text-shadow: -0.05em -0.025em 0 var(--accent), 0.025em 0.025em 0 #ff0000;
    transform: translate(-0.025em, 0.025em);
  }
  49% {
    text-shadow: -0.05em -0.025em 0 var(--accent), 0.025em 0.025em 0 #ff0000;
    transform: translate(-0.025em, 0.025em);
  }
  50% {
    text-shadow: 0.025em 0.05em 0 var(--accent), 0.05em 0 0 #ff0000;
    transform: translate(0.025em, 0);
  }
  99% {
    text-shadow: 0.025em 0.05em 0 var(--accent), 0.05em 0 0 #ff0000;
    transform: translate(0.025em, 0);
  }
  100% {
    text-shadow: 0.05em 0 0 var(--accent), -0.05em -0.025em 0 #ff0000;
    transform: translate(0);
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

@media (max-width: 768px) {
  h1 {
    font-size: 3rem;
  }
  
  .typing {
    font-size: 1rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>
