<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Carta para Arit — aRI</title>

  <!-- Fuentes -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg-1: #060316;
      --bg-2: #20013a;
      --accent-cyan: #00e6d3;
      --accent-pink: #ff5db1;
      --muted: rgba(230,240,255,0.95);
      --glass-border: rgba(255,255,255,0.04);
    }

    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: 'Montserrat', system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background:
        radial-gradient(800px 400px at 10% 10%, rgba(0,230,211,0.04), transparent 6%),
        radial-gradient(700px 360px at 90% 90%, rgba(255,93,177,0.03), transparent 6%),
        linear-gradient(120deg,var(--bg-1) 0%, var(--bg-2) 55%, #071431 100%);
      color:var(--muted);
      display:flex;
      align-items:center;
      justify-content:center;
      padding:48px;
    }

    .stage{
      width:100%;
      max-width:980px;
      border-radius:16px;
      overflow:hidden;
      position:relative;
      box-shadow: 0 20px 60px rgba(2,6,23,0.6);
      border:1px solid var(--glass-border);
      background: linear-gradient(180deg, rgba(255,255,255,0.01), rgba(0,0,0,0.02));
    }

    .content{
      position:relative;
      z-index:2;
      padding:36px;
      backdrop-filter: blur(4px);
      color:var(--muted);
    }

    header{
      text-align:center;
      margin-bottom:12px;
    }

    .title{
      font-family: 'Playfair Display', serif;
      font-size:2.4rem;
      color:#fff;
      margin:0;
      text-shadow: 0 8px 20px rgba(0,0,0,0.6);
    }

    .subtitle{
      margin-top:6px;
      color: rgba(230,240,255,0.85);
      font-size:0.95rem;
    }

    .main-grid{
      display:grid;
      grid-template-columns: 1fr 380px;
      gap:20px;
      align-items:start;
      margin-top:18px;
    }

    /* Carta (ahora con slideshow de fondo) */
    .letter{
      position:relative;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border-radius:12px;
      padding:28px;
      border:1px solid rgba(255,255,255,0.03);
      color:var(--muted);
      box-shadow: 0 10px 30px rgba(2,6,23,0.5);
      overflow:hidden;
      min-height:420px;
    }

    /* Contenedor para el slideshow (dentro de la carta) */
    .letter .bg-slideshow {
      position:absolute;
      inset:0;
      z-index:0;
      pointer-events:none;
      overflow:hidden;
    }
    .letter .bg-slide {
      position:absolute;
      inset:-10%;
      background-position:center;
      background-size:cover;
      filter: saturate(0.9) brightness(0.48) contrast(0.95) blur(2px);
      transform: scale(1.06);
      opacity:0;
      transition: opacity 1.2s ease-in-out;
    }
    .letter .bg-slide.visible { opacity:1; }

    /* Capa overlay para mejorar legibilidad del texto */
    .letter .bg-overlay {
      position:absolute;
      inset:0;
      background: linear-gradient(180deg, rgba(2,6,23,0.36), rgba(32,1,58,0.46));
      z-index:1;
      pointer-events:none;
    }

    /* Contenido real encima del fondo */
    .letter .inner {
      position:relative;
      z-index:2;
      max-width:820px;
    }

    h2{
      font-family: 'Playfair Display', serif;
      color: var(--accent-pink);
      text-align:center;
      margin:6px 0 14px 0;
    }

    p{
      margin:12px 0;
      line-height:1.65;
      font-size:1.02rem;
    }

    em{ color: var(--accent-cyan); font-weight:600; }

    .signature{ text-align:right; font-weight:700; margin-top:16px; color:rgba(255,255,255,0.95) }

    footer{ margin-top:18px; text-align:center; font-size:0.9rem; color:rgba(230,240,255,0.75); }

    /* Sidebar: reproductor + collage */
    .sidebar{
      display:flex;
      flex-direction:column;
      gap:12px;
    }

    .player {
      display:flex;
      flex-direction:column;
      gap:10px;
      align-items:center;
      justify-content:center;
      padding:12px;
      border-radius:10px;
      background: linear-gradient(180deg, rgba(0,0,0,0.28), rgba(0,0,0,0.36));
      border:1px solid rgba(255,255,255,0.03);
    }

    .player .hint{ font-size:0.85rem; color:rgba(230,240,255,0.9) }

    .youtube-wrap {
      width:100%;
      aspect-ratio:16/9;
      border-radius:8px;
      overflow:hidden;
      border:1px solid rgba(255,255,255,0.04);
      box-shadow: 0 8px 30px rgba(0,0,0,0.6);
      background:linear-gradient(180deg, rgba(0,0,0,0.35), rgba(0,0,0,0.45));
    }

    /* Collage grid */
    .collage{
      display:grid;
      grid-template-columns: repeat(2, 1fr);
      gap:8px;
      border-radius:10px;
      overflow:hidden;
      border:1px solid rgba(255,255,255,0.03);
      background: linear-gradient(180deg, rgba(255,255,255,0.012), rgba(255,255,255,0.01));
      padding:8px;
    }

    .collage img{
      width:100%;
      height:120px;
      object-fit:cover;
      display:block;
      border-radius:6px;
      cursor:pointer;
      transition: transform .25s ease, box-shadow .25s ease;
    }

    .collage img:hover{
      transform: translateY(-6px) scale(1.02);
      box-shadow: 0 12px 30px rgba(0,0,0,0.6);
    }

    /* Lightbox */
    .lightbox{
      position:fixed;
      inset:0;
      display:none;
      align-items:center;
      justify-content:center;
      background: rgba(2,6,23,0.8);
      z-index:9999;
      padding:20px;
    }
    .lightbox img{
      max-width:calc(100% - 80px);
      max-height:calc(100% - 80px);
      box-shadow: 0 24px 80px rgba(0,0,0,0.8);
      border-radius:8px;
    }
    .lightbox:target{ display:flex; }

    @media (max-width:960px){
      .main-grid{ grid-template-columns: 1fr; }
      .youtube-wrap{ aspect-ratio:16/9; }
      .collage img{ height:90px; }
    }
  </style>
</head>

<body>
  <div class="stage" role="main" aria-labelledby="main-title">
    <div class="content">
      <header>
        <h1 id="main-title" class="title">✨ Carta para Arit ✨</h1>
        <div class="subtitle">una página para Arit — estética inspirada en Gustavo Cerati</div>
      </header>

      <div class="main-grid">
        <article class="letter" aria-label="Carta">
          <!-- Slideshow background container -->
          <div class="bg-slideshow" aria-hidden="true" id="bg-slideshow">
            <!-- Slides will be injected by JS -->
          </div>

          <!-- Overlay para legibilidad -->
          <div class="bg-overlay" aria-hidden="true"></div>

          <!-- Contenido real encima del fondo -->
          <div class="inner">
            <p><em>🌌 Entre acordes y melodías, la vida nos regala encuentros inesperados.</em> Como si una canción de Gustavo Cerati hubiera tejido los hilos invisibles del destino, nuestras historias se cruzaron y descubrí que la amistad puede nacer en los lugares más mágicos.</p>

            <h2>Querida Arit</h2>

            <p>Quiero que sepas que estoy para ti. Que puedes contar conmigo en cada momento, en cada instante en que necesites apoyo, compañía o simplemente alguien que te recuerde lo especial que eres. No importa la distancia ni el tiempo: la amistad verdadera atraviesa todo eso.</p>

            <p>En este poco tiempo que hemos compartido, te has convertido en alguien muy importante para mí. Tu esencia, tu forma de ver el mundo y tu manera de iluminar con tu presencia han dejado una huella profunda. Cada charla, cada risa y cada silencio compartido me han mostrado lo valiosa que es nuestra conexión.</p>

            <p>Y aunque ahora me encuentre en Moquegua, quiero que sepas que mi regreso traerá consigo muchos detalles pensados con cariño, gestos que te hagan sentir especial y que te arranquen sonrisas sinceras. La distancia no enfría el afecto; lo hace más fuerte, más decidido.</p>

            <p>Nuestra amistad nació de algo tan simple y a la vez tan grande: compartir la admiración por Gustavo Cerati. Sus canciones fueron el puente que nos unió, y ahora ese puente se ha convertido en camino para seguir conociéndonos y acompañarnos en lo que venga.</p>

            <p>No olvides nunca que te quiero mucho, que mi cariño por ti es sincero y que mi amistad es un refugio al que siempre podrás acudir. Esta carta es solo un reflejo de lo que siento, pero lo más importante está en los momentos que vendrán.</p>

            <p><em>🌠 Así como Cerati cantaba que “mereces lo que sueñas”, yo sueño con verte feliz, con acompañarte en cada paso y con seguir construyendo esta amistad que ya se siente eterna.</em></p>

            <p class="signature">Con mucho cariño,<br>Benjamín 🌹</p>
          </div>
        </article>

        <aside class="sidebar" aria-label="Multimedia y collage">
          <div class="player" aria-label="Reproductor de música">
            <div class="hint">Reproducir «Perdonar es divino» — Gustavo Cerati</div>

            <!-- Incrustado usando el ID que me diste -->
            <div class="youtube-wrap" title="Perdonar es divino — Gustavo Cerati">
              <iframe
                src="https://www.youtube.com/embed/C3h5NmHDy0w?rel=0&showinfo=0"
                width="560" height="315"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen
                aria-label="Video de YouTube: Perdonar es divino">
              </iframe>
            </div>

            <div style="font-size:0.82rem; color:rgba(230,240,255,0.75); text-align:center; margin-top:6px;">
              Nota: se está usando un embed de YouTube; respeta derechos de autor al compartir o redistribuir.
            </div>
          </div>

          <div class="collage" aria-label="Collage de fotos de Gustavo Cerati">
            <!-- Reemplaza las imágenes por tus propias fotos en assets/ si lo prefieres -->
            <img src="assets/cerati-1.jpg" alt="Gustavo Cerati 1" loading="lazy" data-full="assets/cerati-1.jpg">
            <img src="assets/cerati-2.jpg" alt="Gustavo Cerati 2" loading="lazy" data-full="assets/cerati-2.jpg">
            <img src="assets/cerati-3.jpg" alt="Gustavo Cerati 3" loading="lazy" data-full="assets/cerati-3.jpg">
            <img src="assets/cerati-4.jpg" alt="Gustavo Cerati 4" loading="lazy" data-full="assets/cerati-4.jpg">
            <img src="assets/cerati-5.jpg" alt="Gustavo Cerati 5" loading="lazy" data-full="assets/cerati-5.jpg">
            <img src="assets/cerati-6.jpg" alt="Gustavo Cerati 6" loading="lazy" data-full="assets/cerati-6.jpg">
          </div>
        </aside>
      </div>

      <footer>
        Página creada con cariño para Arit — estilo inspirado en Gustavo Cerati.
        <div style="margin-top:8px; font-size:0.82rem; color:rgba(230,240,255,0.7)">
          Nota: las imágenes del fondo se guardarán en <code>assets/</code>. Confírmame que proceda con la descarga y el commit.
        </div>
      </footer>
    </div>
  </div>

  <!-- Lightbox simple (sin dependencias) -->
  <div id="lightbox" class="lightbox" role="dialog" aria-hidden="true" onclick="closeLightbox()">
    <img id="lightbox-img" src="" alt="Foto ampliada">
  </div>

  <script>
    // Lightbox básico
    const imgs = document.querySelectorAll('.collage img');
    const lightbox = document.getElementById('lightbox');
    const lbImg = document.getElementById('lightbox-img');

    imgs.forEach(img => {
      img.addEventListener('click', (e) => {
        const src = img.dataset.full || img.src;
        lbImg.src = src;
        lightbox.style.display = 'flex';
        lightbox.setAttribute('aria-hidden', 'false');
      });
    });

    function closeLightbox(){
      lightbox.style.display = 'none';
      lightbox.setAttribute('aria-hidden', 'true');
      lbImg.src = '';
    }

    // Cerrar con Esc
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') closeLightbox();
    });

    // ========== SLIDESHOW DE FONDO (CROSSFADE) ==========
    (function(){
      const bgContainer = document.getElementById('bg-slideshow');
      // Rutas locales (serán añadidas a assets/cerati-1..6)
      const backgrounds = [
        "assets/cerati-1.jpg",
        "assets/cerati-2.jpg",
        "assets/cerati-3.jpg",
        "assets/cerati-4.jpg",
        "assets/cerati-5.jpg",
        "assets/cerati-6.jpg"
      ];

      // Crear dos capas para crossfade
      const slideA = document.createElement('div');
      const slideB = document.createElement('div');
      slideA.className = 'bg-slide';
      slideB.className = 'bg-slide';
      bgContainer.appendChild(slideA);
      bgContainer.appendChild(slideB);

      let idx = 0;
      let visible = slideA;
      let hidden = slideB;

      // Inicial
      visible.style.backgroundImage = `url('${backgrounds[idx]}')`;
      visible.classList.add('visible');

      function nextSlide(){
        idx = (idx + 1) % backgrounds.length;
        hidden.style.backgroundImage = `url('${backgrounds[idx]}')`;
        requestAnimationFrame(() => {
          hidden.classList.add('visible');
          visible.classList.remove('visible');
          const tmp = visible;
          visible = hidden;
          hidden = tmp;
        });
      }

      const INTERVAL = 6000;
      let timer = setInterval(nextSlide, INTERVAL);

      document.addEventListener('visibilitychange', () => {
        if (document.hidden) clearInterval(timer);
        else timer = setInterval(nextSlide, INTERVAL);
      });
    })();
  </script>
</body>
</html>
