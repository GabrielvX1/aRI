<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Carta para Arit — aRI</title>

  <!-- Fuentes: serif elegante para títulos y sans para cuerpo -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Montserrat:wght@300;400;600&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg-1: #060316;     /* nocturno */
      --bg-2: #20013a;     /* púrpura profundo */
      --accent-cyan: #00e6d3; /* brillo electrónico */
      --accent-pink: #ff5db1; /* neón cálido */
      --glass: rgba(255,255,255,0.04);
      --glass-border: rgba(255,255,255,0.06);
      --muted: rgba(230,240,255,0.85);
    }

    /* Reset / Base */
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;
      font-family: 'Montserrat', system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: radial-gradient(1000px 600px at 10% 10%, rgba(0,230,211,0.06), transparent 10%),
                  radial-gradient(900px 500px at 90% 90%, rgba(255,93,177,0.04), transparent 10%),
                  linear-gradient(120deg,var(--bg-1) 0%, var(--bg-2) 55%, #071431 100%);
      color: var(--muted);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:48px;
    }

    /* Contenedor principal */
    .card{
      width:100%;
      max-width:960px;
      border-radius:16px;
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border: 1px solid var(--glass-border);
      box-shadow: 0 20px 50px rgba(2,6,23,0.6), inset 0 1px 0 rgba(255,255,255,0.02);
      overflow:hidden;
      position:relative;
      padding:36px;
      backdrop-filter: blur(6px) saturate(1.05);
    }

    /* Decoración sutil: líneas y onda (estética sonora) */
    .card::before{
      content: "";
      position:absolute;
      left:-10%;
      top: -30%;
      width:120%;
      height:160%;
      background:
        radial-gradient(800px 160px at 10% 10%, rgba(0,230,211,0.06), transparent 8%),
        radial-gradient(700px 140px at 90% 90%, rgba(255,93,177,0.04), transparent 8%);
      transform:rotate(-6deg);
      pointer-events:none;
      z-index:0;
    }

    header{
      position:relative;
      z-index:2;
      text-align:center;
      padding:28px 12px;
      margin-bottom:18px;
    }

    .title{
      display:inline-block;
      font-family: 'Playfair Display', serif;
      font-size:2.6rem;
      letter-spacing:0.02em;
      color:#fff;
      text-shadow:
        0 6px 24px rgba(0,0,0,0.6),
        0 0 12px rgba(0,230,211,0.06);
      margin:0;
    }

    .subtitle{
      margin-top:8px;
      color:rgba(230,240,255,0.8);
      font-size:0.95rem;
      opacity:0.95;
    }

    /* Onda SVG pequeña */
    .wave{
      margin-top:16px;
      height:34px;
      opacity:0.9;
      filter: drop-shadow(0 8px 24px rgba(0,0,0,0.6));
    }

    /* Sección principal tipo "carta" */
    .letter{
      position:relative;
      z-index:2;
      background: linear-gradient(180deg, rgba(255,255,255,0.015), rgba(255,255,255,0.01));
      border-radius:12px;
      padding:34px;
      margin: 12px auto 0 auto;
      max-width:880px;
      color:var(--muted);
      border: 1px solid rgba(255,255,255,0.03);
      box-shadow: 0 12px 30px rgba(2,6,23,0.5);
    }

    h2{
      font-family: 'Playfair Display', serif;
      color: var(--accent-pink);
      font-size:1.6rem;
      margin:0 0 12px 0;
      text-align:center;
      letter-spacing:0.02em;
      text-shadow: 0 6px 18px rgba(0,0,0,0.6);
    }

    p{
      margin:16px 0;
      line-height:1.65;
      font-size:1.05rem;
      color:rgba(230,240,255,0.95);
    }

    em{
      color:var(--accent-cyan);
      font-style:normal;
      font-weight:600;
      display:inline-block;
      letter-spacing:0.01em;
    }

    /* Firma */
    .signature{
      text-align:right;
      font-weight:700;
      margin-top:18px;
      color: rgba(255,255,255,0.95);
      font-size:1.05rem;
    }

    /* Pie */
    footer{
      margin-top:26px;
      text-align:center;
      font-size:0.9rem;
      color:rgba(230,240,255,0.7);
      opacity:0.95;
    }

    /* Pequeños toques neón para enlaces/acentos */
    .neon{
      color:var(--accent-cyan);
      text-shadow: 0 0 10px rgba(0,230,211,0.22), 0 6px 16px rgba(0,0,0,0.6);
      font-weight:600;
    }

    /* Responsivo */
    @media (max-width:640px){
      .title{font-size:1.8rem}
      .letter{padding:22px}
      p{font-size:1rem}
    }
  </style>
</head>

<body>
  <div class="card" role="main" aria-labelledby="main-title">
    <header>
      <h1 id="main-title" class="title">✨ Carta para Arit ✨</h1>
      <div class="subtitle">una página para Arit — inspirada en la estética de Gustavo Cerati</div>

      <!-- Onda decorativa SVG: sugiere sonido / atmósfera -->
      <svg class="wave" viewBox="0 0 1200 60" preserveAspectRatio="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
        <defs>
          <linearGradient id="g" x1="0" x2="1">
            <stop offset="0" stop-color="#00e6d3" stop-opacity="0.28"/>
            <stop offset="1" stop-color="#ff5db1" stop-opacity="0.2"/>
          </linearGradient>
        </defs>
        <path d="M0 30 C200 10 400 50 600 30 C800 10 1000 50 1200 30 L1200 60 L0 60 Z" fill="url(#g)"/>
      </svg>
    </header>

    <article class="letter" aria-label="Carta">
      <p><em>🌌 Entre acordes y melodías, la vida nos regala encuentros inesperados.</em> Como si una canción de Gustavo Cerati hubiera tejido los hilos invisibles del destino, nuestras historias se cruzaron y descubrí que la amistad puede nacer en los lugares más mágicos.</p>

      <h2>Querida Arit</h2>

      <p>Quiero que sepas que estoy para ti. Que puedes contar conmigo en cada momento, en cada instante en que necesites apoyo, compañía o simplemente alguien que te recuerde lo especial que eres. No importa la distancia ni el tiempo: la amistad verdadera atraviesa todo eso.</p>

      <p>En este poco tiempo que hemos compartido, te has convertido en alguien muy importante para mí. Tu esencia, tu forma de ver el mundo y tu manera de iluminar con tu presencia han dejado una huella profunda. Cada charla, cada risa y cada silencio compartido me han mostrado lo valiosa que es nuestra conexión.</p>

      <p>Y aunque ahora me encuentre en Moquegua, quiero que sepas que mi regreso traerá consigo muchos detalles pensados con cariño, gestos que te hagan sentir especial y que te arranquen sonrisas sinceras. La distancia no enfría el afecto; lo hace más fuerte, más decidido.</p>

      <p>Nuestra amistad nació de algo tan simple y a la vez tan grande: compartir la admiración por Gustavo Cerati. Sus canciones fueron el puente que nos unió, y ahora ese puente se ha convertido en camino para seguir conociéndonos y acompañarnos en lo que venga.</p>

      <p>No olvides nunca que te quiero mucho, que mi cariño por ti es sincero y que mi amistad es un refugio al que siempre podrás acudir. Esta carta es solo un reflejo de lo que siento, pero lo más importante está en los momentos que vendrán.</p>

      <p><em>🌠 Así como Cerati cantaba que “mereces lo que sueñas”, yo sueño con verte feliz, con acompañarte en cada paso y con seguir construyendo esta amistad que ya se siente eterna.</em></p>

      <p class="signature">Con mucho cariño,<br>Benjamín 🌹</p>
    </article>

    <footer>
      Página creada con cariño para Arit — estilo inspirado en Gustavo Cerati. Si quieres, puedo ajustar colores, tipografías o añadir animaciones suaves (parallax, aparición de acordes).
    </footer>
  </div>
</body>
</html>
