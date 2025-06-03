<template>
  <div>
    <nav class="navbar cosmic-gradient">
      <div class="logo">
        <router-link to="/" class="neon-logo">
          <span class="logo-icon">🚀</span> Programando Futuros
        </router-link>
      </div>
      
      <ul class="nav-links">
        <li><router-link to="/contato" class="nav-item hover-glow">Entre em Contato</router-link></li>
        
        <!-- Áreas de Acesso -->
        <li class="nav-dropdown">        
          <ul class="dropdown-menu">
            <li><router-link to="/aluno" class="dropdown-item">Área do Aluno</router-link></li>
            <li><router-link to="/voluntario" class="dropdown-item">Área do Voluntário</router-link></li>
            <li><router-link to="/escola" class="dropdown-item">Área da Escola</router-link></li>
            <li><router-link to="/admin" class="dropdown-item admin-item">Administração</router-link></li>
          </ul>
        </li>
        
        <li>
          <router-link to="/login" class="nav-item login-btn pulse-animation">
            <span class="icon">👨‍💻</span> Acessar Sistema
          </router-link>
        </li>
      </ul>
      
      <div class="hamburger cosmic-burger" @click="toggleMenu">
        <div class="bar cosmic-bar"></div>
        <div class="bar cosmic-bar"></div>
        <div class="bar cosmic-bar"></div>
      </div>
    </nav>

    <!-- Menu Mobile -->
    <div v-if="menuOpen" class="mobile-menu holographic-effect">
      <div class="close-btn" @click="closeMenu">✕</div>
      <ul class="mobile-links">
        <li><router-link to="/contato" @click="closeMenu" class="nav-item mobile-glow">Entre em Contato</router-link></li>
        
        <!-- Dropdown Mobile -->
        <li class="mobile-dropdown" @click="toggleMobileDropdown">
          <a class="nav-item mobile-glow">
            Áreas de Acesso <span class="dropdown-arrow">▼</span>
          </a>
          <ul class="mobile-dropdown-menu" :class="{ 'active': mobileDropdownOpen }">
            <li><router-link to="/aluno" @click="closeMenu" class="dropdown-item">Área do Aluno</router-link></li>
            <li><router-link to="/voluntario" @click="closeMenu" class="dropdown-item">Área do Voluntário</router-link></li>
            <li><router-link to="/escola" @click="closeMenu" class="dropdown-item">Área da Escola</router-link></li>
            <li><router-link to="/admin" @click="closeMenu" class="dropdown-item admin-item">Administração</router-link></li>
          </ul>
        </li>
        
        <li><router-link to="/login" @click="closeMenu" class="nav-item mobile-glow">Acessar Sistema</router-link></li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
    return {
      menuOpen: false,
      mobileDropdownOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
      if (this.menuOpen) {
        document.body.style.overflow = 'hidden';
      } else {
        document.body.style.overflow = '';
      }
    },
    closeMenu() {
      this.menuOpen = false;
      this.mobileDropdownOpen = false;
      document.body.style.overflow = '';
    },
    toggleMobileDropdown() {
      this.mobileDropdownOpen = !this.mobileDropdownOpen;
    }
  }
};
</script>

<style scoped>
/* (Mantido o mesmo estilo CSS do exemplo anterior) */
/* Cores e variáveis */
:root {
  --cosmic-blue: #1F3A73;
  --stellar-orange: #F39C12;
  --nebula-purple: #8E44AD;
  --galaxy-dark: #0F1C3F;
  --admin-red: #E74C3C;
  --text-light: #FFFFFF;
}

/* Estrutura principal */
.navbar {
  background: linear-gradient(135deg, var(--cosmic-blue), var(--galaxy-dark));
  padding: 15px 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  width: 100%;
  top: 0;
  z-index: 1000;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(10px);
}

.neon-logo {
  font-size: 1.8em;
  font-weight: bold;
  color: white;
  text-decoration: none;
  font-family: 'Orbitron', sans-serif;
  letter-spacing: 1px;
  position: relative;
  transition: all 0.3s ease;
}

.neon-logo:hover {
  text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px var(--stellar-orange);
}

.logo-icon {
  margin-right: 10px;
  animation: float 3s ease-in-out infinite;
}

.nav-links {
  display: flex;
  list-style: none;
  align-items: center;
}

.nav-item {
  margin: 0 20px;
  color: #fff;
  font-size: 1.1em;
  text-decoration: none;
  position: relative;
  transition: all 0.3s ease;
  padding: 8px 0;
  font-weight: 500;
}

.hover-glow:hover {
  color: var(--stellar-orange);
  text-shadow: 0 0 8px rgba(243, 156, 18, 0.7);
}

.nav-item::after {
  content: '';
  position: absolute;
  width: 0;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: var(--stellar-orange);
  transition: width 0.3s ease;
}

.nav-item:hover::after {
  width: 100%;
}

.login-btn {
  background: linear-gradient(45deg, var(--nebula-purple), #4A90E2);
  color: white;
  padding: 12px 25px;
  border-radius: 30px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.4s ease;
  border: none;
  display: flex;
  align-items: center;
  box-shadow: 0 4px 15px rgba(74, 144, 226, 0.4);
}

.login-btn:hover {
  background: linear-gradient(45deg, var(--stellar-orange), #E74C3C);
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(243, 156, 18, 0.6);
}

.pulse-animation {
  animation: pulse 2s infinite;
}

.icon {
  margin-right: 8px;
  font-size: 1.2em;
}

/* Dropdown Desktop */
.nav-dropdown {
  position: relative;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  background: rgba(31, 58, 115, 0.95);
  border-radius: 0 0 10px 10px;
  width: 220px;
  opacity: 0;
  visibility: hidden;
  transform: translateY(10px);
  transition: all 0.3s ease;
  z-index: 1001;
  border: 1px solid rgba(74, 144, 226, 0.3);
  border-top: none;
}

.nav-dropdown:hover .dropdown-menu {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}

.dropdown-item {
  display: block;
  padding: 12px 20px;
  color: #fff;
  text-decoration: none;
  transition: all 0.3s ease;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.dropdown-item:hover {
  background: rgba(243, 156, 18, 0.1);
  color: #FFFFFF;
  padding-left: 25px;
}

.admin-item {
  color: #FF6B6B;
  position: relative;
}

.admin-item::before {
  content: '';
  position: absolute;
  left: 10px;
  top: 50%;
  transform: translateY(-50%);
  width: 6px;
  height: 6px;
  background: var(--admin-red);
  border-radius: 50%;
}

.dropdown-arrow {
  font-size: 0.7em;
  margin-left: 5px;
  transition: transform 0.3s ease;
}

.nav-dropdown:hover .dropdown-arrow {
  transform: rotate(180deg);
}

/* Menu Mobile */
.mobile-menu {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(15, 28, 63, 0.95);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  z-index: 999;
  animation: fadeIn 0.5s ease;
}

.holographic-effect {
  background: linear-gradient(135deg, rgba(31, 58, 115, 0.9), rgba(15, 28, 63, 0.95));
  backdrop-filter: blur(10px);
}

.close-btn {
  position: absolute;
  top: 30px;
  right: 30px;
  color: white;
  font-size: 2em;
  cursor: pointer;
  transition: all 0.3s ease;
}

.close-btn:hover {
  color: var(--stellar-orange);
  transform: rotate(90deg) scale(1.2);
}

.mobile-links {
  list-style: none;
  padding: 0;
  text-align: center;
}

.mobile-links li {
  margin: 25px 0;
}

.mobile-glow {
  color: white;
  font-size: 1.5em;
  text-decoration: none;
  padding: 10px 20px;
  border-radius: 30px;
  transition: all 0.3s ease;
  display: inline-block;
  position: relative;
}

.mobile-glow:hover {
  color: var(--stellar-orange);
  background: rgba(255, 255, 255, 0.1);
  transform: scale(1.1);
  text-shadow: 0 0 10px var(--stellar-orange);
}

/* Dropdown Mobile */
.mobile-dropdown-menu {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.5s ease;
  padding-left: 20px;
}

.mobile-dropdown-menu.active {
  max-height: 500px;
}

.mobile-dropdown .dropdown-item {
  padding: 10px 15px;
  font-size: 0.9em;
}

/* Hamburger Menu */
.hamburger {
  display: none;
  cursor: pointer;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 24px;
  position: relative;
  z-index: 1001;
}

.bar {
  width: 100%;
  height: 3px;
  background-color: #fff;
  border-radius: 5px;
  transition: all 0.4s ease;
}

.hamburger:hover .bar {
  background-color: var(--stellar-orange);
  box-shadow: 0 0 8px var(--stellar-orange);
}

/* Animações */
@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-10px); }
}

@keyframes pulse {
  0% { box-shadow: 0 0 0 0 rgba(74, 144, 226, 0.7); }
  70% { box-shadow: 0 0 0 15px rgba(74, 144, 226, 0); }
  100% { box-shadow: 0 0 0 0 rgba(74, 144, 226, 0); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* Responsividade */
@media (max-width: 992px) {
  .nav-links, .nav-dropdown {
    display: none;
  }
  
  .hamburger {
    display: flex;
  }
}

@media (max-width: 576px) {
  .navbar {
    padding: 15px 20px;
  }
  
  .mobile-dropdown-menu {
    background: rgba(15, 28, 63, 0.5);
    border-radius: 5px;
    margin-top: 5px;
  }
  
  .neon-logo {
    font-size: 1.5em;
  }
  
  .mobile-glow {
    font-size: 1.3em;
  }
}
</style>