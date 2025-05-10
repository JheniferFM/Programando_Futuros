<template>
  <div id="app">
    <!-- Loading cósmico (sobrepõe tudo) -->
    <CosmicLoading v-if="isLoading" />
    
    <!-- Conteúdo principal (oculto durante o loading) -->
    <div v-show="!isLoading" class="main-content">
      <Menu />
      <Hero />
      <About />
      <Areas />
      <DashboardPreview />
      <Footer />
    </div>
  </div>
</template>

<script>
import Menu from './components/Menu.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Areas from './components/Areas.vue'
import DashboardPreview from './components/DashboardPreview.vue'
import Footer from './components/Footer.vue'
import CosmicLoading from './components/CosmicLoading.vue';



export default {
  name: 'App',
  components: {
    Menu,
    Hero,
    About,
    Areas,
    DashboardPreview,
    Footer,
    CosmicLoading
  },
  data() {
    return {
      isLoading: true
    }
  },
  mounted() {
    // Simula carregamento ou espera por recursos críticos
    this.simulateLoading()
  },
  methods: {
    simulateLoading() {
      // Tempo mínimo de exibição do loading (3 segundos)
      setTimeout(() => {
        this.isLoading = false
        document.body.style.overflow = 'auto' // Libera o scroll
      }, 3000)
    }
  },
  created() {
    // Bloqueia scroll durante o loading
    document.body.style.overflow = 'hidden'
  }
}
</script>

<style>
/* Estilos gerais da página */
#app {
  position: relative;
  min-height: 100vh;
}

.main-content {
  opacity: 0;
  animation: fadeIn 0.5s forwards;
  animation-delay: 0.3s; /* Espera o loading sair */
}

@keyframes fadeIn {
  to { opacity: 1; }
}

/* Garante que o loading fique por cima de tudo */
.cosmic-loading-container {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 9999;
}

/* Remove margens padrão do body */
body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
</style>