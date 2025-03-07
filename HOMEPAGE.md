<html lang="es">
<head>
  <meta charset="utf-8"/>
  <meta content="width=device-width, initial-scale=1.0" name="viewport"/>
  <title>Art48</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" rel="stylesheet"/>
  <style>
    .nav-link {
      position: relative;
      padding: 0.5rem 1rem;
    }
    .nav-link:hover {
      background-color: rgba(242, 136, 75, 0.8);
    }
    .hover-text:hover {
      color: #F2884B;
    }
    .mobile-nav-link {
      position: relative;
    }
    .mobile-nav-link::after {
      content: '';
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(242, 136, 75, 0.8);
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    .mobile-nav-link:hover::after {
      opacity: 1;
    }
    .scroll-container {
      display: flex;
      overflow-x: auto;
      scroll-behavior: smooth;
      justify-content: flex-start;
    }
    .scroll-container::-webkit-scrollbar {
      display: none;
    }
    .scroll-arrow {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 50px;
      height: 450px;
      cursor: pointer;
    }
    .scroll-arrow i {
      transition: transform 0.3s ease;
    }
    .scroll-arrow:hover i {
      transform: scale(1.2);
    }
    .project-card {
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 400px;
      height: 450px;
      background-color: #595959;
      margin-right: 20px;
    }
    .project-card:hover .overlay {
      opacity: 1;
    }
    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.5rem;
      font-weight: bold;
      text-transform: uppercase;
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    @media (max-width: 768px) {
      .project-card {
        width: 400px;
        height: 450px;
        margin-right: 0;
      }
      .scroll-container {
        justify-content: flex-start;
      }
      .scroll-container > *:not(:first-child) {
        display: none;
      }
    }
    .tooltip {
      display: none;
      position: absolute;
      background-color: white;
      color: black;
      padding: 1rem;
      border: 1px solid #262626;
      border-radius: 0.5rem;
      z-index: 10;
    }
    .info-box {
      display: none;
      position: absolute;
      background-color: rgba(255, 255, 255, 0.9);
      color: black;
      padding: 2rem;
      border-radius: 0.5rem;
      z-index: 20;
      width: 80%;
      max-width: 500px;
    }
    .info-box h2 {
      margin-bottom: 1rem;
    }
    .info-box p {
      margin-bottom: 1rem;
    }
    .text-4xl:hover, .text-3xl:hover, .text-2xl:hover {
      color: #A9A9A9;
    }
  </style>
  <script>
    function scrollRight() {
      const container = document.querySelector('.scroll-container');
      container.scrollBy({ left: 420, behavior: 'smooth' });
      setTimeout(() => {
        const firstChild = container.firstElementChild;
        container.appendChild(firstChild);
      }, 300);
    }
    function toggleMenu() {
      const menu = document.getElementById('mobile-menu');
      menu.classList.toggle('hidden');
    }
    function showTooltip(event, text) {
      const tooltip = document.getElementById('tooltip');
      tooltip.innerHTML = text;
      tooltip.style.display = 'block';
      tooltip.style.left = `${event.pageX}px`;
      tooltip.style.top = `${event.pageY}px`;
    }
    function hideTooltip() {
      const tooltip = document.getElementById('tooltip');
      tooltip.style.display = 'none';
    }
    function showInfoBox(event, title, content) {
      const infoBox = document.getElementById('info-box');
      infoBox.querySelector('h2').innerText = title;
      infoBox.querySelector('p').innerText = content;
      infoBox.style.display = 'block';
      infoBox.style.left = `${event.pageX}px`;
      infoBox.style.top = `${event.pageY}px`;
    }
    function hideInfoBox() {
      const infoBox = document.getElementById('info-box');
      infoBox.style.display = 'none';
    }
    document.addEventListener('click', function(event) {
      const infoBox = document.getElementById('info-box');
      if (!event.target.closest('.info-box') && !event.target.closest('.text-4xl') && !event.target.closest('.text-3xl') && !event.target.closest('.text-2xl')) {
        hideInfoBox();
      }
    });
  </script>
</head>
<body class="relative bg-[#D9D9D9] text-[#262626]">
  <div class="relative h-screen">
    <img alt="Background image of a modern architectural building with a glass facade" class="absolute inset-0 w-full h-full object-cover" src="http://art48.archi/wp-content/uploads/2013/12/2014_MAGISTRAT_1.jpg"/>
    <div class="absolute inset-0 bg-black opacity-30"></div>
    <header class="absolute top-0 left-0 right-0 flex justify-between items-center p-6">
      <div class="text-white font-bold flex flex-col items-start">
        <span class="block text-5xl md:text-6xl tracking-wider hover-text">Art48</span>
        <div class="text-sm font-light tracking-wider">Architecture and design</div>
      </div>
      <nav class="hidden md:flex space-x-6 text-white text-sm">
        <a class="nav-link" href="https://www.blackbox.ai/screenshot/XMYaH3lbM0iWO854E0sbu?share=true">Projects</a>
        <a class="nav-link" href="#">Ecospace</a>
        <a class="nav-link" href="#">Team</a>
        <a class="nav-link" href="#">About</a>
        <a class="nav-link" href="#">Contact</a>
        <a class="nav-link" href="#">EN</a>
        <a class="nav-link" href="#">FR</a>
      </nav>
      <button class="md:hidden text-white text-2xl" onclick="toggleMenu()">
        <i class="fas fa-bars"></i>
      </button>
    </header>
    <div class="absolute bottom-0 left-0 right-0 p-6 text-white flex flex-col md:flex-row md:items-center md:justify-between md:px-[4cm]">
      <h1 class="text-xl md:text-2xl mb-4 md:mb-0 w-full text-center md:w-auto">¿Cómo te gustaría vivir?</h1>
      <p class="text-xs md:text-sm mb-6 md:mb-0 text-center md:text-left max-w-md mx-auto md:mx-0 md:ml-4">
        En tini construimos estilos de vida, formas de sentir y disfrutar espacios únicos. Espacios con vida para una vida mejor.
      </p>
    </div>
  </div>
  <div class="p-6">
    <p class="text-center text-lg md:text-xl mb-16">
      <strong>Great projects begin with great relationships.</strong>
    </p>
    <div>
      <h2 class="text-left text-2xl md:text-3xl font-bold mb-8" style="margin-left: 6cm; margin-bottom: 10cm;">Featured Projects</h2>
    </div>
    <div id="tooltip" class="tooltip"></div>
    <div id="info-box" class="info-box">
      <h2></h2>
      <p></p>
    </div>
    <footer class="p-6 flex flex-col md:flex-row justify-between text-xs md:text-sm mt-16">
      <div class="hidden md:block mb-8">
        <h3 class="font-bold text-5xl md:text-6xl tracking-wider mb-2">Art48</h3>
      </div>
      <div class="flex flex-col md:flex-row md:space-x-8">
        <div class="text-left">
          <h3 class="font-bold text-lg mb-2">Contact</h3>
          <p>123 Fake Street, City, Country</p>
          <p>+123 456 789</p>
          <p>info@art48.com</p>
        </div>
        <div class="text-right mt-4 md:mt-0">
          <h3 class="font-bold text-lg mb-2">Social Media</h3>
          <p>Facebook</p>
          <p>Twitter</p>
          <p>Instagram</p>
        </div>
      </div>
    </footer>
  </div>
  <div class="md:hidden fixed inset-0 bg-black bg-opacity-50 hidden" id="mobile-menu">
    <div class="bg-white bg-opacity-90 p-6 m-4 rounded-lg flex flex-col items-center">
      <button class="text-black text-2xl mb-4 self-end" onclick="toggleMenu()">
        <i class="fas fa-times"></i>
      </button>
      <nav class="space-y-4 text-black text-lg text-center">
        <a class="block mobile-nav-link" href="https://www.blackbox.ai/screenshot/XMYaH3lbM0iWO854E0sbu?share=true">Projects</a>
        <a class="block mobile-nav-link" href="#">Ecospace</a>
        <a class="block mobile-nav-link" href="#">Team</a>
        <a class="block mobile-nav-link" href="#">About</a>
        <a class="block mobile-nav-link" href="#">Contact</a>
        <a class="block mobile-nav-link" href="#">EN</a>
        <a class="block mobile-nav-link" href="#">FR</a>
      </nav>
    </div>
  </div>
  <script>
    document.addEventListener('click', function(event) {
      const infoBox = document.getElementById('info-box');
      if (!event.target.closest('.info-box') && !event.target.closest('.text-4xl') && !event.target.closest('.text-3xl') && !event.target.closest('.text-2xl')) {
        hideInfoBox();
      }
    });
  </script>
</body>
</html>
