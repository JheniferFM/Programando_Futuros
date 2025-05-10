<template>
  <div>
    <!-- Hero Section -->
    <section class="hero">
      <h2>Bem-vindo ao Programando Futuros</h2>
      <p>Conectando voluntários a escolas públicas com foco em educação tecnológica.</p>
      <!-- Botão de Login / Cadastro -->
      <button @click="goToLogin" class="login-btn">Login / Cadastro</button>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  methods: {
    // Função para redirecionar para a página de login
    goToLogin() {
      this.$router.push({ name: 'Login' });
    }
  }
};
</script>

<style scoped>
.login-btn {
  background-color: #4A90E2;
  color: white;
  padding: 10px 20px;
  font-size: 1.2rem;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 20px;
  transition: background-color 0.3s;
}

.login-btn:hover {
  background-color: #1F3A73;
}
</style>
