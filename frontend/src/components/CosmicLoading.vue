<template>
  <section class="areas-section cosmic-bg">
    <div class="stars"></div>
    <div class="twinkling"></div>
    
    <h2 class="section-title cosmic-text">
      <span class="title-decorator">◆</span> ÁREAS ABORDADAS <span class="title-decorator">◆</span>
    </h2>
    
    <div class="areas-grid">
      <div 
        v-for="area in areas" 
        :key="area.id" 
        class="area-card"
        @mouseenter="activateCard(area.id)"
        @mouseleave="deactivateCard(area.id)"
      >
        <div class="card-inner" :class="{active: activeCard === area.id}">
          <div class="card-front">
            <div class="tech-icon" v-html="area.icon"></div>
            <h3 class="tech-title">{{ area.title }}</h3>
          </div>
          <div class="card-back">
            <p class="tech-description">{{ area.description }}</p>
            <div class="tech-particles"></div>
          </div>
          <div class="card-glow"></div>
        </div>
      </div>
    </div>
    
    <div class="cyber-line"></div>
  </section>
</template>

<script>
export default {
  name: 'TechAreas',
  data() {
    return {
      activeCard: null,
      areas: [
        {
          id: 1,
          title: 'PROGRAMAÇÃO',
          icon: '&lt;svg viewBox="0 0 24 24"&gt;&lt;path d="M3,3H21V21H3V3M5,5V19H19V5H5M13.39,17.24L16.45,12L13.39,6.76L11.39,7.76L13.79,12L11.39,16.24L13.39,17.24M10.61,17.24L7.55,12L10.61,6.76L12.61,7.76L10.21,12L12.61,16.24L10.61,17.24Z"/&gt;&lt;/svg&gt;',
          description: 'Domine linguagens como Python, JavaScript e C++ com nossos cursos imersivos em realidade aumentada.'
        },
        {
          id: 2,
          title: 'REDES QUÂNTICAS',
          icon: '&lt;svg viewBox="0 0 24 24"&gt;&lt;path d="M21,13C21,15.76 18.76,18 16,18H8C5.24,18 3,15.76 3,13C3,10.24 5.24,8 8,8H16C18.76,8 21,10.24 21,13M5,13C5,14.66 6.34,16 8,16H16C17.66,16 19,14.66 19,13C19,11.34 17.66,10 16,10H8C6.34,10 5,11.34 5,13M19,19H5V21H19V19Z"/&gt;&lt;/svg&gt;',
          description: 'Explore o futuro das comunicações com redes quânticas e protocolos de segurança avançados.'
        },
        {
          id: 3,
          title: 'HARDWARE AI',
          icon: '&lt;svg viewBox="0 0 24 24"&gt;&lt;path d="M5,3H19A2,2 0 0,1 21,5V19A2,2 0 0,1 19,21H5A2,2 0 0,1 3,19V5A2,2 0 0,1 5,3M6,6V18H18V6H6Z"/&gt;&lt;/svg&gt;',
          description: 'Desenvolva sistemas embarcados com IA e robótica cognitiva para soluções autônomas.'
        },
        {
          id: 4,
          title: 'TI&C ESPACIAL',
          icon: '&lt;svg viewBox="0 0 24 24"&gt;&lt;path d="M12,2A10,10 0 0,1 22,12A10,10 0 0,1 12,22A10,10 0 0,1 2,12A10,10 0 0,1 12,2M12,4A8,8 0 0,0 4,12A8,8 0 0,0 12,20A8,8 0 0,0 20,12A8,8 0 0,0 12,4Z"/&gt;&lt;/svg&gt;',
          description: 'Tecnologias para colonização interplanetária e sistemas de informação galácticos.'
        }
      ]
    }
  },
  methods: {
    activateCard(id) {
      this.activeCard = id
    },
    deactivateCard() {
      this.activeCard = null
    }
  }
}
</script>

<style scoped>
/* Cores futuristas */
:root {
  --cosmic-blue: #1F3A73;
  --neon-cyan: #00F7FF;
  --neon-purple: #8A2BE2;
  --tech-yellow: #F9D423;
  --dark-space: #0A0E17;
}

/* Fundo cósmico */
.areas-section {
  position: relative;
  padding: 80px 20px;
  overflow: hidden;
  background: linear-gradient(135deg, var(--dark-space) 0%, var(--cosmic-blue) 100%);
}

.cosmic-bg {
  background: linear-gradient(135deg, #0F1C3F 0%, #1F3A73 100%);
}

.stars, .twinkling {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
}

.stars {
  background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><circle cx="20" cy="20" r="0.5" fill="white"/><circle cx="50" cy="30" r="0.7" fill="white"/><circle cx="80" cy="10" r="0.3" fill="white"/><circle cx="10" cy="70" r="0.4" fill="white"/><circle cx="40" cy="80" r="0.6" fill="white"/><circle cx="90" cy="60" r="0.5" fill="white"/><circle cx="70" cy="90" r="0.8" fill="white"/></svg>') repeat;
  background-size: 100px 100px;
  opacity: 0.8;
  animation: moveStars 200s linear infinite;
}

.twinkling {
  background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20"><circle cx="10" cy="10" r="0.5" fill="white"/></svg>') repeat;
  background-size: 20px 20px;
  opacity: 0.2;
  animation: moveTwinkling 100s linear infinite;
}

/* Título estilizado */
.section-title {
  font-size: 2.5rem;
  text-transform: uppercase;
  letter-spacing: 4px;
  margin-bottom: 60px;
  position: relative;
  z-index: 2;
}

.cosmic-text {
  background: linear-gradient(45deg, var(--neon-cyan), var(--neon-purple));
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 0 0 10px rgba(0, 247, 255, 0.3);
}

.title-decorator {
  color: var(--neon-purple);
  margin: 0 15px;
}

/* Grid de cards tecnológicos */
.areas-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}

.area-card {
  perspective: 1000px;
  height: 300px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
  border-radius: 15px;
  overflow: hidden;
}

.area-card:hover .card-inner {
  transform: rotateY(180deg);
}

.card-inner.active {
  transform: rotateY(180deg);
}

.card-front, .card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 30px;
  box-sizing: border-box;
}

.card-front {
  background: rgba(15, 28, 63, 0.7);
  border: 1px solid rgba(74, 144, 226, 0.3);
  backdrop-filter: blur(5px);
}

.card-back {
  background: linear-gradient(45deg, rgba(31, 58, 115, 0.9), rgba(15, 28, 63, 0.95));
  transform: rotateY(180deg);
  border: 1px solid var(--neon-cyan);
  box-shadow: 0 0 20px rgba(0, 247, 255, 0.3);
}

.tech-icon {
  width: 80px;
  height: 80px;
  margin-bottom: 20px;
  fill: var(--neon-cyan);
  filter: drop-shadow(0 0 5px var(--neon-cyan));
}

.tech-icon svg {
  width: 100%;
  height: 100%;
  fill: currentColor;
}

.tech-title {
  font-size: 1.5rem;
  color: white;
  text-transform: uppercase;
  letter-spacing: 2px;
  margin-bottom: 15px;
  text-shadow: 0 0 10px rgba(0, 247, 255, 0.5);
}

.tech-description {
  color: rgba(255, 255, 255, 0.9);
  text-align: center;
  line-height: 1.6;
  font-size: 1rem;
}

/* Efeitos especiais */
.card-glow {
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, var(--neon-cyan), var(--neon-purple), var(--tech-yellow));
  z-index: -1;
  filter: blur(10px);
  opacity: 0;
  transition: opacity 0.3s;
}

.area-card:hover .card-glow {
  opacity: 0.6;
}

.tech-particles {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: 
    radial-gradient(1px 1px at 20% 30%, var(--neon-cyan), rgba(0,0,0,0)),
    radial-gradient(1px 1px at 80% 70%, var(--neon-purple), rgba(0,0,0,0));
  opacity: 0.3;
  animation: twinkle 3s infinite alternate;
}

.cyber-line {
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--neon-cyan), transparent);
  margin: 80px auto 0;
  max-width: 800px;
  position: relative;
}

.cyber-line::before {
  content: '';
  position: absolute;
  top: -5px;
  left: 0;
  width: 10px;
  height: 10px;
  background: var(--neon-cyan);
  border-radius: 50%;
  animation: pulse 2s infinite;
}

.cyber-line::after {
  content: '';
  position: absolute;
  top: -5px;
  right: 0;
  width: 10px;
  height: 10px;
  background: var(--neon-cyan);
  border-radius: 50%;
  animation: pulse 2s infinite 0.5s;
}

/* Animações */
@keyframes moveStars {
  from { background-position: 0 0; }
  to { background-position: -1000px 1000px; }
}

@keyframes moveTwinkling {
  from { background-position: 0 0; }
  to { background-position: -100px 100px; }
}

@keyframes twinkle {
  from { opacity: 0.1; }
  to { opacity: 0.5; }
}

@keyframes pulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.3); opacity: 0.7; }
}

/* Responsividade */
@media (max-width: 768px) {
  .section-title {
    font-size: 1.8rem;
  }
  
  .areas-grid {
    grid-template-columns: 1fr;
    max-width: 400px;
  }
  
  .area-card {
    height: 250px;
  }
}
</style>