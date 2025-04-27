<template>
  <div class="dashboard-container cosmic-panel">
    <div class="dashboard-header">
      <h2 class="dashboard-title">🚀 Dashboard: Mapeamento Tecnológico Educacional</h2>
      <p class="dashboard-description">
        Monitoramento em tempo real do acesso ao ensino tecnológico nas escolas públicas da Asa Norte – DF.
        <br>Dados que transformam realidades e direcionam ações estratégicas.
      </p>
    </div>
    
    <div class="dashboard-grid">
      <div class="data-card card-glow">
        <div class="data-icon">📈</div>
        <h3>Cobertura Atual</h3>
        <div class="data-value">78%</div>
        <div class="data-progress">
          <div class="progress-bar" style="width: 78%"></div>
        </div>
        <p>Escolas com infraestrutura tecnológica básica</p>
      </div>
      
      <div class="data-card card-glow">
        <div class="data-icon">👨‍🏫</div>
        <h3>Capacitação Docente</h3>
        <div class="data-value">62%</div>
        <div class="data-progress">
          <div class="progress-bar" style="width: 62%"></div>
        </div>
        <p>Professores com formação em tecnologia educacional</p>
      </div>
      
      <div class="data-card card-glow">
        <div class="data-icon">💻</div>
        <h3>Acesso Alunos</h3>
        <div class="data-value">45%</div>
        <div class="data-progress">
          <div class="progress-bar" style="width: 45%"></div>
        </div>
        <p>Alunos com acesso regular a computadores</p>
      </div>
      
      <div class="data-card card-glow">
        <div class="data-icon">🔄</div>
        <h3>Impacto Voluntários</h3>
        <div class="data-value">+230%</div>
        <div class="data-trend up">↑</div>
        <p>Aumento no engajamento após nosso programa</p>
      </div>
    </div>
    
    <div class="dashboard-frame holographic-display">
      <div class="powerbi-overlay">
        <iframe
          src="https://app.powerbi.com/reportEmbed?reportId=YOUR_REPORT_ID&groupId=YOUR_GROUP_ID&autoAuth=true&ctid=YOUR_TENANT_ID"
          frameborder="0"
          allowFullScreen="true"
        ></iframe>
      </div>
      <div class="holographic-lines"></div>
    </div>
    
    <div class="dashboard-footer">
      <p>Dados atualizados em tempo real | Última atualização: {{ currentDate }}</p>
      <button class="download-btn">
        <span class="btn-icon">⬇️</span> Baixar Relatório Completo
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "DashboardPreview",
  data() {
    return {
      currentDate: new Date().toLocaleDateString('pt-BR', {
        day: '2-digit',
        month: 'long',
        year: 'numeric'
      })
    };
  },
  mounted() {
    // Anima os cards quando entram na viewport
    const cards = document.querySelectorAll('.data-card');
    cards.forEach((card, index) => {
      card.style.opacity = '0';
      card.style.transform = 'translateY(30px)';
      
      setTimeout(() => {
        card.style.transition = 'all 0.6s ease-out';
        card.style.opacity = '1';
        card.style.transform = 'translateY(0)';
      }, 200 * index);
    });
  }
};
</script>

<style scoped>
.dashboard-container {
  width: 100%;
  max-width: 1400px;
  margin: 0 auto;
  padding: 40px 20px;
  position: relative;
}

.cosmic-panel {
  background: rgba(15, 28, 63, 0.8);
  border-radius: 20px;
  backdrop-filter: blur(10px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  border: 1px solid rgba(74, 144, 226, 0.2);
  margin: 40px auto;
  overflow: hidden;
}

.dashboard-header {
  text-align: center;
  margin-bottom: 40px;
  padding: 0 20px;
}

.dashboard-title {
  font-size: 2.2rem;
  color: white;
  margin-bottom: 15px;
  font-weight: 700;
  position: relative;
  display: inline-block;
}

.dashboard-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 3px;
  background: linear-gradient(90deg, #F39C12, #4A90E2);
  border-radius: 3px;
}

.dashboard-description {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.8);
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.6;
}

.dashboard-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 25px;
  margin-bottom: 50px;
  padding: 0 20px;
}

.data-card {
  background: rgba(31, 58, 115, 0.6);
  border-radius: 15px;
  padding: 25px;
  text-align: center;
  transition: all 0.3s ease;
  border: 1px solid rgba(74, 144, 226, 0.3);
}

.card-glow:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px rgba(74, 144, 226, 0.3);
  border-color: rgba(243, 156, 18, 0.5);
}

.data-icon {
  font-size: 2.5rem;
  margin-bottom: 15px;
}

.data-card h3 {
  color: white;
  margin-bottom: 15px;
  font-size: 1.3rem;
}

.data-value {
  font-size: 2.5rem;
  font-weight: 700;
  color: #F39C12;
  margin-bottom: 10px;
}

.data-progress {
  height: 8px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 4px;
  margin-bottom: 15px;
  overflow: hidden;
}

.progress-bar {
  height: 100%;
  background: linear-gradient(90deg, #4A90E2, #8E44AD);
  border-radius: 4px;
  transition: width 1s ease;
}

.data-trend {
  font-size: 1.8rem;
  margin-bottom: 10px;
}

.data-trend.up {
  color: #2ECC71;
}

.data-card p {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  margin-top: 10px;
}

.dashboard-frame {
  position: relative;
  height: 600px;
  border-radius: 15px;
  overflow: hidden;
  margin: 40px 0;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
}

.holographic-display {
  border: 1px solid rgba(74, 144, 226, 0.5);
  background: rgba(0, 0, 0, 0.7);
}

.powerbi-overlay {
  width: 100%;
  height: 100%;
  position: relative;
  z-index: 2;
}

.powerbi-overlay iframe {
  width: 100%;
  height: 100%;
}

.holographic-lines {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    linear-gradient(90deg, rgba(74, 144, 226, 0.1) 1px, transparent 1px),
    linear-gradient(rgba(74, 144, 226, 0.1) 1px, transparent 1px);
  background-size: 20px 20px;
  z-index: 1;
  pointer-events: none;
  animation: scan 8s linear infinite;
}

.dashboard-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  margin-top: 30px;
  flex-wrap: wrap;
}

.dashboard-footer p {
  color: rgba(255, 255, 255, 0.6);
  font-size: 0.9rem;
}

.download-btn {
  background: linear-gradient(45deg, #4A90E2, #8E44AD);
  color: white;
  border: none;
  padding: 12px 25px;
  border-radius: 30px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  box-shadow: 0 5px 15px rgba(74, 144, 226, 0.4);
}

.download-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 20px rgba(74, 144, 226, 0.6);
}

.btn-icon {
  margin-right: 8px;
}

/* Animações */
@keyframes scan {
  0% { background-position: 0 0; }
  100% { background-position: 20px 20px; }
}

/* Responsividade */
@media (max-width: 768px) {
  .dashboard-title {
    font-size: 1.8rem;
  }
  
  .dashboard-description {
    font-size: 1rem;
  }
  
  .dashboard-footer {
    flex-direction: column;
    gap: 15px;
    text-align: center;
  }
}

@media (max-width: 480px) {
  .dashboard-title {
    font-size: 1.5rem;
  }
  
  .data-card {
    padding: 20px 15px;
  }
  
  .data-value {
    font-size: 2rem;
  }
}
</style>