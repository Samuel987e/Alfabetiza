# Alfabetiza
AlfabetizaJá — PWA de Alfabetização Gamificada (ODS 4)

"Assegurar a educação inclusiva, equitativa e de qualidade e promover oportunidades de aprendizagem ao longo da vida para todos." — foco em alfabetização básica e leitura precoce.




---

1) Descrição do Problema

Muitas crianças (especialmente em áreas vulneráveis) têm acesso limitado a recursos de alfabetização de qualidade fora da escola. Falta material educativo acessível que funcione offline, com feedback imediato e que motive o aprendizado continuado.

Problema específico: baixa frequência de práticas de leitura e insuficiência de exercícios interativos que mantenham crianças engajadas entre aulas presenciais.

2) Justificativa (vínculo com ODS 4)

Alfabetização é a base para todos os demais aprendizados e oportunidades. Uma PWA acessível e leve permite alcance em dispositivos baratos e com internet intermitente — alinhando-se à meta do ODS 4 de ampliação do acesso e qualidade educacional. O projeto incorpora boas práticas de UX, acessibilidade (WCAG 2.1) e critérios de qualidade do software (ISO/IEC 25010).

3) Público-Alvo

Crianças de 5 a 9 anos em fase de alfabetização inicial.

Professores e mediadores escolares que buscam material complementar.

Famílias com acesso limitado a aplicativos instaláveis (por isso PWA).


4) Objetivos do App (metas mensuráveis)

1. Disponibilizar 50 lições curtas (níveis) nas áreas: letras, sílabas, palavras e leitura simples até o final da segunda versão.


2. Aumentar em 20% a taxa de acerto médio do usuário em exercícios após 4 semanas de uso (avaliado em estudos de usabilidade / testes com 20 usuários piloto).


3. Suportar uso offline total após o primeiro carregamento (Service Worker + cache) e funcionar em navegadores móveis base (Android 7+, iOS 12+).


4. Cumprir nível AA de acessibilidade WCAG 2.1 para interfaces básicas.



5) Tipo de Aplicação

PWA (Progressive Web App) — escolhida por: instalação via navegador (sem lojas), baixo custo de distribuição, funcionamento offline (Service Worker) e ampla compatibilidade com dispositivos econômicos.

6) MVP — Funcionalidades Principais

Tela Home: apresentação de avatar do usuário, progresso e botão "Continuar".

Trilhas de Aprendizado (Níveis): lições curtas com tarefas interativas (arrastar sílabas, completar palavras, ouvir e repetir).

Modo Offline: todo conteúdo do nível atual e próximos 3 níveis armazenados localmente.

Feedback Imediato: correção com dicas, medalhas e pontos.

Perfil / Progresso: histórico simples e estatísticas (acertos/erros por nível).

Acessibilidade: suporte a leitura por voz (TTS), alto contraste e textos escaláveis.


7) Fluxo de Tela (alto nível)

1. Splash → Home


2. Home → Seleção de Nível / Continuar


3. Nível (instrução → exercício → feedback) → Próximo / Repetir


4. Perfil → Estatísticas



8) Tecnologias e Arquitetura

Frontend: HTML5, CSS3, JavaScript (ES6+), framework: Vue 3 ou React (PWA friendly). Recomenda-se Vue para rapidez no protótipo.

Service Worker: Workbox (ou implementação manual) para cache e fallback offline.

Armazenamento local: IndexedDB (via idb library) para dados estruturados; fallback localStorage para configurações pequenas.

Backend (opcional para versão 2): Firebase (Auth + Firestore) ou Supabase para sincronização e login de professores.

Build & Deploy: Vite + Netlify / Firebase Hosting.


9) Requisitos do Sistema

Navegadores: Chrome Android (versão 80+), Firefox Android (v68+), Safari iOS (v12+) — testes recomendados.

Dispositivo: smartphones com 1GB RAM e conexões móveis (3G) — app otimizado para baixo consumo de dados.

Dependências (exemplo): Node.js v18+, npm/yarn, Workbox, idb, Vue/React.


10) Instalação e Uso (MVP local)

Pré-requisitos

Node.js e npm instalados.


Passos (rodando localmente)

1. Clonar repositório: git clone https://github.com/SEU_USUARIO/alfabetizaja-pwa.git


2. Entrar na pasta: cd alfabetizaja-pwa


3. Instalar dependências: npm install


4. Rodar em modo dev: npm run dev


5. Build para produção: npm run build


6. Servir build: npm run preview ou fazer deploy para Netlify/Vercel/Firebase Hosting.



Credenciais de teste (MVP sem backend): não aplicável — o app usa perfil local; para testes com backend (versão 2) serão fornecidas credenciais em README do backend.

11) Requisitos de Acessibilidade (WCAG 2.1 AA)

Textos com contraste mínimo 4.5:1 para corpo e 3:1 para títulos grandes.

Navegabilidade por teclado (Tab order lógico).

Labels explícitos em inputs e botões aria-label/aria-describedby.

TTS (ouvir instruções) e alternativas textuais para imagens.

Tamanho de toque mínimo 44x44px para botões.


12) UX/UI — Diretrizes Visuais

Paleta: tons amigáveis e alto contraste; cor primária roxa (considerando preferência do usuário), cor secundária amarela para acentos.

Tipografia: fonte sans-serif legível, escalonada (16px base).

Componentes: uso de cards, botões com estados (hover/focus/disabled) e microfeedbacks (som/ânimações suaves via CSS/Framer Motion em versões web avançadas).

Layout responsivo: grid fluido, tamanho de fonte ajustável via preferências.


13) Evidências Visuais (entrega)

Incluir no repositório a pasta /screenshots com, no mínimo, 3 imagens:

home.png — tela inicial com progresso.

menu_niveis.png — seleção de níveis/trilhas.

exercicio.png — um exercício com feedback após tentativa.


> Se possível, incluir também um pequeno vídeo (30–60s) demonstrando fluxo "abrir app → completar 1 exercício → ver medalha".



14) Banco de Dados / BaaS (opcional)

MVP: armazenamento local (IndexedDB) sem backend.

Versão 2: autenticação de professores e sincronização via Firebase Auth + Firestore ou Supabase. Esquema proposto:

users/{userId}: perfil, idade, progresso

lessons/{lessonId}: conteúdo, exercícios

attempts/{userId}/{attemptId}: histórico de tentativas



15) Testes e Avaliação Técnica

Testes manuais (20 usuários piloto): registrar tempo por lição, taxa de acerto, feedback qualitativo.

Testes de desempenho: Lighthouse (PWA score), Time to Interactive (TTI) < 5s em dispositivos de entrada.

Verificação de acessibilidade: Lighthouse Accessibility + axe-core.


16) Métrica de Sucesso (relacionada à rubrica)

README completo e claro → 20%.

App funcional (MVP executável no navegador + PWA installable) → 35%.

UX/UI com consistência e acessibilidade → 20%.

Capturas de tela (mín. 3) → 10%.

Relevância social e vínculo ao ODS → 15%.


17) Roadmap de Implementação (sprints)

Sprint 1 (1–2 semanas): protótipo de alta fidelidade (Figma/Canva) + README. Sprint 2 (2 semanas): implementação base (Home, Níveis, 5 lições interativas) + Service Worker offline. Sprint 3 (1 semana): Acessibilidade, TTS e perfil local. Sprint 4 (1 semana): Testes piloto, ajustes UX e preparo de screenshots e entrega.

18) Checklist de Entrega

[ ] README.md completo (este documento)

[ ] Repositório GitHub com código (link)

[ ] Build PWA hospedado (Netlify / Firebase Hosting) ou instruções de preview

[ ] Pasta /screenshots com home.png, menu_niveis.png, exercicio.png

[ ] Evidências adicionais (vídeo curto opcional)


19) Referências

ONU — Objetivos de Desenvolvimento Sustentável. Acesso em 15 set. 2025.

Google Material Design: https://m3.material.io. Acesso em 15 set. 2025.

ABNT NBR ISO/IEC 25010 (Qualidade de Produto), 2011.

WCAG 2.1 — Guidelines de Acessibilidade.



---

Anexos (rápido protótipo de código — index.html básico)

<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>AlfabetizaJá</title>
  <link rel="manifest" href="/manifest.json">
</head>
<body>
  <div id="app">Carregando AlfabetizaJá...</div>
  <script>
    // Exemplo mínimo: mostrar progresso salvo no localStorage
    document.addEventListener('DOMContentLoaded',()=>{
      const root=document.getElementById('app');
      const prog=localStorage.getItem('progress')||0;
      root.innerHTML=`<h1>AlfabetizaJá</h1><p>Progresso: ${prog}%</p><button id="add">+5%</button>`;
      document.getElementById('add').addEventListener('click',()=>{
        const n=Math.min(100,Number(localStorage.getItem('progress')||0)+5);
        localStorage.setItem('progress',n);
        root.querySelector('p').textContent=`Progresso: ${n}%`;
      });
    });
  </script>
</body>
</html>


---

