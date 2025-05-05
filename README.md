<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="Portal TechYago - Conteúdo sobre Arquitetura, Sistemas, Web, HTML/CSS, Lógica, Robótica, Java, Gestão, Matemática e Redes." />
  <meta name="keywords" content="tecnologia, programação, web, desenvolvimento, Java, robótica, matemática" />
  <title>Portal TechYago</title>
  <link rel="icon" type="image/png" href="https://cdn-icons-png.flaticon.com/512/1055/1055646.png" />
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet" />

  <style>
    :root {
      --bg-main: #000;
      --bg-header: #0a0a0a;
      --bg-tab: #1a1a1a;
      --bg-card: #111;
      --highlight: #FFD700;
      --text-color: #4fc3f7;
    }
    /* Temas Light, Vibrant, Pastel, Cyber e Galaxy */
    body.theme-light {
      --bg-main: #f9fbfd;
      --bg-header: #e6f0fa;
      --bg-tab: #d0e5fb;
      --bg-card: #ffffff;
      --highlight: #468ef5;
      --text-color: #1e293b;
    }
    body.theme-vibrant {
      --bg-main: #fff7f0;
      --bg-header: #ff6f61;
      --bg-tab: #ffd166;
      --bg-card: #06d6a0;
      --highlight: #118ab2;
      --text-color: #073b4c;
    }
    body.theme-pastel {
      --bg-main: #fef6fb;
      --bg-header: #cdb4db;
      --bg-tab: #b5ead7;
      --bg-card: #fbc4ab;
      --highlight: #ffb5e8;
      --text-color: #645caa;
    }
    body.theme-cyber {
      --bg-main: #0d0d0d;
      --bg-header: #121212;
      --bg-tab: #1f1b24;
      --bg-card: #191919;
      --highlight: #00ffff;
      --text-color: #d1c4e9;
    }
    /* Tema Galaxy aprimorado */
    body.theme-galaxy {
      /* Fundo principal com gradiente espacial (pode ser ajustado para simular nebulosas) */
      --bg-main: radial-gradient(ellipse at bottom, #090a2e 0%, #0d0c30 60%, #050520 100%);
      --bg-header: #1c1b3a;
      --bg-tab: #292758;
      --bg-card: #1f1d44;
      --highlight: #c77dff;
      --text-color: #a0c4ff;
    }
    /* Fundo animado apenas para Galaxy */
    .galaxy-bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
      z-index: -1;
      pointer-events: none;
      /* Animação suave de gradiente para simular movimento espacial */
      background: radial-gradient(ellipse at center, rgba(9,10,46,0.8) 0%, rgba(13,12,48,0.8) 70%, rgba(5,5,32,0.8) 100%);
      animation: backgroundFlow 20s ease infinite alternate;
    }
    @keyframes backgroundFlow {
      0% { transform: scale(1) rotate(0deg); }
      100% { transform: scale(1.05) rotate(2deg); }
    }
    /* Criando várias estrelas usando pseudo-elementos */
    .galaxy-bg::before {
      content: "";
      position: absolute;
      top: 0; left: 0;
      width: 200%;
      height: 200%;
      background: transparent;
      background-image: 
        radial-gradient(white 1px, transparent 1px),
        radial-gradient(white 1px, transparent 1px);
      background-size: 3px 3px, 2px 2px;
      background-position: 0 0, 50% 50%;
      animation: starShift 50s linear infinite;
    }
    @keyframes starShift {
      from { transform: translateX(0) translateY(0); }
      to { transform: translateX(-50px) translateY(50px); }
    }
    /* Estilos aprimorados para as estrelas pontuais (além dos pseudo-elementos) */
    .star {
      position: absolute;
      width: 3px;
      height: 3px;
      background: white;
      border-radius: 50%;
      opacity: 0.8;
      animation: twinkle 3s infinite alternate;
    }
    .star:nth-child(2) { top: 15%; left: 70%; }
    .star:nth-child(3) { top: 40%; left: 30%; }
    .star:nth-child(4) { top: 65%; left: 80%; }
    .star:nth-child(5) { top: 80%; left: 20%; }
    @keyframes twinkle {
      from { opacity: 0.5; }
      to { opacity: 1; }
    }
    /* Meteoros com animação mais fluida */
    .meteor {
      position: absolute;
      width: 100px;
      height: 2px;
      background: linear-gradient(90deg, white, transparent);
      opacity: 0.8;
      animation: shoot 5s linear infinite;
    }
    @keyframes shoot {
      0% {
        transform: translateX(-120px) translateY(0) rotate(45deg);
        opacity: 1;
      }
      100% {
        transform: translateX(120vw) translateY(120vh) rotate(45deg);
        opacity: 0;
      }
    }
    /* Asteroides suavizados */
    .asteroid {
      position: absolute;
      width: 12px;
      height: 6px;
      background: #777;
      border-radius: 50%;
      transform: rotate(45deg);
      opacity: 0.7;
      animation: drift 8s linear infinite;
    }
    @keyframes drift {
      from { transform: translateX(0) translateY(0) rotate(45deg); }
      to { transform: translateX(100vw) translateY(100vh) rotate(405deg); }
    }
    /* Elementos Especiais permanecem, com leve ajuste de animação se necessário */
    .planet {
      position: absolute;
      width: 40px;
      height: 40px;
      background: radial-gradient(circle, #ff8fab, #a29bfe);
      border-radius: 50%;
      animation: float 6s ease-in-out infinite alternate;
    }
    @keyframes float {
      0% { transform: translateY(0); }
      100% { transform: translateY(20px); }
    }
    .earth {
      position: absolute;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      background: radial-gradient(circle at 20% 20%, #0b3d91, #1e90ff);
      border: 2px solid #fff;
      animation: float 8s ease-in-out infinite;
    }
    .moon {
      position: absolute;
      width: 30px;
      height: 30px;
      border-radius: 50%;
      background: #ccc;
      border: 1px solid #888;
      animation: float 6s ease-in-out infinite alternate;
    }
    .sun {
      position: absolute;
      width: 80px;
      height: 80px;
      border-radius: 50%;
      background: radial-gradient(circle, #ffdf00, #ff7f00);
      box-shadow: 0 0 20px rgba(255, 223, 0, 0.8);
      animation: float 10s ease-in-out infinite alternate;
    }
    .three-marias {
      position: absolute;
      width: 50px;
      height: 10px;
    }
    .three-marias .maria {
      position: absolute;
      width: 5px;
      height: 5px;
      background: white;
      border-radius: 50%;
      animation: twinkle 4s infinite alternate;
    }
    .three-marias .maria:nth-child(1) { left: 0; }
    .three-marias .maria:nth-child(2) { left: 20px; }
    .three-marias .maria:nth-child(3) { left: 40px; }
    .satellite {
      position: absolute;
      width: 20px;
      height: 10px;
      background: silver;
      border: 1px solid #fff;
      border-radius: 50%;
      animation: orbit 10s linear infinite;
    }
    .satellite:nth-of-type(1) {
      top: 22%;
      left: 45%;
      animation-duration: 8s;
    }
    .satellite:nth-of-type(2) {
      top: 60%;
      left: 10%;
      animation-duration: 12s;
    }
    @keyframes orbit {
      0% {
        transform: rotate(0deg) translateX(80px) rotate(0deg);
      }
      100% {
        transform: rotate(360deg) translateX(80px) rotate(-360deg);
      }
    }

    /* Reset e Configurações Globais */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: var(--bg-main);
      color: var(--text-color);
      transition: background 0.5s, color 0.5s;
    }
    header {
      background-color: var(--bg-header);
      padding: 1.5rem;
      text-align: center;
      font-size: 2.5rem;
      font-weight: bold;
      color: var(--highlight);
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
      border-bottom: 2px solid var(--highlight);
    }
    .theme-selector {
      position: fixed;
      top: 1rem;
      right: 1rem;
      display: flex;
      flex-wrap: wrap;
      gap: 0.5rem;
      z-index: 999;
    }
    .theme-selector button {
      padding: 0.5rem 0.8rem;
      border: none;
      border-radius: 0.5rem;
      cursor: pointer;
      font-weight: bold;
      color: white;
      transition: transform 0.2s;
    }
    .theme-selector button:hover {
      transform: scale(1.05);
    }
    nav {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      background-color: var(--bg-tab);
      padding: 0.5rem;
      border-bottom: 1px solid var(--highlight);
    }
    nav button {
      background-color: transparent;
      border: 1px solid var(--highlight);
      color: var(--text-color);
      padding: 0.75rem 1.25rem;
      margin: 0.25rem;
      font-size: 1rem;
      cursor: pointer;
      border-radius: 0.5rem;
      transition: background 0.3s, transform 0.2s, color 0.3s;
      position: relative;
      overflow: hidden;
    }
    nav button::after {
      content: '';
      position: absolute;
      top: 0; left: -75%;
      width: 50%;
      height: 100%;
      background: rgba(255, 255, 255, 0.2);
      transform: skewX(-20deg);
      animation: shimmer 2s infinite;
    }
    @keyframes shimmer {
      0% { left: -75%; }
      100% { left: 125%; }
    }
    nav button:hover, nav button:focus {
      background-color: var(--highlight);
      color: #000;
      transform: scale(1.05);
      outline: none;
    }
    #loader {
      text-align: center;
      padding: 2rem;
      font-size: 1.2rem;
      color: var(--highlight);
      display: none;
    }
    .content {
      padding: 2rem;
      display: none;
      animation: fadeIn 0.4s ease-in-out;
    }
    .content.active {
      display: block;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .card {
      background-color: var(--bg-card);
      border-radius: 1rem;
      padding: 1.5rem;
      margin-bottom: 1.5rem;
      box-shadow: 0 0 12px rgba(0, 255, 255, 0.15);
      border: 1px solid var(--highlight);
      transition: transform 0.3s;
    }
    .card:hover {
      transform: scale(1.02);
      box-shadow: 0 0 16px rgba(0, 255, 255, 0.3);
    }
    .card img {
      width: 100%;
      max-height: 200px;
      object-fit: cover;
      border-radius: 1rem;
      margin-bottom: 1rem;
    }
    footer {
      text-align: center;
      font-size: 0.9rem;
      padding: 2rem 1rem;
      border-top: 1px solid var(--highlight);
      margin-top: 2rem;
      background: linear-gradient(270deg, var(--highlight), var(--text-color));
      background-size: 400% 400%;
      animation: gradientFlow 10s ease infinite;
      color: #fff;
    }
    @keyframes gradientFlow {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    @media (max-width: 768px) {
      nav {
        flex-direction: column;
      }
      .card {
        padding: 1rem;
      }
    }
    #feedback {
      padding: 2rem;
      background: var(--bg-tab);
      border-top: 1px solid var(--highlight);
      margin-top: 2rem;
    }
    #feedback h2 {
      color: var(--highlight);
      margin-bottom: 1rem;
    }
    #feedback form label {
      display: block;
      margin-bottom: 0.5rem;
    }
    #feedback form input,
    #feedback form textarea {
      width: 100%;
      padding: 0.5rem;
      margin-bottom: 1rem;
      border: 1px solid var(--highlight);
      border-radius: 0.3rem;
    }
    #feedback form button {
      background: var(--highlight);
      color: #000;
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 0.3rem;
      cursor: pointer;
    }
    .feedback-item {
      opacity: 0;
      animation: fadeInFeedback 0.5s forwards;
      border-bottom: 1px solid var(--highlight);
      margin-bottom: 1rem;
      padding-bottom: 1rem;
    }
    @keyframes fadeInFeedback {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .custom-theme-panel {
      position: fixed;
      bottom: 1rem;
      right: 1rem;
      background: var(--bg-tab);
      padding: 1rem;
      border-radius: 8px;
      z-index: 999;
    }
    .custom-theme-panel label {
      margin-right: 0.5rem;
    }
    .menu-toggle {
      position: fixed;
      top: 1rem;
      left: 1rem;
      background: var(--highlight);
      color: #000;
      padding: 0.5rem 1rem;
      border: none;
      border-radius: 12px;
      font-size: 1.2rem;
      font-weight: bold;
      z-index: 1000;
      cursor: pointer;
      transition: background 0.3s;
    }
    .menu-toggle:hover {
      background: #fff;
    }
    .side-menu {
      position: fixed;
      top: 0;
      left: -270px;
      width: 250px;
      height: 100%;
      background: rgba(20, 20, 40, 0.95);
      backdrop-filter: blur(4px);
      box-shadow: 4px 0 12px rgba(0, 0, 0, 0.4);
      padding: 2rem 1rem;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      z-index: 999;
      transition: left 0.4s ease;
      border-right: 2px solid var(--highlight);
    }
    .side-menu a {
      color: var(--text-color);
      text-decoration: none;
      font-size: 1.1rem;
      border-bottom: 1px dashed var(--highlight);
      padding-bottom: 0.5rem;
      transition: color 0.3s;
    }
    .side-menu a:hover {
      color: #fff;
    }
    .side-menu.active {
      left: 0;
    }
    #searchInput {
      margin: 1rem auto;
      display: block;
      padding: 0.5rem;
      border-radius: 8px;
      border: 1px solid var(--highlight);
    }
    #btnTopo {
      position: fixed;
      bottom: 2rem;
      right: 2rem;
      background: var(--highlight);
      color: #000;
      border: none;
      padding: 0.75rem;
      border-radius: 50%;
      cursor: pointer;
      box-shadow: 0 0 10px var(--highlight);
      display: none;
      z-index: 1000;
    }
  </style>
</head>
<body class="theme-dark">
  <!-- Fundo animado Galaxy -->
  <div id="galaxyBackground" class="galaxy-bg" style="display: none;">
    <!-- Estrelas extras (elementos fixos) -->
    <div class="star" style="top:10%; left:20%;"></div>
    <div class="star" style="top:25%; left:80%;"></div>
    <div class="star" style="top:50%; left:30%;"></div>
    <div class="star" style="top:70%; left:75%;"></div>
    <div class="star" style="top:85%; left:15%;"></div>
    
    <!-- Meteoros -->
    <div class="meteor" style="top:10%; left:-120px;"></div>
    
    <!-- Asteroides -->
    <div class="asteroid" style="top:30%; left:10%;"></div>
    <div class="asteroid" style="top:50%; left:50%;"></div>
    <div class="asteroid" style="top:70%; left:80%;"></div>
    
    <!-- Planetas especiais -->
    <div class="earth" style="top:20%; left:40%;"></div>
    <div class="moon" style="top:50%; left:60%;"></div>
    <div class="sun" style="top:5%; left:5%;"></div>
    
    <!-- Três Marias (constelação) -->
    <div class="three-marias" style="top:85%; left:40%;">
      <div class="maria"></div>
      <div class="maria"></div>
      <div class="maria"></div>
    </div>
    
    <!-- Satélites -->
    <div class="satellite"></div>
    <div class="satellite" style="animation-duration: 12s; top:60%; left:10%;"></div>
  </div>

  <!-- Seletor de Temas -->
  <div class="theme-selector">
    <button onclick="setTheme('theme-dark')" style="background: #000">Escuro</button>
    <button onclick="setTheme('theme-light')" style="background: #468ef5">Claro</button>
    <button onclick="setTheme('theme-vibrant')" style="background: #ff6f61">Vibrante</button>
    <button onclick="setTheme('theme-pastel')" style="background: #ffb5e8">Pastel</button>
    <button onclick="setTheme('theme-cyber')" style="background: linear-gradient(45deg, #00ffff, #8a2be2)">Neo Cyber</button>
    <button onclick="setTheme('theme-galaxy')" style="background: linear-gradient(135deg, #a0c4ff, #c77dff); color: #000;">Galaxy</button>
  </div>

  <!-- Botão do menu lateral -->
  <button class="menu-toggle" onclick="toggleMenu()">☰ Menu</button>

  <!-- Menu Lateral -->
  <div id="sideMenu" class="side-menu">
    <a href="#" onclick="showTab('arquitetura'); toggleMenu()">🖥️ Arquitetura</a>
    <a href="#" onclick="showTab('sistemas'); toggleMenu()">🧠 Sistemas Operacionais</a>
    <a href="#" onclick="showTab('web'); toggleMenu()">🌐 Programação Web</a>
    <a href="#" onclick="showTab('htmlcss'); toggleMenu()">💻 HTML / CSS</a>
    <a href="#" onclick="showTab('logica'); toggleMenu()">🧩 Lógica de Programação</a>
    <a href="#" onclick="showTab('robotica'); toggleMenu()">🤖 Robótica</a>
    <a href="#" onclick="showTab('java'); toggleMenu()">☕ Java - POO</a>
    <a href="#" onclick="showTab('gestao'); toggleMenu()">⏱️ Gestão de Tempo</a>
    <a href="#" onclick="showTab('matematica'); toggleMenu()">➕ Matemática</a>
    <a href="#" onclick="showTab('redes'); toggleMenu()">📡 Redes</a>
  </div>

  <!-- Cabeçalho -->
  <header>Portal TechYago</header>

  <!-- Campo de busca -->
  <input type="text" id="searchInput" placeholder="Buscar matéria..." oninput="buscarAbas()">

  <!-- Navegação -->
  <nav role="tablist">
    <button role="tab" aria-controls="arquitetura" onclick="showTab('arquitetura')">🖥️ Arquitetura</button>
    <button role="tab" aria-controls="sistemas" onclick="showTab('sistemas')">🧠 Sistemas</button>
    <button role="tab" aria-controls="web" onclick="showTab('web')">🌐 Web</button>
    <button role="tab" aria-controls="htmlcss" onclick="showTab('htmlcss')">💻 HTML/CSS</button>
    <button role="tab" aria-controls="logica" onclick="showTab('logica')">🧩 Lógica</button>
    <button role="tab" aria-controls="robotica" onclick="showTab('robotica')">🤖 Robótica</button>
    <button role="tab" aria-controls="java" onclick="showTab('java')">☕ Java</button>
    <button role="tab" aria-controls="gestao" onclick="showTab('gestao')">⏱️ Gestão</button>
    <button role="tab" aria-controls="redes" onclick="showTab('redes')">📡 Redes</button>
  </nav>

  <!-- Loader -->
  <div id="loader">Carregando conteúdo...</div>

  <main>
    <!-- Aba Arquitetura -->
    <section id="arquitetura" class="content active" data-aos="fade-up">
      <div class="card">
        <h2>Arquitetura e Manutenção dos computadores</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Sistemas -->
    <section id="sistemas" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Sistemas Operacionais</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Web -->
    <section id="web" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Programação Web</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba HTML/CSS -->
    <section id="htmlcss" class="content" data-aos="fade-up">
      <div class="card">
         <h2>HTML/CSS</h2>
         <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Lógica -->
    <section id="logica" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Lógica de Programação</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Robótica -->
    <section id="robotica" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Noções de Robótica</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Java -->
    <section id="java" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Programação Orientada a Objetos em Java</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Gestão -->
    <section id="gestao" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Gestão Temporal</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Matemática -->
    <section id="matematica" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Matemática</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>
    <!-- Aba Redes -->
    <section id="redes" class="content" data-aos="fade-up">
      <div class="card">
        <h2>Redes</h2>
        <p>Conteúdos em breve...</p>
      </div>
    </section>

    <!-- Seção de Feedback -->
    <section id="feedback" data-aos="fade-up">
      <h2>Feedback dos Usuários</h2>
      <form id="feedbackForm">
        <label for="nome">Nome:</label>
        <input type="text" id="nome" name="nome" required>
        <label for="comentario">Comentário:</label>
        <textarea id="comentario" name="comentario" rows="4" required></textarea>
        <button type="submit">Enviar Feedback</button>
      </form>
      <div id="feedbackMessages">
        <!-- Comentários enviados aparecerão aqui -->
      </div>
    </section>
  </main>

  <!-- Botão "Voltar ao Topo" -->
  <button id="btnTopo" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">⬆️</button>

  <footer>
    Feito com 💛 por Yago — 2025<br>
    <a href="https://www.instagram.com/z_yago_1227" target="_blank" style="color:white; margin: 0 8px;">
      <img src="https://cdn-icons-png.flaticon.com/512/2111/2111463.png" width="20" style="vertical-align: middle;"> @z_yago_1227
    </a> |
    <a href="https://www.tiktok.com/@yago1227breck" target="_blank" style="color:white; margin: 0 8px;">
      <img src="https://cdn-icons-png.flaticon.com/512/3046/3046122.png" width="20" style="vertical-align: middle;"> TikTok
    </a> |
    <a href="https://www.instagram.com/nauanloures" target="_blank" style="color:white; margin: 0 8px;">
      <img src="https://cdn-icons-png.flaticon.com/512/2111/2111463.png" width="20" style="vertical-align: middle;"> @nauanloures
    </a>
  </footer>

  <!-- Painel de Customização de Tema -->
  <div class="custom-theme-panel">
    <label for="primaryColor">Destaque:</label>
    <input type="color" id="primaryColor" name="primaryColor" onchange="customTheme(this.value)">
  </div>

  <script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>
  <script>
    AOS.init();

    // Troca de abas com loader
    function showTab(tabId) {
      document.getElementById("loader").style.display = "block";
      setTimeout(() => {
        document.querySelectorAll('.content').forEach(c => c.classList.remove('active'));
        document.getElementById(tabId).classList.add('active');
        document.getElementById("loader").style.display = "none";
      }, 300);
    }

    // Altera tema e armazena preferência
    function setTheme(themeName) {
      document.body.className = themeName;
      localStorage.setItem('preferredTheme', themeName);
      document.getElementById("galaxyBackground").style.display = themeName === "theme-galaxy" ? "block" : "none";
    }
    window.onload = function() {
      const savedTheme = localStorage.getItem('preferredTheme');
      if (savedTheme) {
        setTheme(savedTheme);
      } else {
        if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
          setTheme('theme-dark');
        } else {
          setTheme('theme-light');
        }
      }
    }

    // Customiza a cor de destaque
    function customTheme(primaryColor) {
      document.documentElement.style.setProperty('--highlight', primaryColor);
    }

    // Processa formulário de feedback
    document.getElementById('feedbackForm').addEventListener('submit', function(event) {
      event.preventDefault();
      const nome = document.getElementById('nome').value;
      const comentario = document.getElementById('comentario').value;
      const feedbackItem = document.createElement('div');
      feedbackItem.classList.add('feedback-item');
      feedbackItem.innerHTML = `<strong>${nome}</strong> diz:<br> ${comentario}`;
      document.getElementById('feedbackMessages').appendChild(feedbackItem);
      this.reset();
    });

    // Busca nas abas
    function buscarAbas() {
      const termo = document.getElementById("searchInput").value.toLowerCase();
      document.querySelectorAll("main section.content").forEach(sec => {
        sec.style.display = sec.textContent.toLowerCase().includes(termo) ? "block" : "none";
      });
    }

    // Exibe botão "Voltar ao Topo"
    window.onscroll = function() {
      document.getElementById("btnTopo").style.display = window.scrollY > 300 ? "block" : "none";
    };

    // Alterna menu lateral
    function toggleMenu() {
      document.getElementById("sideMenu").classList.toggle("active");
    }
  </script>
</body>
</html>
