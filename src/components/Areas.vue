<template>
  <section class="tech-areas">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Áreas Abordadas</h2>
        <p class="section-subtitle">Nossos principais campos de atuação tecnológica</p>
      </div>

      <div class="areas-grid">
        <div 
          v-for="area in areas" 
          :key="area.id" 
          class="area-card"
          @mouseenter="hoveredCard = area.id"
          @mouseleave="hoveredCard = null"
        >
          <div class="card-icon" v-html="area.icon"></div>
          <h3 class="card-title">{{ area.title }}</h3>
          <p class="card-description">{{ area.description }}</p>
          <div class="card-hover-indicator" :class="{'active': hoveredCard === area.id}"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'TechAreas',
  data() {
    return {
      hoveredCard: null,
      areas: [
        {
          id: 1,
          title: 'Programação',
          icon: this.getIcon('programming'),
          description: 'Ensino de programação e desenvolvimento de software.'
        },
        {
          id: 2,
          title: 'Redes',
          icon: this.getIcon('network'),
          description: 'Conceitos de redes de computadores e infraestrutura.'
        },
        {
          id: 3,
          title: 'Hardware',
          icon: this.getIcon('hardware'),
          description: 'Introdução ao mundo do hardware e componentes eletrônicos.'
        },
        {
          id: 4,
          title: 'TI&C',
          icon: this.getIcon('itc'),
          description: 'Técnicas em TI&C, com foco em inovação e soluções tecnológicas.'
        }
      ]
    }
  },
  methods: {
    getIcon(type) {
      const icons = {
        programming: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path fill="currentColor" d="M3,3H21V21H3V3M5,5V19H19V5H5M13.39,17.24L16.45,12L13.39,6.76L11.39,7.76L13.79,12L11.39,16.24L13.39,17.24M10.61,17.24L7.55,12L10.61,6.76L12.61,7.76L10.21,12L12.61,16.24L10.61,17.24Z"/></svg>',
        network: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path fill="currentColor" d="M21,13C21,15.76 18.76,18 16,18H8C5.24,18 3,15.76 3,13C3,10.24 5.24,8 8,8H16C18.76,8 21,10.24 21,13M5,13C5,14.66 6.34,16 8,16H16C17.66,16 19,14.66 19,13C19,11.34 17.66,10 16,10H8C6.34,10 5,11.34 5,13M19,19H5V21H19V19Z"/></svg>',
        hardware: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path fill="currentColor" d="M5,3H19A2,2 0 0,1 21,5V19A2,2 0 0,1 19,21H5A2,2 0 0,1 3,19V5A2,2 0 0,1 5,3M6,6V18H18V6H6Z"/></svg>',
        itc: '<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path fill="currentColor" d="M12,2A10,10 0 0,1 22,12A10,10 0 0,1 12,22A10,10 0 0,1 2,12A10,10 0 0,1 12,2M12,4A8,8 0 0,0 4,12A8,8 0 0,0 12,20A8,8 0 0,0 20,12A8,8 0 0,0 12,4Z"/></svg>'
      }
      return icons[type] || ''
    }
  }
}
</script>

<style scoped>
.tech-areas {
  padding: 80px 0;
  background-color: #f8fafc;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.section-header {
  text-align: center;
  margin-bottom: 50px;
}

.section-title {
  font-size: 2.25rem;
  color: #1e293b;
  margin-bottom: 15px;
  font-weight: 600;
}

.section-subtitle {
  font-size: 1.1rem;
  color: #64748b;
  max-width: 600px;
  margin: 0 auto;
}

.areas-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
}

.area-card {
  background: white;
  border-radius: 12px;
  padding: 40px 30px;
  text-align: center;
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
  transition: all 0.3s ease;
  border: 1px solid #e2e8f0;
}

.area-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.card-icon {
  width: 70px;
  height: 70px;
  margin: 0 auto 25px;
  color: #3b82f6;
}

.card-icon svg {
  width: 100%;
  height: 100%;
  display: block;
}

.card-title {
  font-size: 1.25rem;
  color: #1e293b;
  margin-bottom: 15px;
  font-weight: 500;
}

.card-description {
  font-size: 1rem;
  color: #64748b;
  line-height: 1.6;
}

.card-hover-indicator {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: #3b82f6;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.card-hover-indicator.active {
  transform: scaleX(1);
}

@media (max-width: 768px) {
  .tech-areas {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 1.75rem;
  }
  
  .areas-grid {
    grid-template-columns: 1fr;
    max-width: 400px;
    margin: 0 auto;
  }
}
</style>