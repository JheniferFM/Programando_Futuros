<script setup>
import { ref, onMounted } from 'vue'

defineProps({
  msg: String,
})

const count = ref(0)
const rocketLaunched = ref(false)

const launchRocket = () => {
  count.value++
  if (count.value % 5 === 0) {
    rocketLaunched.value = true
    setTimeout(() => {
      rocketLaunched.value = false
    }, 2000)
  }
}

onMounted(() => {
  // Efeito de digitação para a mensagem
  const msgElement = document.querySelector('.typing-effect')
  if (msgElement) {
    const text = msgElement.textContent
    msgElement.textContent = ''
    
    let i = 0
    const typing = setInterval(() => {
      if (i < text.length) {
        msgElement.textContent += text.charAt(i)
        i++
      } else {
        clearInterval(typing)
      }
    }, 50)
  }
})
</script>

<template>
  <div class="hello-world cosmic-card">
    <h1 class="typing-effect">{{ msg }}</h1>
    
    <div class="interactive-area">
      <div class="counter-card" @click="launchRocket">
        <div class="counter-value">{{ count }}</div>
        <div class="counter-label">cliques</div>
        <div class="rocket" :class="{ launched: rocketLaunched }">🚀</div>
      </div>
      
      <div class="code-editor">
        <div class="editor-header">
          <div class="editor-dots">
            <span class="dot red"></span>
            <span class="dot yellow"></span>
            <span class="dot green"></span>
          </div>
          <div class="editor-title">HelloWorld.vue</div>
        </div>
        <div class="editor-content">
          <pre><code>&lt;template&gt;
  &lt;div class="hello-world"&gt;
    &lt;h1&gt;{{ msg }}&lt;/h1&gt;
    &lt;button @click="count++"&gt;
      Count is: {{ count }}
    &lt;/button&gt;
  &lt;/div&gt;
&lt;/template&gt;

&lt;script setup&gt;
const props = defineProps({
  msg: String
})

const count = ref(0)
&lt;/script&gt;</code></pre>
        </div>
      </div>
    </div>
    
    <div class="resource-links">
      <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank" class="resource-link">
        <span class="link-icon">⚡</span> create-vue
      </a>
      <a href="https://vuejs.org/guide/scaling-up/tooling.html#ide-support" target="_blank" class="resource-link">
        <span class="link-icon">🔧</span> Vue Tooling Guide
      </a>
      <a href="https://vitejs.dev/" target="_blank" class="resource-link">
        <span class="link-icon">⚙️</span> Vite Docs
      </a>
    </div>
  </div>
</template>

<style scoped>
.hello-world {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
  position: relative;
}

.cosmic-card {
  background: rgba(31, 58, 115, 0.6);
  border-radius: 20px;
  backdrop-filter: blur(10px);
  border: 1px solid rgba(74, 144, 226, 0.3);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  overflow: hidden;
}

h1 {
  font-size: 2.2rem;
  margin-bottom: 2rem;
  color: white;
  font-weight: 700;
  background: linear-gradient(45deg, #fff, #4A90E2);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}

.interactive-area {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 30px;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}

.counter-card {
  flex: 1;
  min-width: 200px;
  background: rgba(15, 28, 63, 0.7);
  border-radius: 15px;
  padding: 2rem;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(74, 144, 226, 0.3);
}

.counter-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(74, 144, 226, 0.3);
}

.counter-value {
  font-size: 3rem;
  font-weight: 700;
  color: #F39C12;
  margin-bottom: 0.5rem;
}

.counter-label {
  font-size: 1rem;
  color: rgba(255, 255, 255, 0.8);
}

.rocket {
  position: absolute;
  bottom: 20px;
  right: 20px;
  font-size: 2rem;
  transition: all 1s ease;
  transform: rotate(-45deg);
}

.rocket.launched {
  transform: translateY(-100px) rotate(-45deg);
  opacity: 0;
}

.code-editor {
  flex: 2;
  min-width: 300px;
  background: #0F1C3F;
  border-radius: 10px;
  overflow: hidden;
  text-align: left;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
}

.editor-header {
  background: rgba(31, 58, 115, 0.8);
  padding: 0.5rem 1rem;
  display: flex;
  align-items: center;
  border-bottom: 1px solid rgba(74, 144, 226, 0.2);
}

.editor-dots {
  display: flex;
  gap: 6px;
  margin-right: 10px;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.red { background: #FF5F56; }
.yellow { background: #FFBD2E; }
.green { background: #27C93F; }

.editor-title {
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
  font-family: monospace;
}

.editor-content {
  padding: 1rem;
  overflow-x: auto;
}

.editor-content pre {
  margin: 0;
  font-family: 'Fira Code', monospace;
  color: #A4B5D6;
  font-size: 0.9rem;
  line-height: 1.5;
}

.resource-links {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.resource-link {
  display: flex;
  align-items: center;
  color: white;
  text-decoration: none;
  padding: 0.8rem 1.5rem;
  border-radius: 30px;
  background: rgba(74, 144, 226, 0.2);
  border: 1px solid rgba(74, 144, 226, 0.4);
  transition: all 0.3s ease;
}

.resource-link:hover {
  background: rgba(74, 144, 226, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(74, 144, 226, 0.3);
}

.link-icon {
  margin-right: 8px;
  font-size: 1.2rem;
}

/* Responsividade */
@media (max-width: 768px) {
  .interactive-area {
    flex-direction: column;
  }
  
  .counter-card, .code-editor {
    width: 100%;
  }
  
  h1 {
    font-size: 1.8rem;
  }
}

@media (max-width: 480px) {
  .hello-world {
    padding: 1.5rem;
  }
  
  h1 {
    font-size: 1.5rem;
  }
  
  .resource-links {
    flex-direction: column;
    gap: 10px;
  }
  
  .resource-link {
    justify-content: center;
  }
}
</style>