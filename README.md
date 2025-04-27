# 📌 Visão Geral
Sistema que facilita o voluntariado em escolas públicas, com foco no ensino de programação e tecnologia para jovens.

## ✨ Funcionalidades Principais
- **Área do Aluno**: Acesso a materiais e projetos educacionais
- **Área do Voluntário**: Cadastro e gestão de atividades voluntárias
- **Área da Escola**: Solicitação e acompanhamento de voluntários
- **Administração**: Gestão completa do sistema

## 🛠️ Tecnologias Utilizadas
### Frontend
- Vue.js 3
- Tailwind CSS
- Axios
- Vue Router

### Backend (se aplicável)
- Node.js
- Express
- MongoDB
📂 Arquitetura de Pastas

programando-futuros/
│
├── index.html               # Arquivo base do projeto usado pelo Vite
│
├── package.json             # Declaração de dependências e scripts
├── package-lock.json        # Lockfile para versões fixas das dependências
│
├── vite.config.js           # Configuração personalizada do Vite
│
├── README.md                # Arquivo de documentação inicial do projeto
│
├── public/                  # Arquivos públicos (acessados diretamente via URL)
│   ├── images/              # Pasta de imagens públicas do projeto
│   ├── index.html           # Pode conter redirecionamento ou fallback (opcional no Vite)
│   └── vite.svg             # Logo padrão do Vite
│
├── node_modules/            # Pacotes instalados (não editar)
│   ├── (várias dependências) # Ex: Vue, Vite, Chart.js, GSAP, etc.
│
└── src/                     # Pasta principal do código-fonte
    │
    ├── App.vue              # Componente principal que gerencia a estrutura geral
    │
    ├── main.js              # Arquivo que inicializa o Vue, carrega o App.vue e o roteamento
    │
    ├── style.css            # Estilos globais da aplicação
    │
    ├── assets/              # Arquivos estáticos usados na aplicação (imagens, fontes, etc)
    │   └── (imagens, ícones, etc)
    │
    ├── components/          # Componentes reutilizáveis (usados dentro das Views)
    │   ├── Menu.vue         # Cabeçalho ou barra de navegação
    │   ├── Hero.vue         # Seção de destaque principal
    │   ├── About.vue        # Seção "Sobre o projeto"
    │   ├── Areas.vue        # Seção de áreas ou temas de atuação
    │   ├── DashboardPreview.vue # Prévia do dashboard ou dados estatísticos
    │   └── Footer.vue       # Rodapé do site
    │
    ├── views/               # Páginas principais da aplicação (renderizadas pelas rotas)
    │   ├── Home.vue         # Página inicial (landing page)
    │   ├── Login.vue        # Página de Login e Cadastro de usuários
    │   └── (futuro: Cadastro.vue, Dashboard.vue, etc)
    │
    └── router/              # Configuração do Vue Router (definição de rotas)
        └── index.js         # Arquivo que define todas as rotas do sistema
