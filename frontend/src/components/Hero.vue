<template>
  <section class="hero cosmic-bg" ref="heroSection">
    <div class="stars"></div>
    <div class="twinkling"></div>
    <div class="hero-content">
      <h2 class="hero-title cosmic-text">
        <span class="title-word">Bem-vindo</span>
        <span class="title-word">ao</span>
        <span class="title-word">Programando</span>
        <span class="title-word">Futuros!</span>
      </h2>
      <p class="hero-subtitle">Conectando voluntários para construir o futuro da educação tecnológica. 
        O Projeto Integrador III visa consolidar os conhecimentos adquiridos pela turma de ADS através do desenvolvimento de uma solução prática e aplicável a um problema real. 
        O projeto Programando Futuros é uma plataforma web voltada para o incentivo à educação tecnológica em escolas públicas, buscando transformar a realidade de estudantes por meio de oficinas de tecnologia.
        O projeto estimula a aplicação de habilidades em programação, análise de sistemas e trabalho em equipe, promovendo a entrega de resultados concretos e socialmente relevantes.
      </p>
      <div class="cta-buttons">
        <router-link to="/login" class="cta-btn primary-cta">Junte-se a Nós</router-link>
        <router-link to="/about" class="cta-btn secondary-cta">Saiba Mais</router-link>
      </div>
    </div>

  </section>
</template>

<script>
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: 'Hero',
  mounted() {
    // Animação de entrada cósmica
    gsap.from(this.$refs.heroSection, {
      opacity: 0,
      duration: 2,
      ease: "power4.out",
    });

    // Animação das palavras do título
    gsap.from(".title-word", {
      opacity: 0,
      y: 50,
      duration: 1,
      stagger: 0.2,
      ease: "back.out(1.7)",
      delay: 0.3
    });

    // Animação do subtítulo
    gsap.from(".hero-subtitle", {
      opacity: 0,
      y: 30,
      delay: 1.5,
      duration: 1.5,
      ease: "power4.out"
    });

    // Animação dos botões CTA
    gsap.from(".cta-btn", {
      opacity: 0,
      y: 40,
      duration: 1,
      stagger: 0.2,
      delay: 2,
      ease: "elastic.out(1, 0.5)"
    });

    // Animação do scroll indicator
    gsap.from(".scroll-indicator", {
      opacity: 0,
      y: 20,
      delay: 3,
      duration: 1,
      ease: "power2.out"
    });

    // Efeito parallax para o fundo
    ScrollTrigger.create({
      trigger: this.$refs.heroSection,
      start: "top top",
      end: "bottom top",
      scrub: true,
      onUpdate: (self) => {
        const speed = 0.5;
        const offset = self.scroll() * speed;
        gsap.to(".stars", { y: -offset * 0.5, ease: "none" });
        gsap.to(".twinkling", { y: -offset * 0.2, ease: "none" });
      }
    });
  }
};
</script>

<style scoped>
.hero {
  height: 100vh;
  min-height: 700px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  position: relative;
  overflow: hidden;
  padding: 0 20px;
}

.cosmic-bg {
  background: linear-gradient(135deg, #0F1C3F 0%, #1F3A73 50%, #0F1C3F 100%);
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

.hero-content {
  position: relative;
  z-index: 2;
  max-width: 900px;
  margin: 0 auto;
}

.hero-title {
  font-size: 4rem;
  font-weight: 800;
  margin-bottom: 1.5rem;
  line-height: 1.2;
  font-family: 'Orbitron', sans-serif;
  text-transform: uppercase;
  background: linear-gradient(45deg, #fff 30%, #4a6de2 70%);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  display: inline-block;
}

.title-word {
  display: inline-block;
  margin: 0 8px;
}

.hero-subtitle {
  font-size: 1.2rem;
  color: rgba(255, 255, 255, 0.9);
  margin-bottom: 3rem;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.6;
}

.cta-buttons {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 40px;
}

.cta-btn {
  padding: 15px 35px;
  border-radius: 50px;
  font-weight: 600;
  font-size: 1.1rem;
  text-decoration: none;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  z-index: 1;
}

.primary-cta {
  background: linear-gradient(45deg, #F39C12, #E74C3C);
  color: white;
  box-shadow: 0 8px 25px rgba(243, 156, 18, 0.4);
}

.primary-cta:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 30px rgba(243, 156, 18, 0.6);
}

.primary-cta::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(45deg, #E74C3C, #F39C12);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: -1;
}

.primary-cta:hover::before {
  opacity: 1;
}

.secondary-cta {
  background: transparent;
  color: white;
  border: 2px solid rgba(255, 255, 255, 0.3);
}

.secondary-cta:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: white;
  transform: translateY(-5px);
}

.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  animation: bounce 2s infinite;
}

.mouse {
  width: 30px;
  height: 50px;
  border: 2px solid rgba(255, 255, 255, 0.7);
  border-radius: 15px;
  margin-bottom: 10px;
  position: relative;
}

.scroller {
  width: 6px;
  height: 10px;
  background: white;
  border-radius: 3px;
  position: absolute;
  top: 10px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 2.5s infinite;
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

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateY(0) translateX(-50%); }
  40% { transform: translateY(-20px) translateX(-50%); }
  60% { transform: translateY(-10px) translateX(-50%); }
}

@keyframes scroll {
  0% { opacity: 0; transform: translateY(0) translateX(-50%); }
  20% { opacity: 1; }
  50% { transform: translateY(15px) translateX(-50%); opacity: 1; }
  100% { transform: translateY(25px) translateX(-50%); opacity: 0; }
}

/* Responsividade */
@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-subtitle {
    font-size: 1.2rem;
  }
  
  .cta-buttons {
    flex-direction: column;
    gap: 15px;
  }
  
  .cta-btn {
    width: 100%;
    max-width: 250px;
    margin: 0 auto;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 2rem;
  }
  
  .hero-subtitle {
    font-size: 1rem;
  }
  
  .title-word {
    display: block;
    margin: 5px 0;
  }
}
</style>