<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Fussion Games Store</title>

  <link rel="icon" href="file:///C:/Users/Julian%20Mendoza/Downloads/fgs.png">
  <!-- =========================================================
       FUENTES: Orbitron (display gamer) + Rajdhani (body clean)
       ========================================================= -->
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;700;900&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>

  <style>
    /* ============================================================
       CSS VARIABLES – Paleta de colores extraída de la imagen
       ============================================================ */
    :root {
      --blue:      #0597F2;   /* Azul primario             */
      --green:     #03A66A;   /* Verde acento              */
      --red:       #F20505;   /* Rojo vibrante             */
      --darkred:   #A60303;   /* Rojo oscuro               */
      --deepred:   #590202;   /* Rojo profundo / sombras   */

      --bg:        #0a0a0f;   /* Fondo principal casi negro */
      --bg2:       #12121a;   /* Fondo secundario tarjetas  */
      --bg3:       #1a1a26;   /* Fondo terciario hover      */
      --border:    rgba(5,151,242,0.18); /* Bordes sutiles azul */
      --text:      #e8e8f0;   /* Texto principal            */
      --muted:     #7a7a9a;   /* Texto secundario           */

      --font-display: 'Orbitron', monospace;
      --font-body:    'Rajdhani', sans-serif;

      --radius:    6px;
      --radius-lg: 12px;
      --transition: 0.22s ease;
    }

    /* ============================================================
       RESET & BASE
       ============================================================ */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--font-body);
      font-size: 16px;
      line-height: 1.6;
      overflow-x: hidden;
    }

    a { color: inherit; text-decoration: none; }
    ul { list-style: none; }
    img { display: block; max-width: 100%; }

    /* Scrollbar personalizada */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--blue); border-radius: 3px; }

    /* ============================================================
       1. BANNER SUPERIOR – Noticias / avisos importantes
       ============================================================ */
    #top-banner {
      background: linear-gradient(90deg, var(--deepred), var(--darkred), var(--red));
      color: #fff;
      font-family: var(--font-body);
      font-size: 0.85rem;
      font-weight: 600;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      padding: 8px 0;
      position: relative;
      overflow: hidden;
    }

    /* Marquee / ticker de noticias */
    .banner-ticker {
      display: flex;
      align-items: center;
      gap: 60px;
      white-space: nowrap;
      animation: ticker 30s linear infinite;
      width: max-content;
    }

    .banner-ticker span {
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .banner-ticker span::before {
      content: '◆';
      color: rgba(255,255,255,0.6);
      font-size: 0.6rem;
    }

    @keyframes ticker {
      from { transform: translateX(0); }
      to   { transform: translateX(-50%); }
    }

    /* Botón cerrar banner */
    #banner-close {
      position: absolute;
      right: 12px; top: 50%;
      transform: translateY(-50%);
      background: none; border: none;
      color: rgba(255,255,255,0.7);
      cursor: pointer; font-size: 1.1rem;
      z-index: 10;
      transition: color var(--transition);
    }
    #banner-close:hover { color: #fff; }

    /* ============================================================
       2. HEADER – Logo + nombre + Login/Registro + Carrito
       ============================================================ */
    #header {
      background: var(--bg2);
      border-bottom: 1px solid var(--border);
      position: sticky;
      top: 0;
      z-index: 1000;
      backdrop-filter: blur(12px);
    }

    .header-inner {
      max-width: 1400px;
      margin: 0 auto;
      padding: 0 24px;
      height: 68px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
    }

    /* --- Logo y nombre de la tienda --- */
    .logo-area {
      display: flex;
      align-items: center;
      gap: 12px;
      cursor: pointer;
    }

    /* *** IMAGEN DEL LOGO ***
         Reemplaza el div.logo-icon con:
         <img src="URL_O_RUTA_DEL_LOGO" alt="PixelVault Logo" style="height:44px;width:44px;object-fit:contain;" />
    */
    .logo-icon {
      width: 44px; height: 44px;
      background: linear-gradient(135deg, var(--red), var(--darkred));
      border-radius: var(--radius);
      display: flex; align-items: center; justify-content: center;
      font-family: var(--font-display);
      font-weight: 900; font-size: 1.2rem;
      color: #fff;
      box-shadow: 0 0 16px rgba(5,151,242,0.4);
      flex-shrink: 0;
    }

    .logo-name {
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 1.35rem;
      letter-spacing: 0.06em;
      background: linear-gradient(90deg, var(--blue), var(--green));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .logo-tagline {
      font-size: 0.65rem;
      color: var(--muted);
      letter-spacing: 0.12em;
      text-transform: uppercase;
      display: block;
      margin-top: -4px;
    }

    /* --- Barra de búsqueda (centro) --- */
    .search-bar {
      flex: 1;
      max-width: 480px;
      position: relative;
    }

    .search-bar input {
      width: 100%;
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: 30px;
      padding: 9px 44px 9px 18px;
      color: var(--text);
      font-family: var(--font-body);
      font-size: 0.9rem;
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
    }

    .search-bar input::placeholder { color: var(--muted); }

    .search-bar input:focus {
      border-color: var(--blue);
      box-shadow: 0 0 12px rgba(5,151,242,0.25);
    }

    .search-bar button {
      position: absolute;
      right: 12px; top: 50%;
      transform: translateY(-50%);
      background: none; border: none;
      color: var(--muted); cursor: pointer;
      font-size: 1rem;
      transition: color var(--transition);
    }
    .search-bar button:hover { color: var(--blue); }

    /* --- Acciones del header (Login + Carrito) --- */
    .header-actions {
      display: flex;
      align-items: center;
      gap: 12px;
      flex-shrink: 0;
    }

    /* Botón login/registro
       NOTE: Cuando haya BD funcional, reemplazar por .user-avatar (círculo con foto de perfil)
       Ver comentario más abajo
    */
    .btn-login {
      display: flex;
      align-items: center;
      gap: 8px;
      background: transparent;
      border: 1.5px solid var(--blue);
      color: var(--blue);
      border-radius: 30px;
      padding: 7px 18px;
      font-family: var(--font-body);
      font-weight: 600;
      font-size: 0.88rem;
      letter-spacing: 0.04em;
      cursor: pointer;
      transition: background var(--transition), color var(--transition), box-shadow var(--transition);
    }
    .btn-login:hover {
      background: var(--blue);
      color: #fff;
      box-shadow: 0 0 16px rgba(5,151,242,0.4);
    }

    /* --- Avatar de usuario (activar cuando haya sesión / BD) ---
         Elimina el .btn-login y usa esto cuando el usuario esté logueado:

         <div class="user-avatar" title="Mi perfil">
           <img src="URL_FOTO_PERFIL" alt="Perfil" />
           <!-- Si no hay foto: muestra las iniciales -->
         </div>

        .user-avatar {
          width: 38px; height: 38px;
          border-radius: 50%;
          border: 2px solid var(--blue);
          overflow: hidden;
          cursor: pointer;
          transition: box-shadow var(--transition);
        }
        .user-avatar:hover { box-shadow: 0 0 14px rgba(5,151,242,0.5); }
        .user-avatar img { width:100%; height:100%; object-fit:cover; }
    */

    /* Botón carrito */
    .btn-cart {
      position: relative;
      background: var(--bg3);
      border: 1.5px solid var(--border);
      color: var(--text);
      border-radius: var(--radius);
      width: 42px; height: 42px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem;
      cursor: pointer;
      transition: border-color var(--transition), color var(--transition);
    }
    .btn-cart:hover { border-color: var(--blue); color: var(--blue); }

    .cart-badge {
      position: absolute;
      top: -6px; right: -6px;
      background: var(--red);
      color: #fff;
      font-size: 0.65rem;
      font-weight: 700;
      width: 18px; height: 18px;
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-family: var(--font-display);
    }

    /* ============================================================
       3. MENÚ DE NAVEGACIÓN PRINCIPAL
       ============================================================ */
    #main-nav {
      background: var(--bg2);
      border-bottom: 2px solid rgba(5,151,242,0.12);
      position: sticky;
      top: 68px;
      z-index: 900;
    }

    .nav-inner {
      max-width: 1400px;
      margin: 0 auto;
      padding: 0 24px;
      display: flex;
      align-items: stretch;
      gap: 0;
    }

    /* Cada item del menú */
    .nav-item {
      position: relative;
      display: flex;
      align-items: center;
    }

    .nav-link {
      display: flex;
      align-items: center;
      gap: 6px;
      padding: 14px 18px;
      font-family: var(--font-body);
      font-weight: 600;
      font-size: 0.9rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      color: var(--muted);
      cursor: pointer;
      white-space: nowrap;
      transition: color var(--transition);
      border-bottom: 2px solid transparent;
      margin-bottom: -2px;
    }

    .nav-link:hover,
    .nav-item.active > .nav-link {
      color: var(--blue);
      border-bottom-color: var(--blue);
    }

    .nav-link .arrow {
      font-size: 0.6rem;
      transition: transform var(--transition);
    }

    .nav-item:hover > .nav-link .arrow { transform: rotate(180deg); }

    /* --- Dropdown genérico --- */
    .dropdown {
      display: none;
      position: absolute;
      top: calc(100% + 2px);
      left: 0;
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      min-width: 220px;
      padding: 10px 0;
      box-shadow: 0 16px 40px rgba(0,0,0,0.6);
      z-index: 1000;
      animation: fadeDown 0.18s ease;
    }

    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-8px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    .nav-item:hover > .dropdown { display: block; }

    .dropdown-link {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 10px 20px;
      font-size: 0.88rem;
      font-weight: 500;
      color: var(--muted);
      transition: color var(--transition), background var(--transition), padding-left var(--transition);
    }

    .dropdown-link:hover {
      color: var(--text);
      background: var(--bg3);
      padding-left: 26px;
    }

    .dropdown-link .ico { font-size: 1rem; }

    /* Separador dentro del dropdown */
    .dropdown-sep {
      height: 1px;
      background: var(--border);
      margin: 6px 16px;
    }

    /* Sub-encabezado dentro del dropdown (ej: "Videojuegos") */
    .dropdown-header {
      padding: 8px 20px 4px;
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--blue);
      font-family: var(--font-display);
    }

    /* Dropdown de segundo nivel (sub-dropdown) */
    .sub-dropdown {
      position: relative;
    }

    .sub-dropdown > .dropdown-link::after {
      content: '›';
      margin-left: auto;
      opacity: 0.5;
    }

    .sub-dropdown > .dropdown {
      left: 100%;
      top: -10px;
    }

    .sub-dropdown:hover > .dropdown { display: block; }

    /* ============================================================
       4. CARRUSEL DE IMÁGENES (Hero / Noticias de tienda / consolas)
       ============================================================ */
    #carousel {
      position: relative;
      overflow: hidden;
      height: 420px;      /* Ajusta la altura según necesites */
      background: var(--bg);
    }

    .carousel-track {
      display: flex;
      height: 100%;
      transition: transform 0.55s cubic-bezier(0.77,0,0.18,1);
    }

    /* Cada slide del carrusel
       *** IMÁGENES DEL CARRUSEL ***
       En cada .carousel-slide, añade:
         - background-image: url('URL_O_RUTA_IMAGEN_SLIDE_N');
         - O incluye un <img> dentro del slide
       Actualmente muestran un placeholder degradado con texto indicativo.
    */
    .carousel-slide {
      flex-shrink: 0;
      width: 100%;
      height: 100%;
      position: relative;
      display: flex;
      align-items: flex-end;
    }

    /* Placeholder visual por slide (remover cuando se usen imágenes reales) */
    .carousel-slide:nth-child(1) { background: linear-gradient(135deg, #0a0a1a 0%, #0d1f3c 50%, #091428 100%); }
    .carousel-slide:nth-child(2) { background: linear-gradient(135deg, #0a0a1a 0%, #1a0505 50%, #2d0a0a 100%); }
    .carousel-slide:nth-child(3) { background: linear-gradient(135deg, #0a0a1a 0%, #051a0d 50%, #041208 100%); }
    .carousel-slide:nth-child(4) { background: linear-gradient(135deg, #0a0a1a 0%, #0a0a0a 50%, #1a1a2d 100%); }

    /* Zona de imagen principal del slide
       Reemplazar .slide-img-placeholder por <img src="..." /> o <video> */
    .slide-img-placeholder {
      position: absolute;
      inset: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      color: rgba(255,255,255,0.05);
      font-size: 6rem;
    }

    /* Overlay degradado inferior para legibilidad del texto */
    .slide-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, rgba(10,10,15,0.95) 0%, rgba(10,10,15,0.3) 50%, transparent 100%);
    }

    /* Contenido textual del slide */
    .slide-content {
      position: relative;
      z-index: 2;
      padding: 36px 48px;
      max-width: 700px;
    }

    .slide-tag {
      display: inline-block;
      background: var(--blue);
      color: #fff;
      font-family: var(--font-display);
      font-size: 0.65rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      padding: 4px 12px;
      border-radius: 3px;
      margin-bottom: 12px;
    }

    .slide-title {
      font-family: var(--font-display);
      font-size: 2.2rem;
      font-weight: 700;
      line-height: 1.15;
      margin-bottom: 10px;
      color: #fff;
    }

    .slide-desc {
      font-size: 0.95rem;
      color: rgba(255,255,255,0.7);
      margin-bottom: 20px;
      max-width: 520px;
    }

    .slide-cta {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: var(--blue);
      color: #fff;
      border: none;
      border-radius: var(--radius);
      padding: 10px 24px;
      font-family: var(--font-body);
      font-weight: 700;
      font-size: 0.9rem;
      cursor: pointer;
      transition: box-shadow var(--transition), transform var(--transition);
    }
    .slide-cta:hover {
      box-shadow: 0 0 20px rgba(5,151,242,0.5);
      transform: translateY(-2px);
    }

    /* Controles del carrusel */
    .carousel-btn {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background: rgba(10,10,15,0.7);
      border: 1px solid var(--border);
      color: var(--text);
      width: 44px; height: 44px;
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: 1.1rem;
      cursor: pointer;
      z-index: 10;
      transition: background var(--transition), border-color var(--transition);
    }
    .carousel-btn:hover { background: var(--blue); border-color: var(--blue); }

    #carousel-prev { left: 16px; }
    #carousel-next { right: 16px; }

    /* Dots del carrusel */
    .carousel-dots {
      position: absolute;
      bottom: 16px; left: 50%;
      transform: translateX(-50%);
      display: flex; gap: 8px;
      z-index: 10;
    }

    .dot {
      width: 8px; height: 8px;
      border-radius: 50%;
      background: rgba(255,255,255,0.3);
      cursor: pointer;
      transition: background var(--transition), width var(--transition);
    }
    .dot.active {
      background: var(--blue);
      width: 24px;
      border-radius: 4px;
    }

    /* ============================================================
       5. SECCIÓN DE CONTENIDO PRINCIPAL (cambia según el menú)
       ============================================================ */
    #main-content {
      max-width: 1400px;
      margin: 0 auto;
      padding: 48px 24px 80px;
    }

    /* --- Cabecera de sección --- */
    .section-header {
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      margin-bottom: 32px;
      padding-bottom: 16px;
      border-bottom: 1px solid var(--border);
    }

    .section-title {
      font-family: var(--font-display);
      font-size: 1.6rem;
      font-weight: 700;
      letter-spacing: 0.04em;
      color: var(--text);
    }

    .section-title span {
      color: var(--blue);
    }

    .section-subtitle {
      font-size: 0.88rem;
      color: var(--muted);
      margin-top: 4px;
    }

    .btn-ver-todos {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--muted);
      border-radius: var(--radius);
      padding: 8px 18px;
      font-family: var(--font-body);
      font-size: 0.83rem;
      font-weight: 600;
      letter-spacing: 0.05em;
      cursor: pointer;
      transition: border-color var(--transition), color var(--transition);
    }
    .btn-ver-todos:hover { border-color: var(--blue); color: var(--blue); }

    /* ============================================================
       5A. GRID DE PRODUCTOS (tarjetas de videojuegos/consolas)
       ============================================================ */
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      gap: 20px;
    }

    /* Tarjeta de producto */
    .product-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      overflow: hidden;
      cursor: pointer;
      transition: transform var(--transition), border-color var(--transition), box-shadow var(--transition);
      position: relative;
    }

    .product-card:hover {
      transform: translateY(-4px);
      border-color: rgba(5,151,242,0.4);
      box-shadow: 0 12px 32px rgba(0,0,0,0.5);
    }

    /* *** IMAGEN DEL PRODUCTO ***
       Reemplaza .product-img-placeholder por:
       <img src="URL_O_RUTA_IMAGEN" alt="Nombre del juego" class="product-img" />
       y agrega: .product-img { width:100%; height:100%; object-fit:cover; }
    */
    .product-img-placeholder {
      width: 100%;
      height: 160px;
      background: var(--bg3);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3rem;
      color: rgba(255,255,255,0.08);
      position: relative;
      overflow: hidden;
    }

    /* Badges sobre la imagen */
    .product-badges {
      position: absolute;
      top: 10px; left: 10px;
      display: flex; flex-direction: column; gap: 5px;
    }

    .badge {
      font-family: var(--font-display);
      font-size: 0.6rem;
      font-weight: 700;
      letter-spacing: 0.08em;
      padding: 3px 8px;
      border-radius: 3px;
      text-transform: uppercase;
    }

    .badge-nuevo    { background: var(--green); color: #fff; }
    .badge-oferta   { background: var(--red);   color: #fff; }
    .badge-preventa { background: var(--blue);  color: #fff; }
    .badge-digital  { background: var(--deepred); color: #fff; }
    .badge-fisico   { background: #2a2a3a; color: var(--muted); border: 1px solid var(--border); }

    /* Contenido textual de la tarjeta */
    .product-body {
      padding: 14px 16px 16px;
    }

    .product-console {
      font-size: 0.72rem;
      color: var(--blue);
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .product-name {
      font-family: var(--font-body);
      font-weight: 700;
      font-size: 0.97rem;
      line-height: 1.3;
      margin-bottom: 10px;
      color: var(--text);
    }

    /* Info rápida del juego (año, modo, etc.) */
    .product-meta {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-bottom: 12px;
    }

    .meta-tag {
      font-size: 0.7rem;
      padding: 2px 8px;
      border-radius: 30px;
      background: var(--bg3);
      color: var(--muted);
      border: 1px solid var(--border);
    }

    .product-price-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
    }

    .product-price {
      font-family: var(--font-display);
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--green);
    }

    .product-price-old {
      font-size: 0.8rem;
      color: var(--muted);
      text-decoration: line-through;
      margin-left: 4px;
    }

    .btn-add-cart {
      background: var(--blue);
      border: none;
      border-radius: var(--radius);
      color: #fff;
      width: 34px; height: 34px;
      display: flex; align-items: center; justify-content: center;
      font-size: 1rem;
      cursor: pointer;
      flex-shrink: 0;
      transition: box-shadow var(--transition), transform var(--transition);
    }
    .btn-add-cart:hover {
      box-shadow: 0 0 14px rgba(5,151,242,0.5);
      transform: scale(1.08);
    }

    /* ============================================================
       5B. VISTA DE DETALLE DE VIDEOJUEGO
       ============================================================ */
    #game-detail {
      display: none; /* Se activa vía JS cuando se selecciona un juego */
    }

    .game-detail-inner {
      display: grid;
      grid-template-columns: 1fr 1.5fr;
      gap: 40px;
      align-items: start;
    }

    /* Columna izquierda: portada + trailer */
    .game-cover {
      border-radius: var(--radius-lg);
      overflow: hidden;
      border: 1px solid var(--border);
    }

    /* *** PORTADA DEL JUEGO ***
       Reemplaza .game-cover-placeholder por:
       <img src="URL_PORTADA" alt="Portada del juego" style="width:100%;display:block;" />
    */
    .game-cover-placeholder {
      width: 100%;
      aspect-ratio: 3/4;
      background: var(--bg3);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 5rem;
      color: rgba(255,255,255,0.06);
    }

    /* *** TRAILER DEL JUEGO ***
       Reemplaza .trailer-placeholder por:
       <div class="trailer-wrapper">
         <iframe
           src="https://www.youtube.com/embed/VIDEO_ID"
           title="Trailer del juego"
           frameborder="0"
           allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
           allowfullscreen
           style="width:100%;aspect-ratio:16/9;border-radius:8px;margin-top:12px;"
         ></iframe>
       </div>
    */
    .trailer-placeholder {
      margin-top: 12px;
      aspect-ratio: 16/9;
      background: var(--bg3);
      border-radius: var(--radius);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.5rem;
      color: rgba(255,255,255,0.12);
      border: 1px solid var(--border);
      cursor: pointer;
      transition: border-color var(--transition);
    }
    .trailer-placeholder:hover { border-color: var(--red); }

    /* Columna derecha: info completa del juego */
    .game-info-title {
      font-family: var(--font-display);
      font-size: 2rem;
      font-weight: 700;
      margin-bottom: 8px;
    }

    .game-info-console {
      color: var(--blue);
      font-weight: 600;
      font-size: 0.9rem;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      margin-bottom: 20px;
    }

    /* Tabla de especificaciones del juego */
    .game-specs {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-bottom: 24px;
    }

    .spec-item {
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 12px 14px;
    }

    .spec-label {
      font-size: 0.7rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.08em;
      font-weight: 600;
      margin-bottom: 3px;
    }

    .spec-value {
      font-weight: 700;
      font-size: 0.95rem;
    }

    .spec-value.active  { color: var(--green); }
    .spec-value.inactive{ color: var(--red);   }

    .game-desc {
      font-size: 0.92rem;
      color: rgba(232,232,240,0.8);
      line-height: 1.7;
      margin-bottom: 28px;
    }

    /* Bloque de precio y compra */
    .game-purchase {
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 20px 24px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      flex-wrap: wrap;
    }

    .game-price {
      font-family: var(--font-display);
      font-size: 1.8rem;
      font-weight: 700;
      color: var(--green);
    }

    .game-price-note {
      font-size: 0.78rem;
      color: var(--muted);
      margin-top: 2px;
    }

    .btn-comprar {
      background: linear-gradient(90deg, var(--green), #05c97e);
      border: none;
      border-radius: var(--radius);
      color: #fff;
      padding: 13px 32px;
      font-family: var(--font-body);
      font-weight: 700;
      font-size: 1rem;
      letter-spacing: 0.05em;
      cursor: pointer;
      transition: box-shadow var(--transition), transform var(--transition);
    }
    .btn-comprar:hover {
      box-shadow: 0 0 20px rgba(3,166,106,0.5);
      transform: translateY(-2px);
    }

    .btn-favorito {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--muted);
      border-radius: var(--radius);
      padding: 13px 16px;
      cursor: pointer;
      font-size: 1.1rem;
      transition: color var(--transition), border-color var(--transition);
    }
    .btn-favorito:hover { color: var(--red); border-color: var(--red); }

    /* ============================================================
       5C. SECCIÓN CONSOLAS (grilla visual)
       ============================================================ */
    .consoles-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 20px;
    }

    .console-card {
      background: var(--bg2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      overflow: hidden;
      cursor: pointer;
      transition: transform var(--transition), border-color var(--transition);
      display: flex;
      flex-direction: column;
    }
    .console-card:hover {
      transform: translateY(-4px);
      border-color: rgba(5,151,242,0.4);
    }

    /* *** IMAGEN DE LA CONSOLA ***
       Reemplaza .console-img-placeholder por:
       <img src="URL_IMAGEN_CONSOLA" alt="Nombre consola" class="console-img" />
       y agrega: .console-img { width:100%; height:100%; object-fit:cover; }
    */
    .console-img-placeholder {
      width: 100%;
      height: 180px;
      background: var(--bg3);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 4rem;
      color: rgba(255,255,255,0.07);
    }

    .console-body {
      padding: 16px 18px 20px;
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .console-brand {
      font-size: 0.72rem;
      color: var(--blue);
      font-weight: 600;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-bottom: 4px;
    }

    .console-name {
      font-family: var(--font-display);
      font-weight: 700;
      font-size: 1.1rem;
      margin-bottom: 8px;
    }

    .console-desc {
      font-size: 0.85rem;
      color: var(--muted);
      flex: 1;
      margin-bottom: 16px;
    }

    .console-price {
      font-family: var(--font-display);
      font-size: 1.2rem;
      font-weight: 700;
      color: var(--green);
    }

    /* ============================================================
       5D. SECCIÓN ACCESORIOS
       ============================================================ */
    /* Usa el mismo .products-grid y .product-card con categoría "Accesorio" */

    /* ============================================================
       5E. SECCIÓN CITAS (Agendar)
       ============================================================ */
    #section-citas .citas-form-wrap {
      max-width: 640px;
      margin: 0 auto;
    }

    .form-group {
      margin-bottom: 20px;
    }

    .form-label {
      display: block;
      font-size: 0.83rem;
      font-weight: 600;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 7px;
    }

    .form-input,
    .form-select,
    .form-textarea {
      width: 100%;
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 11px 16px;
      color: var(--text);
      font-family: var(--font-body);
      font-size: 0.92rem;
      outline: none;
      transition: border-color var(--transition), box-shadow var(--transition);
    }
    .form-input:focus,
    .form-select:focus,
    .form-textarea:focus {
      border-color: var(--blue);
      box-shadow: 0 0 10px rgba(5,151,242,0.2);
    }

    .form-textarea { min-height: 100px; resize: vertical; }

    .form-select option { background: var(--bg2); }

    .btn-agendar {
      width: 100%;
      background: linear-gradient(90deg, var(--blue), #06c0ff);
      border: none;
      border-radius: var(--radius);
      color: #fff;
      padding: 14px;
      font-family: var(--font-body);
      font-weight: 700;
      font-size: 1rem;
      letter-spacing: 0.06em;
      cursor: pointer;
      transition: box-shadow var(--transition);
    }
    .btn-agendar:hover { box-shadow: 0 0 20px rgba(5,151,242,0.4); }

    /* ============================================================
       5F. SECCIÓN NOSOTROS
       ============================================================ */
    #section-nosotros .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 40px;
      align-items: center;
    }

    /* *** IMAGEN DE "NOSOTROS" / LOCAL ***
       Reemplaza .about-img-placeholder por:
       <img src="URL_FOTO_TIENDA" alt="Tienda PixelVault" style="width:100%;border-radius:12px;" />
    */
    .about-img-placeholder {
      width: 100%;
      aspect-ratio: 4/3;
      background: var(--bg3);
      border-radius: var(--radius-lg);
      border: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 5rem;
      color: rgba(255,255,255,0.06);
    }

    .about-text h2 {
      font-family: var(--font-display);
      font-size: 1.8rem;
      font-weight: 700;
      margin-bottom: 16px;
      line-height: 1.2;
    }

    .about-text p {
      color: rgba(232,232,240,0.75);
      font-size: 0.95rem;
      line-height: 1.8;
      margin-bottom: 20px;
    }

    .about-stats {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-top: 28px;
    }

    .stat-box {
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 16px;
      text-align: center;
    }

    .stat-number {
      font-family: var(--font-display);
      font-size: 1.6rem;
      font-weight: 700;
      color: var(--blue);
    }

    .stat-label {
      font-size: 0.78rem;
      color: var(--muted);
      margin-top: 4px;
    }

    /* ============================================================
       FILTROS DE CATEGORÍA (para las secciones de juegos/accesorios)
       ============================================================ */
    .filters-bar {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 28px;
    }

    .filter-btn {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--muted);
      border-radius: 30px;
      padding: 7px 16px;
      font-family: var(--font-body);
      font-size: 0.82rem;
      font-weight: 600;
      cursor: pointer;
      transition: all var(--transition);
    }

    .filter-btn:hover,
    .filter-btn.active {
      background: var(--blue);
      border-color: var(--blue);
      color: #fff;
    }

    /* ============================================================
       FOOTER
       ============================================================ */
    #footer {
      background: var(--bg2);
      border-top: 1px solid var(--border);
      padding: 48px 24px 24px;
    }

    .footer-inner {
      max-width: 1400px;
      margin: 0 auto;
    }

    .footer-grid {
      display: grid;
      grid-template-columns: 2fr 1fr 1fr 1fr;
      gap: 40px;
      margin-bottom: 40px;
    }

    .footer-brand .logo-name { font-size: 1.5rem; margin-bottom: 12px; display: block; }

    .footer-brand p {
      font-size: 0.88rem;
      color: var(--muted);
      line-height: 1.7;
      margin-bottom: 20px;
    }

    .social-links {
      display: flex;
      gap: 10px;
    }

    .social-btn {
      width: 36px; height: 36px;
      background: var(--bg3);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      display: flex; align-items: center; justify-content: center;
      font-size: 0.95rem;
      cursor: pointer;
      transition: border-color var(--transition), color var(--transition);
    }
    .social-btn:hover { border-color: var(--blue); color: var(--blue); }

    .footer-col h4 {
      font-family: var(--font-display);
      font-size: 0.75rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--blue);
      margin-bottom: 16px;
    }

    .footer-col ul li {
      margin-bottom: 10px;
    }

    .footer-col ul li a {
      font-size: 0.88rem;
      color: var(--muted);
      transition: color var(--transition);
    }
    .footer-col ul li a:hover { color: var(--text); }

    .footer-bottom {
      border-top: 1px solid var(--border);
      padding-top: 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .footer-bottom p {
      font-size: 0.8rem;
      color: var(--muted);
    }

    /* ============================================================
       SECCIONES – Lógica de visibilidad (JS las controla)
       ============================================================ */
    .page-section { display: none; }
    .page-section.visible { display: block; }

    /* ============================================================
       UTILIDADES
       ============================================================ */
    .glow-blue { text-shadow: 0 0 20px rgba(5,151,242,0.5); }
    .glow-green { text-shadow: 0 0 20px rgba(3,166,106,0.5); }

    /* Línea decorativa con color de acento */
    .accent-line {
      width: 48px; height: 3px;
      background: var(--blue);
      border-radius: 2px;
      margin-bottom: 20px;
    }

    /* ============================================================
       RESPONSIVE (básico)
       ============================================================ */
    @media (max-width: 1024px) {
      .footer-grid { grid-template-columns: 1fr 1fr; }
      .game-detail-inner { grid-template-columns: 1fr; }
      .about-grid { grid-template-columns: 1fr; }
    }

    @media (max-width: 768px) {
      .logo-tagline { display: none; }
      .search-bar { display: none; } /* Mostrar como toggle en móvil */
      .nav-inner { overflow-x: auto; padding: 0 12px; }
      .nav-link { padding: 12px 12px; font-size: 0.8rem; }
      #carousel { height: 280px; }
      .slide-title { font-size: 1.4rem; }
      .slide-content { padding: 20px 24px; }
      .products-grid { grid-template-columns: repeat(auto-fill, minmax(160px, 1fr)); }
      .footer-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>

<body>

  <!-- ============================================================
       1. BANNER SUPERIOR – Noticias y avisos importantes
       Para cambiar los mensajes edita los <span> dentro de .banner-ticker
       El ticker se duplica para lograr el efecto de loop infinito
       ============================================================ -->
  <div id="top-banner">
    <div class="banner-ticker">
      <!-- Primera copia del contenido del banner -->
      <span>🎮 Nueva llegada: Xbox Series X edición limitada – ¡Pocas unidades!</span>
      <span>🛍️ Envíos gratis en compras mayores a $999 MXN</span>
      <span>🎯 Preventa disponible: [NOMBRE DEL JUEGO] – Regístrate aquí</span>
      <span>🕹️ Citas disponibles – Agenda tu visita a la tienda</span>
      <span>⚡ Oferta del día: [DESCRIPCIÓN DE OFERTA] – Válido hasta [FECHA]</span>
      <!-- Segunda copia (necesaria para el efecto ticker continuo) -->
      <span>🎮 Nueva llegada: Xbox Series X edición limitada – ¡Pocas unidades!</span>
      <span>🛍️ Envíos gratis en compras mayores a $999 MXN</span>
      <span>🎯 Preventa disponible: [NOMBRE DEL JUEGO] – Regístrate aquí</span>
      <span>🕹️ Citas disponibles – Agenda tu visita a la tienda</span>
      <span>⚡ Oferta del día: [DESCRIPCIÓN DE OFERTA] – Válido hasta [FECHA]</span>
    </div>
    <button id="banner-close" title="Cerrar aviso">✕</button>
  </div>

  <!-- ============================================================
       2. HEADER – Logo + Búsqueda + Login/Registro + Carrito
       ============================================================ -->
  <header id="header">
    <div class="header-inner">

      <!-- Logo y nombre -->
      <div class="logo-area" onclick="showSection('inicio')">

  <div class="logo-icon">
    <img src="file:///C:/Users/Julian%20Mendoza/Downloads/fgs.png"
         alt="Logo"
         style="height:100%; width:100%; object-fit:contain;">
  </div>

  <div>
    <span class="logo-name">Fussion Games</span>
    <span class="logo-tagline">Store</span>
  </div>

</div>

      <!-- Barra de búsqueda central -->
      <div class="search-bar">
        <input type="text" placeholder="Buscar juegos, consolas, accesorios…" id="search-input" />
        <button>🔍</button>
      </div>

      <!-- Acciones del header -->
      <div class="header-actions">

        <!-- Botón de login/registro
             CUANDO HAYA BD: reemplazar por círculo de avatar (ver comentario en CSS .user-avatar)
             También se puede usar un dropdown de perfil aquí -->
        <button class="btn-login" onclick="showSection('login')">
          👤 Iniciar sesión
        </button>

        <!-- Carrito de compras
             El badge "3" debe actualizarse dinámicamente con JS cuando haya lógica de carrito -->
        <button class="btn-cart" onclick="showSection('carrito')" title="Carrito de compras">
          🛒
          <span class="cart-badge" id="cart-count">3</span>
        </button>

      </div>
    </div>
  </header>

  <!-- ============================================================
       3. MENÚ DE NAVEGACIÓN PRINCIPAL
       Estructura: Inicio / Consolas▾ / Juegos▾ / Accesorios / Citas / Nosotros
       Los dropdowns de Consolas y Juegos tienen las mismas plataformas
       ============================================================ -->
  <nav id="main-nav">
    <ul class="nav-inner">

      <!-- Inicio -->
      <li class="nav-item active">
        <a class="nav-link" onclick="showSection('inicio')">Inicio</a>
      </li>

      <!-- ─── CONSOLAS ──────────────────────────────────────────── -->
      <li class="nav-item">
        <a class="nav-link">
          Consolas <span class="arrow">▾</span>
        </a>
        <ul class="dropdown">

          <!-- Nintendo -->
          <li>
            <a class="dropdown-link" onclick="showSection('consolas-nintendo')">
              <span class="ico">🍄</span> Nintendo
            </a>
          </li>

          <!-- Xbox -->
          <li>
            <a class="dropdown-link" onclick="showSection('consolas-xbox')">
              <span class="ico">🟩</span> Xbox
            </a>
          </li>

          <!-- PlayStation -->
          <li>
            <a class="dropdown-link" onclick="showSection('consolas-playstation')">
              <span class="ico">🔵</span> PlayStation
            </a>
          </li>

          <!-- Retro -->
          <li>
            <a class="dropdown-link" onclick="showSection('consolas-retro')">
              <span class="ico">👾</span> Retro
            </a>
          </li>

          <li><div class="dropdown-sep"></div></li>

          <!-- Categorías de consolas -->
          <li><div class="dropdown-header">Categorías</div></li>

          <li>
            <a class="dropdown-link" onclick="showSection('consolas-solo-venta')">
              <span class="ico">📦</span> Solo venta de consolas
            </a>
          </li>
          <li>
            <a class="dropdown-link" onclick="showSection('consolas-accesorios')">
              <span class="ico">🎮</span> Accesorios
            </a>
          </li>

        </ul>
      </li>

      <!-- ─── JUEGOS ─────────────────────────────────────────────── -->
      <li class="nav-item">
        <a class="nav-link">
          Juegos <span class="arrow">▾</span>
        </a>
        <ul class="dropdown">

          <!-- Plataformas (sub-dropdown con categorías de juegos) -->

          <!-- Nintendo + categorías -->
          <li class="sub-dropdown">
            <a class="dropdown-link">
              <span class="ico">🍄</span> Nintendo
            </a>
            <ul class="dropdown">
              <li><div class="dropdown-header">Formato</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-nintendo-fisicos')">🕹️ Físicos</a></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-nintendo-digitales')">💾 Digitales</a></li>
              <li><div class="dropdown-sep"></div></li>
              <li><div class="dropdown-header">Tipo</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-nintendo-accesorios')">🎮 Accesorios</a></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-nintendo-preventa')">⏳ Preventas / Bajo pedido</a></li>
            </ul>
          </li>

          <!-- Xbox + categorías -->
          <li class="sub-dropdown">
            <a class="dropdown-link">
              <span class="ico">🟩</span> Xbox
            </a>
            <ul class="dropdown">
              <li><div class="dropdown-header">Formato</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-xbox-fisicos')">🕹️ Físicos</a></li>
              <!-- Digitales Solo 360 aplica a Xbox 360 específicamente -->
              <li><a class="dropdown-link" onclick="showSection('juegos-xbox-digitales')">💾 Digitales (Solo 360)</a></li>
              <li><div class="dropdown-sep"></div></li>
              <li><div class="dropdown-header">Tipo</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-xbox-accesorios')">🎮 Accesorios</a></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-xbox-preventa')">⏳ Preventas / Bajo pedido</a></li>
            </ul>
          </li>

          <!-- PlayStation + categorías -->
          <li class="sub-dropdown">
            <a class="dropdown-link">
              <span class="ico">🔵</span> PlayStation
            </a>
            <ul class="dropdown">
              <li><div class="dropdown-header">Formato</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-ps-fisicos')">🕹️ Físicos</a></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-ps-digitales')">💾 Digitales</a></li>
              <li><div class="dropdown-sep"></div></li>
              <li><div class="dropdown-header">Tipo</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-ps-accesorios')">🎮 Accesorios</a></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-ps-preventa')">⏳ Preventas / Bajo pedido</a></li>
            </ul>
          </li>

          <!-- Retro + categorías -->
          <li class="sub-dropdown">
            <a class="dropdown-link">
              <span class="ico">👾</span> Retro
            </a>
            <ul class="dropdown">
              <li><div class="dropdown-header">Formato</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-retro-fisicos')">🕹️ Físicos</a></li>
              <li><div class="dropdown-sep"></div></li>
              <li><div class="dropdown-header">Tipo</div></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-retro-accesorios')">🎮 Accesorios</a></li>
              <li><a class="dropdown-link" onclick="showSection('juegos-retro-preventa')">⏳ Preventas / Bajo pedido</a></li>
            </ul>
          </li>

          <li><div class="dropdown-sep"></div></li>
          <li><div class="dropdown-header">Especiales</div></li>
          <!-- Todas las consolas menos PC (ventas cruzadas) -->
          <li>
            <a class="dropdown-link" onclick="showSection('juegos-todas-consolas')">
              <span class="ico">🌐</span> Todas las consolas (menos PC)
            </a>
          </li>

        </ul>
      </li>

      <!-- Accesorios (general) -->
      <li class="nav-item">
        <a class="nav-link" onclick="showSection('accesorios')">Accesorios</a>
      </li>

      <!-- Citas -->
      <li class="nav-item">
        <a class="nav-link" onclick="showSection('citas')">Citas</a>
      </li>

      <!-- Nosotros -->
      <li class="nav-item">
        <a class="nav-link" onclick="showSection('nosotros')">Nosotros</a>
      </li>

    </ul>
  </nav>

  <!-- ============================================================
       4. CARRUSEL DE IMÁGENES – Noticias de tienda / consolas / juegos
       Para agregar slides: duplica un .carousel-slide y edita su contenido.
       Las imágenes se agregan en .carousel-slide como background-image
       o colocando un <img> dentro de .slide-img-placeholder
       ============================================================ -->
  <section id="carousel">

    <div class="carousel-track" id="carousel-track">

      <!-- ─── SLIDE 1: Noticia de tienda ────────────────────────── -->
      <div class="carousel-slide">
        <!-- *** IMAGEN SLIDE 1 ***
             Opción A (background): style="background-image:url('URL_IMAGEN_1');background-size:cover;background-position:center;"
             Opción B (tag img):    <img src="URL_IMAGEN_1" style="position:absolute;inset:0;width:100%;height:100%;object-fit:cover;" />
        -->
        <div class="slide-img-placeholder">🎮</div>
        <div class="slide-overlay"></div>
        <div class="slide-content">
          <span class="slide-tag">Novedad en tienda</span>
          <h2 class="slide-title">[TÍTULO NOTICIA O PRODUCTO DESTACADO]</h2>
          <p class="slide-desc">[Descripción breve de la noticia, oferta o producto. Ej: nueva consola, bundle especial, evento de la tienda.]</p>
          <button class="slide-cta">Ver más →</button>
        </div>
      </div>

      <!-- ─── SLIDE 2: Oferta / Consola destacada ───────────────── -->
      <div class="carousel-slide">
        <!-- *** IMAGEN SLIDE 2 *** -->
        <div class="slide-img-placeholder">🕹️</div>
        <div class="slide-overlay"></div>
        <div class="slide-content">
          <span class="slide-tag" style="background:var(--red);">Oferta especial</span>
          <h2 class="slide-title">[NOMBRE DE CONSOLA O JUEGO EN OFERTA]</h2>
          <p class="slide-desc">[Descripción de la oferta. Precio anterior y nuevo, fechas de vigencia, condiciones.]</p>
          <button class="slide-cta" style="background:var(--red);">¡Ver oferta! →</button>
        </div>
      </div>

      <!-- ─── SLIDE 3: Preventa / Lanzamiento próximo ───────────── -->
      <div class="carousel-slide">
        <!-- *** IMAGEN SLIDE 3 *** -->
        <div class="slide-img-placeholder">⚡</div>
        <div class="slide-overlay"></div>
        <div class="slide-content">
          <span class="slide-tag" style="background:var(--green);">Preventa abierta</span>
          <h2 class="slide-title">[NOMBRE DEL PRÓXIMO LANZAMIENTO]</h2>
          <p class="slide-desc">[Fecha de lanzamiento, plataformas disponibles, precio de preventa y beneficios por reservar.]</p>
          <button class="slide-cta" style="background:var(--green);">Reservar ahora →</button>
        </div>
      </div>

      <!-- ─── SLIDE 4: Evento de la tienda ─────────────────────── -->
      <div class="carousel-slide">
        <!-- *** IMAGEN SLIDE 4 *** -->
        <div class="slide-img-placeholder">🏆</div>
        <div class="slide-overlay"></div>
        <div class="slide-content">
          <span class="slide-tag" style="background:var(--deepred);">Evento</span>
          <h2 class="slide-title">[NOMBRE DEL EVENTO DE LA TIENDA]</h2>
          <p class="slide-desc">[Detalle del evento, fecha, hora, lugar y cómo participar. Torneos, inauguraciones, etc.]</p>
          <button class="slide-cta" onclick="showSection('citas')">¡Me apunto! →</button>
        </div>
      </div>

    </div><!-- /carousel-track -->

    <!-- Controles -->
    <button class="carousel-btn" id="carousel-prev">‹</button>
    <button class="carousel-btn" id="carousel-next">›</button>

    <!-- Dots de navegación -->
    <div class="carousel-dots" id="carousel-dots">
      <div class="dot active" onclick="goToSlide(0)"></div>
      <div class="dot" onclick="goToSlide(1)"></div>
      <div class="dot" onclick="goToSlide(2)"></div>
      <div class="dot" onclick="goToSlide(3)"></div>
    </div>

  </section>

  <!-- ============================================================
       5. CONTENIDO PRINCIPAL (cambia según la sección activa)
       Cada .page-section está oculta por defecto; JS la hace visible
       ============================================================ -->
  <main id="main-content">

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN: INICIO – Productos destacados y novedades
         ────────────────────────────────────────────────────────── -->
    <section id="section-inicio" class="page-section visible">

      <!-- Productos destacados -->
      <div class="section-header">
        <div>
          <h2 class="section-title">Productos <span>Destacados</span></h2>
          <p class="section-subtitle">Lo más popular de la semana en PixelVault</p>
        </div>
        <button class="btn-ver-todos" onclick="showSection('juegos-todas-consolas')">Ver todos →</button>
      </div>

      <!-- Filtros rápidos (en la página de inicio) -->
      <div class="filters-bar">
        <button class="filter-btn active">Todos</button>
        <button class="filter-btn">Nintendo</button>
        <button class="filter-btn">Xbox</button>
        <button class="filter-btn">PlayStation</button>
        <button class="filter-btn">Retro</button>
        <button class="filter-btn">Accesorios</button>
        <button class="filter-btn">Preventas</button>
      </div>

      <!-- Grid de productos
           *** Para agregar un juego real:
               1. Copia un .product-card completo
               2. Cambia el emoji de .product-img-placeholder por la imagen real
               3. Actualiza nombre, consola, año, precio y badges ***
      -->
      <div class="products-grid">

        <!-- Producto 1 -->
        <div class="product-card" onclick="showGameDetail('game-1')">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN JUEGO 1: <img src="URL_JUEGO_1" alt="Nombre" style="width:100%;height:100%;object-fit:cover;"> *** -->
            🎮
            <div class="product-badges">
              <span class="badge badge-nuevo">Nuevo</span>
              <span class="badge badge-fisico">Físico</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">Nintendo Switch</div>
            <div class="product-name">[Nombre del Juego 1]</div>
            <div class="product-meta">
              <span class="meta-tag">📅 [AÑO]</span>
              <span class="meta-tag">👥 Multi</span>
              <span class="meta-tag">🌐 Online ✓</span>
            </div>
            <div class="product-price-row">
              <div>
                <span class="product-price">$[PRECIO]</span>
              </div>
              <button class="btn-add-cart" title="Añadir al carrito">+</button>
            </div>
          </div>
        </div>

        <!-- Producto 2 -->
        <div class="product-card" onclick="showGameDetail('game-2')">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN JUEGO 2 *** -->
            🕹️
            <div class="product-badges">
              <span class="badge badge-oferta">Oferta</span>
              <span class="badge badge-fisico">Físico</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">PlayStation 5</div>
            <div class="product-name">[Nombre del Juego 2]</div>
            <div class="product-meta">
              <span class="meta-tag">📅 [AÑO]</span>
              <span class="meta-tag">👤 Single</span>
              <span class="meta-tag">🔄 Retrocompat.</span>
            </div>
            <div class="product-price-row">
              <div>
                <span class="product-price">$[PRECIO]</span>
                <span class="product-price-old">$[PRECIO ANTERIOR]</span>
              </div>
              <button class="btn-add-cart" title="Añadir al carrito">+</button>
            </div>
          </div>
        </div>

        <!-- Producto 3 -->
        <div class="product-card" onclick="showGameDetail('game-3')">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN JUEGO 3 *** -->
            🟩
            <div class="product-badges">
              <span class="badge badge-digital">Digital</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">Xbox 360 · Solo digital</div>
            <div class="product-name">[Nombre del Juego 3]</div>
            <div class="product-meta">
              <span class="meta-tag">📅 [AÑO]</span>
              <span class="meta-tag">👥 Multi</span>
            </div>
            <div class="product-price-row">
              <div>
                <span class="product-price">$[PRECIO]</span>
              </div>
              <button class="btn-add-cart" title="Añadir al carrito">+</button>
            </div>
          </div>
        </div>

        <!-- Producto 4 -->
        <div class="product-card" onclick="showGameDetail('game-4')">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN JUEGO 4 *** -->
            👾
            <div class="product-badges">
              <span class="badge badge-preventa">Preventa</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">Retro / SNES</div>
            <div class="product-name">[Nombre del Juego 4]</div>
            <div class="product-meta">
              <span class="meta-tag">📅 [AÑO]</span>
              <span class="meta-tag">👤 Single</span>
            </div>
            <div class="product-price-row">
              <div>
                <span class="product-price">A tratar</span>
              </div>
              <button class="btn-add-cart" title="Bajo pedido">📩</button>
            </div>
          </div>
        </div>

        <!-- Producto 5 -->
        <div class="product-card">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN JUEGO 5 *** -->
            🔵
            <div class="product-badges">
              <span class="badge badge-nuevo">Nuevo</span>
              <span class="badge badge-fisico">Físico</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">PlayStation 4</div>
            <div class="product-name">[Nombre del Juego 5]</div>
            <div class="product-meta">
              <span class="meta-tag">📅 [AÑO]</span>
              <span class="meta-tag">👥 Multi</span>
              <span class="meta-tag">🌐 Online ✓</span>
            </div>
            <div class="product-price-row">
              <div>
                <span class="product-price">$[PRECIO]</span>
              </div>
              <button class="btn-add-cart">+</button>
            </div>
          </div>
        </div>

        <!-- Producto 6 (Accesorio) -->
        <div class="product-card" onclick="showSection('accesorios')">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN ACCESORIO *** -->
            🎛️
            <div class="product-badges">
              <span class="badge badge-nuevo">Nuevo</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">Accesorio · Universal</div>
            <div class="product-name">[Nombre del Accesorio]</div>
            <div class="product-meta">
              <span class="meta-tag">🎮 Control</span>
              <span class="meta-tag">🔌 [Tipo]</span>
            </div>
            <div class="product-price-row">
              <div>
                <span class="product-price">$[PRECIO]</span>
              </div>
              <button class="btn-add-cart">+</button>
            </div>
          </div>
        </div>

      </div><!-- /products-grid -->

      <!-- Consolas destacadas -->
      <div class="section-header" style="margin-top:56px;">
        <div>
          <h2 class="section-title">Consolas <span>Disponibles</span></h2>
          <p class="section-subtitle">Stock actual en tienda</p>
        </div>
        <button class="btn-ver-todos" onclick="showSection('consolas-solo-venta')">Ver todas →</button>
      </div>

      <div class="consoles-grid">

        <!-- Consola 1 -->
        <div class="console-card" onclick="showSection('consolas-nintendo')">
          <div class="console-img-placeholder">
            <!-- *** IMAGEN CONSOLA NINTENDO ***
                 <img src="URL_IMAGEN_NINTENDO" alt="Nintendo Switch" style="width:100%;height:100%;object-fit:contain;padding:16px;" />
            -->
            🍄
          </div>
          <div class="console-body">
            <div class="console-brand">Nintendo</div>
            <div class="console-name">Switch / Switch OLED</div>
            <p class="console-desc">[Descripción breve. Stock, colores disponibles, bundle actual.]</p>
            <div class="console-price">$[PRECIO] MXN</div>
          </div>
        </div>

        <!-- Consola 2 -->
        <div class="console-card" onclick="showSection('consolas-xbox')">
          <div class="console-img-placeholder">
            <!-- *** IMAGEN CONSOLA XBOX *** -->
            🟩
          </div>
          <div class="console-body">
            <div class="console-brand">Microsoft</div>
            <div class="console-name">Xbox Series X / S</div>
            <p class="console-desc">[Descripción breve. Modelos disponibles, colores, capacidades.]</p>
            <div class="console-price">$[PRECIO] MXN</div>
          </div>
        </div>

        <!-- Consola 3 -->
        <div class="console-card" onclick="showSection('consolas-playstation')">
          <div class="console-img-placeholder">
            <!-- *** IMAGEN CONSOLA PS *** -->
            🔵
          </div>
          <div class="console-body">
            <div class="console-brand">Sony</div>
            <div class="console-name">PlayStation 5 / 4</div>
            <p class="console-desc">[Descripción breve. Versión disc/digital, stock, accesorios incluidos.]</p>
            <div class="console-price">$[PRECIO] MXN</div>
          </div>
        </div>

        <!-- Consola 4 -->
        <div class="console-card" onclick="showSection('consolas-retro')">
          <div class="console-img-placeholder">
            <!-- *** IMAGEN CONSOLA RETRO *** -->
            👾
          </div>
          <div class="console-body">
            <div class="console-brand">Retro</div>
            <div class="console-name">Colección Clásica</div>
            <p class="console-desc">[SNES, N64, Mega Drive, PS1, Xbox 360 y más. Consulta disponibilidad.]</p>
            <div class="console-price">Desde $[PRECIO] MXN</div>
          </div>
        </div>

      </div><!-- /consoles-grid -->

    </section><!-- /section-inicio -->

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN: DETALLE DE VIDEOJUEGO
         Se activa al hacer click en un producto
         Toda la info del juego se muestra aquí
         ────────────────────────────────────────────────────────── -->
    <section id="section-game-detail" class="page-section">

      <!-- Botón volver -->
      <button class="btn-ver-todos" onclick="goBack()" style="margin-bottom:24px;">
        ← Volver
      </button>

      <div class="game-detail-inner">

        <!-- Columna izquierda: portada y trailer -->
        <div>

          <!-- Portada del juego -->
          <div class="game-cover">
            <!-- *** PORTADA DEL JUEGO ***
                 Reemplaza el placeholder por:
                 <img src="URL_PORTADA_JUEGO" alt="Nombre del juego" style="width:100%;display:block;" />
            -->
            <div class="game-cover-placeholder">🎮</div>
          </div>

          <!-- Trailer del juego
               *** Para poner el trailer real, reemplaza .trailer-placeholder por un iframe de YouTube:
               <iframe
                 src="https://www.youtube.com/embed/[VIDEO_ID]"
                 title="Trailer"
                 frameborder="0"
                 allow="autoplay; encrypted-media"
                 allowfullscreen
                 style="width:100%;aspect-ratio:16/9;display:block;border-radius:8px;margin-top:12px;"
               ></iframe>
          -->
          <div class="trailer-placeholder" title="Trailer del juego">
            ▶ Trailer
          </div>

        </div>

        <!-- Columna derecha: toda la información del juego -->
        <div>

          <div class="game-info-console" id="detail-console">Nintendo Switch</div>
          <h1 class="game-info-title" id="detail-title">[NOMBRE DEL JUEGO]</h1>

          <!-- Especificaciones del juego (los valores se actualizan por JS / o se editan aquí) -->
          <div class="game-specs">

            <div class="spec-item">
              <div class="spec-label">📅 Año de lanzamiento</div>
              <div class="spec-value" id="detail-year">[AÑO]</div>
            </div>

            <div class="spec-item">
              <div class="spec-label">📡 Estado del juego</div>
              <!-- active = vigente / inactive = descontinuado -->
              <div class="spec-value active" id="detail-status">Vigente</div>
            </div>

            <div class="spec-item">
              <div class="spec-label">🎮 Modo de juego</div>
              <!-- Multijugador / Single Player / Ambos -->
              <div class="spec-value" id="detail-mode">Multijugador</div>
            </div>

            <div class="spec-item">
              <div class="spec-label">🌐 Servidores online</div>
              <!-- active si los servidores siguen abiertos -->
              <div class="spec-value active" id="detail-online">Abiertos ✓</div>
            </div>

            <div class="spec-item">
              <div class="spec-label">🔄 Retrocompatible</div>
              <div class="spec-value" id="detail-retro">Sí</div>
            </div>

            <div class="spec-item">
              <div class="spec-label">📦 Formato</div>
              <div class="spec-value" id="detail-format">Físico / Digital</div>
            </div>

          </div><!-- /game-specs -->

          <!-- Descripción del juego -->
          <p class="game-desc" id="detail-desc">
            [Aquí va la descripción completa del videojuego. Incluye género, historia, mecánicas principales,
            por qué es especial y qué tipo de jugador disfrutará de él. Puedes escribir 3-5 oraciones.]
          </p>

          <!-- Bloque de precio y compra -->
          <div class="game-purchase">
            <div>
              <div class="game-price" id="detail-price">$[PRECIO] MXN</div>
              <div class="game-price-note" id="detail-price-note">Precio en tienda · Sujeto a disponibilidad</div>
            </div>
            <div style="display:flex;gap:10px;">
              <button class="btn-favorito" title="Añadir a favoritos">♡</button>
              <button class="btn-comprar">Añadir al carrito 🛒</button>
            </div>
          </div>

        </div><!-- /columna derecha -->

      </div><!-- /game-detail-inner -->

    </section><!-- /section-game-detail -->

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN: ACCESORIOS (controles, cables, headsets, etc.)
         ────────────────────────────────────────────────────────── -->
    <section id="section-accesorios" class="page-section">

      <div class="section-header">
        <div>
          <h2 class="section-title">Acce<span>sorios</span></h2>
          <p class="section-subtitle">Controles, headsets, cables, bases de carga y más</p>
        </div>
      </div>

      <!-- Filtros por tipo de accesorio -->
      <div class="filters-bar">
        <button class="filter-btn active">Todos</button>
        <button class="filter-btn">🎮 Controles</button>
        <button class="filter-btn">🎧 Headsets</button>
        <button class="filter-btn">🔋 Bases de carga</button>
        <button class="filter-btn">📡 Adaptadores</button>
        <button class="filter-btn">🖥️ Cables / HDMI</button>
        <button class="filter-btn">🍄 Nintendo</button>
        <button class="filter-btn">🟩 Xbox</button>
        <button class="filter-btn">🔵 PlayStation</button>
        <button class="filter-btn">👾 Universal</button>
      </div>

      <div class="products-grid">

        <!-- Accesorio 1 -->
        <div class="product-card">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN ACCESORIO 1 *** -->
            🎮
            <div class="product-badges">
              <span class="badge badge-nuevo">Nuevo</span>
            </div>
          </div>
          <div class="product-body">
            <div class="product-console">Control · PlayStation</div>
            <div class="product-name">[Nombre del Accesorio 1]</div>
            <div class="product-meta">
              <span class="meta-tag">🔌 [Tipo conexión]</span>
              <span class="meta-tag">[Color]</span>
            </div>
            <div class="product-price-row">
              <span class="product-price">$[PRECIO]</span>
              <button class="btn-add-cart">+</button>
            </div>
          </div>
        </div>

        <!-- Accesorio 2 -->
        <div class="product-card">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN ACCESORIO 2 *** -->
            🎧
          </div>
          <div class="product-body">
            <div class="product-console">Headset · Universal</div>
            <div class="product-name">[Nombre del Accesorio 2]</div>
            <div class="product-meta">
              <span class="meta-tag">🔊 [Características]</span>
            </div>
            <div class="product-price-row">
              <span class="product-price">$[PRECIO]</span>
              <button class="btn-add-cart">+</button>
            </div>
          </div>
        </div>

        <!-- Más accesorios: duplicar las tarjetas anteriores -->

      </div>

    </section><!-- /section-accesorios -->

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN: CITAS – Agendar visita a la tienda
         ────────────────────────────────────────────────────────── -->
    <section id="section-citas" class="page-section">

      <div class="section-header">
        <div>
          <h2 class="section-title">Agenda tu <span>Cita</span></h2>
          <p class="section-subtitle">Visítanos y te asesoramos en persona</p>
        </div>
      </div>

      <div class="citas-form-wrap">

        <div class="accent-line"></div>

        <p style="color:var(--muted);margin-bottom:28px;font-size:0.93rem;">
          ¿Quieres venir a la tienda, probar una consola o resolver dudas?
          Agenda tu cita y te esperamos con todo listo.
        </p>

        <!-- Formulario de cita
             *** INTEGRACIÓN: Conectar con backend / servicio de reservas (Google Calendar, Calendly, etc.) ***
             action="" → URL del endpoint de tu backend
        -->
        <div id="citas-form">

          <div class="form-group">
            <label class="form-label" for="cita-nombre">Nombre completo</label>
            <input class="form-input" id="cita-nombre" type="text" placeholder="Tu nombre…" />
          </div>

          <div class="form-group">
            <label class="form-label" for="cita-tel">Teléfono / WhatsApp</label>
            <input class="form-input" id="cita-tel" type="tel" placeholder="+52 …" />
          </div>

          <div class="form-group">
            <label class="form-label" for="cita-fecha">Fecha preferida</label>
            <input class="form-input" id="cita-fecha" type="date" />
          </div>

          <div class="form-group">
            <label class="form-label" for="cita-hora">Horario preferido</label>
            <select class="form-select" id="cita-hora">
              <option value="">Selecciona un horario…</option>
              <option>10:00 – 11:00</option>
              <option>11:00 – 12:00</option>
              <option>12:00 – 13:00</option>
              <option>13:00 – 14:00</option>
              <option>15:00 – 16:00</option>
              <option>16:00 – 17:00</option>
              <option>17:00 – 18:00</option>
            </select>
          </div>

          <div class="form-group">
            <label class="form-label" for="cita-motivo">¿En qué te podemos ayudar?</label>
            <select class="form-select" id="cita-motivo">
              <option value="">Selecciona el motivo…</option>
              <option>Compra de consola</option>
              <option>Compra de videojuego</option>
              <option>Accesorios / controles</option>
              <option>Asesoría general</option>
              <option>Reparación / revisión</option>
              <option>Preventa / encargo especial</option>
              <option>Otro</option>
            </select>
          </div>

          <div class="form-group">
            <label class="form-label" for="cita-notas">Notas adicionales (opcional)</label>
            <textarea class="form-textarea" id="cita-notas" placeholder="¿Algo que debamos saber de antemano? Modelo que buscas, dudas específicas…"></textarea>
          </div>

          <button class="btn-agendar" onclick="submitCita()">
            📅 Confirmar cita
          </button>

        </div><!-- /citas-form -->

      </div><!-- /citas-form-wrap -->

    </section><!-- /section-citas -->

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN: NOSOTROS – Historia, equipo y contacto
         ────────────────────────────────────────────────────────── -->
    <section id="section-nosotros" class="page-section">

      <div class="section-header">
        <div>
          <h2 class="section-title">Nosotros</h2>
          <p class="section-subtitle">Conoce a la gente detrás de PixelVault</p>
        </div>
      </div>

      <div class="about-grid">

        <!-- Imagen del local / equipo -->
        <!-- *** IMAGEN DE LA TIENDA ***
             Reemplaza el placeholder por:
             <img src="URL_FOTO_TIENDA_O_EQUIPO" alt="Tienda PixelVault" style="width:100%;border-radius:12px;border:1px solid var(--border);" />
        -->
        <div class="about-img-placeholder">🏪</div>

        <!-- Texto informativo -->
        <div class="about-text">

          <div class="accent-line"></div>

          <h2>Tu rincón <span style="color:var(--blue);">gamer</span> de confianza</h2>

          <!-- *** Edita este texto con la historia real de tu tienda *** -->
          <p>
            [Párrafo 1: Cuándo nació la tienda, quiénes somos, qué nos motivó a abrir. Ej: "PixelVault nació en [AÑO] con la misión de llevar los mejores videojuegos, consolas y accesorios directamente a la comunidad gamer de [Ciudad/Estado]."]
          </p>

          <p>
            [Párrafo 2: Qué nos diferencia. Ej: "Somos apasionados de los videojuegos, conocemos cada plataforma y podemos asesorarte para encontrar exactamente lo que buscas, ya sea el último lanzamiento o una joya retro de los 90s."]
          </p>

          <p>
            [Párrafo 3: Servicios, ubicación, horarios. Ej: "Te atendemos en [DIRECCIÓN] de Lunes a Sábado de [HORARIO]. También aceptamos pedidos especiales y preventas bajo pedido."]
          </p>

          <!-- Stats de la tienda -->
          <div class="about-stats">
            <div class="stat-box">
              <div class="stat-number">[N]+</div>
              <div class="stat-label">Títulos disponibles</div>
            </div>
            <div class="stat-box">
              <div class="stat-number">[N]+</div>
              <div class="stat-label">Clientes satisfechos</div>
            </div>
            <div class="stat-box">
              <div class="stat-number">[N]</div>
              <div class="stat-label">Años de experiencia</div>
            </div>
          </div>

        </div><!-- /about-text -->

      </div><!-- /about-grid -->

      <!-- Mapa / Ubicación -->
      <div style="margin-top:48px;">
        <div class="accent-line"></div>
        <h3 style="font-family:var(--font-display);font-size:1.2rem;margin-bottom:20px;">
          Encuéntranos
        </h3>

        <!-- *** MAPA DE UBICACIÓN ***
             Reemplaza este placeholder por un iframe de Google Maps:
             <iframe
               src="https://www.google.com/maps/embed?pb=[TU_CÓDIGO_DE_EMBED]"
               width="100%" height="360" style="border:0;border-radius:12px;"
               allowfullscreen loading="lazy"
             ></iframe>
        -->
        <div style="
          width:100%; height:320px;
          background:var(--bg3);
          border:1px solid var(--border);
          border-radius:var(--radius-lg);
          display:flex; align-items:center; justify-content:center;
          color:var(--muted); font-size:0.9rem;
        ">
          📍 Aquí va el mapa de Google Maps (reemplazar con iframe embed)
        </div>

        <!-- Datos de contacto -->
        <div style="display:flex;flex-wrap:wrap;gap:16px;margin-top:24px;">

          <div class="spec-item" style="flex:1;min-width:200px;">
            <div class="spec-label">📍 Dirección</div>
            <div class="spec-value">[Calle, Número, Colonia, Ciudad]</div>
          </div>

          <div class="spec-item" style="flex:1;min-width:200px;">
            <div class="spec-label">📞 Teléfono / WhatsApp</div>
            <div class="spec-value">+52 [NÚMERO]</div>
          </div>

          <div class="spec-item" style="flex:1;min-width:200px;">
            <div class="spec-label">⏰ Horario</div>
            <div class="spec-value">[HORARIO, ej: Lun–Sáb 10–20h]</div>
          </div>

          <div class="spec-item" style="flex:1;min-width:200px;">
            <div class="spec-label">✉️ Correo</div>
            <div class="spec-value">[correo@pixelvault.mx]</div>
          </div>

        </div>

      </div>

    </section><!-- /section-nosotros -->

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN GENÉRICA: CONSOLAS (Nintendo / Xbox / PS / Retro)
         Se reutiliza para cada plataforma; el título y contenido
         se actualiza por JS según la plataforma seleccionada
         ────────────────────────────────────────────────────────── -->
    <section id="section-consolas-plataforma" class="page-section">

      <div class="section-header">
        <div>
          <h2 class="section-title" id="consolas-plataforma-title">Consolas</h2>
          <p class="section-subtitle" id="consolas-plataforma-sub">Catálogo disponible</p>
        </div>
      </div>

      <div class="filters-bar">
        <button class="filter-btn active">Todos los modelos</button>
        <button class="filter-btn">Solo venta de consola</button>
        <button class="filter-btn">Bundle con juego</button>
        <button class="filter-btn">Accesorios incluidos</button>
      </div>

      <div class="consoles-grid" id="consolas-plataforma-grid">
        <!-- Las tarjetas se generan aquí por JS o se agregan manualmente -->
        <!-- Ejemplo de tarjeta vacía: -->
        <div class="console-card">
          <div class="console-img-placeholder">
            <!-- *** IMAGEN CONSOLA ***
                 <img src="URL" alt="Modelo" style="width:100%;height:100%;object-fit:contain;padding:16px;" />
            -->
            🕹️
          </div>
          <div class="console-body">
            <div class="console-brand">[MARCA]</div>
            <div class="console-name">[MODELO]</div>
            <p class="console-desc">[Descripción: almacenamiento, colores disponibles, qué incluye.]</p>
            <div class="console-price">$[PRECIO] MXN</div>
          </div>
        </div>
      </div>

    </section><!-- /section-consolas-plataforma -->

    <!-- ──────────────────────────────────────────────────────────
         SECCIÓN GENÉRICA: JUEGOS POR PLATAFORMA + CATEGORÍA
         ────────────────────────────────────────────────────────── -->
    <section id="section-juegos-plataforma" class="page-section">

      <div class="section-header">
        <div>
          <h2 class="section-title" id="juegos-plataforma-title">Juegos</h2>
          <p class="section-subtitle" id="juegos-plataforma-sub">Catálogo disponible</p>
        </div>
      </div>

      <div class="filters-bar" id="juegos-filters">
        <button class="filter-btn active">Todos</button>
        <button class="filter-btn">🕹️ Físicos</button>
        <button class="filter-btn">💾 Digitales</button>
        <button class="filter-btn">⏳ Preventas</button>
        <button class="filter-btn">🎮 Accesorios</button>
      </div>

      <div class="products-grid" id="juegos-plataforma-grid">
        <!-- Agregar .product-card aquí según plataforma seleccionada -->
        <!-- Template de producto vacío: -->
        <div class="product-card">
          <div class="product-img-placeholder">
            <!-- *** IMAGEN JUEGO *** -->
            🎮
          </div>
          <div class="product-body">
            <div class="product-console">[CONSOLA]</div>
            <div class="product-name">[NOMBRE DEL JUEGO]</div>
            <div class="product-meta">
              <span class="meta-tag">📅 [AÑO]</span>
              <span class="meta-tag">[MODO]</span>
            </div>
            <div class="product-price-row">
              <span class="product-price">$[PRECIO]</span>
              <button class="btn-add-cart">+</button>
            </div>
          </div>
        </div>
      </div>

    </section><!-- /section-juegos-plataforma -->

  </main><!-- /main-content -->

  <!-- ============================================================
       FOOTER
       ============================================================ -->
  <footer id="footer">
    <div class="footer-inner">

      <div class="footer-grid">

        <!-- Columna marca -->
        <div class="footer-brand">
          <span class="logo-name">PixelVault</span>
          <!-- *** Edita la descripción de la tienda *** -->
          <p>[Descripción corta de la tienda. Ej: "Somos tu tienda gamer local de confianza. Videojuegos físicos y digitales, consolas, accesorios y más."]</p>
          <div class="social-links">
            <!-- *** REDES SOCIALES: Cambia los href por las URLs reales ***
                 Facebook: https://facebook.com/[tu_pagina]
                 Instagram: https://instagram.com/[tu_cuenta]
                 TikTok: https://tiktok.com/@[tu_cuenta]
                 WhatsApp: https://wa.me/[tu_número]
            -->
            <a class="social-btn" href="#" title="Facebook">f</a>
            <a class="social-btn" href="#" title="Instagram">📸</a>
            <a class="social-btn" href="#" title="TikTok">♪</a>
            <a class="social-btn" href="#" title="WhatsApp">💬</a>
          </div>
        </div>

        <!-- Columna tienda -->
        <div class="footer-col">
          <h4>Tienda</h4>
          <ul>
            <li><a onclick="showSection('inicio')">Inicio</a></li>
            <li><a onclick="showSection('juegos-todas-consolas')">Videojuegos</a></li>
            <li><a onclick="showSection('accesorios')">Accesorios</a></li>
            <li><a onclick="showSection('consolas-solo-venta')">Consolas</a></li>
            <li><a onclick="showSection('juegos-nintendo-preventa')">Preventas</a></li>
          </ul>
        </div>

        <!-- Columna info -->
        <div class="footer-col">
          <h4>Información</h4>
          <ul>
            <li><a onclick="showSection('nosotros')">Nosotros</a></li>
            <li><a onclick="showSection('citas')">Agendar cita</a></li>
            <li><a href="#">Política de envíos</a></li>
            <li><a href="#">Devoluciones</a></li>
            <li><a href="#">Aviso de privacidad</a></li>
          </ul>
        </div>

        <!-- Columna contacto -->
        <div class="footer-col">
          <h4>Contacto</h4>
          <ul>
            <li><a href="#">📍 [Dirección]</a></li>
            <li><a href="#">📞 [Teléfono]</a></li>
            <!-- *** URL de WhatsApp: reemplaza [NÚMERO] por tu número con código de país sin + ni espacios ***
                 Ej: https://wa.me/5212221234567 -->
            <li><a href="https://wa.me/[NÚMERO]">💬 WhatsApp</a></li>
            <li><a href="#">✉️ [correo]</a></li>
            <li><a href="#">⏰ [Horario]</a></li>
          </ul>
        </div>

      </div><!-- /footer-grid -->

      <div class="footer-bottom">
        <p>© 2025 PixelVault. Todos los derechos reservados.</p>
        <p style="color:var(--muted);font-size:0.78rem;">
          Diseño: PixelVault Team · Hecho con ❤️ para gamers
        </p>
      </div>

    </div>
  </footer>

  <!-- ============================================================
       JAVASCRIPT
       – Carrusel automático con dots
       – Navegación entre secciones (showSection)
       – Filtros de productos
       – Lógica básica de citas
       ============================================================ -->
  <script>
    /* ─────────────────────────────────────────────────────────────
       CARRUSEL
       ───────────────────────────────────────────────────────────── */
    const track    = document.getElementById('carousel-track');
    const dots     = document.querySelectorAll('.dot');
    const slides   = document.querySelectorAll('.carousel-slide');
    let current    = 0;
    let autoPlay;

    /** Mueve el carrusel al slide indicado */
    function goToSlide(index) {
      current = (index + slides.length) % slides.length;
      track.style.transform = `translateX(-${current * 100}%)`;
      dots.forEach((d, i) => d.classList.toggle('active', i === current));
    }

    /** Avanza al siguiente slide */
    function nextSlide() { goToSlide(current + 1); }

    /** Retrocede al slide anterior */
    function prevSlide() { goToSlide(current - 1); }

    // Botones de control
    document.getElementById('carousel-next').addEventListener('click', () => {
      nextSlide();
      resetAutoPlay();
    });
    document.getElementById('carousel-prev').addEventListener('click', () => {
      prevSlide();
      resetAutoPlay();
    });

    /** Reinicia el temporizador de autoplay */
    function resetAutoPlay() {
      clearInterval(autoPlay);
      autoPlay = setInterval(nextSlide, 5000); // Cambia cada 5 segundos
    }

    resetAutoPlay(); // Arranca el autoplay al cargar

    /* ─────────────────────────────────────────────────────────────
       BANNER – Cerrar el banner superior
       ───────────────────────────────────────────────────────────── */
    document.getElementById('banner-close').addEventListener('click', function() {
      document.getElementById('top-banner').style.display = 'none';
    });

    /* ─────────────────────────────────────────────────────────────
       NAVEGACIÓN DE SECCIONES
       Mapa de sectionId → id del elemento HTML correspondiente
       ───────────────────────────────────────────────────────────── */

    // Sección anterior (para el botón "volver")
    let previousSection = 'inicio';

    /**
     * Muestra la sección correspondiente al id dado.
     * Oculta todas las demás.
     * @param {string} sectionId - Identificador lógico de la sección
     */
    function showSection(sectionId) {
      // Ocultar todas las secciones
      document.querySelectorAll('.page-section').forEach(s => s.classList.remove('visible'));

      // Actualizar sección anterior
      previousSection = sectionId;

      // ── Routing de secciones ──────────────────────────────────

      if (sectionId === 'inicio') {
        document.getElementById('section-inicio').classList.add('visible');

      } else if (sectionId === 'game-detail' || sectionId.startsWith('game-')) {
        // Vista de detalle de un juego específico
        document.getElementById('section-game-detail').classList.add('visible');

      } else if (sectionId === 'accesorios' || sectionId.includes('accesorios')) {
        document.getElementById('section-accesorios').classList.add('visible');

      } else if (sectionId === 'citas') {
        document.getElementById('section-citas').classList.add('visible');

      } else if (sectionId === 'nosotros') {
        document.getElementById('section-nosotros').classList.add('visible');

      } else if (sectionId.startsWith('consolas-')) {
        // Secciones de consolas por plataforma
        const plataforma = sectionId.replace('consolas-', '');
        const titles = {
          nintendo:      ['🍄 Nintendo', 'Consolas Nintendo disponibles'],
          xbox:          ['🟩 Xbox', 'Consolas Xbox disponibles'],
          playstation:   ['🔵 PlayStation', 'Consolas PlayStation disponibles'],
          retro:         ['👾 Retro', 'Consolas retro / colección clásica'],
          'solo-venta':  ['📦 Solo consolas', 'Venta exclusiva de consolas sin accesorios'],
        };
        const [title, sub] = titles[plataforma] || ['Consolas', 'Catálogo disponible'];
        document.getElementById('consolas-plataforma-title').textContent = title;
        document.getElementById('consolas-plataforma-sub').textContent   = sub;
        document.getElementById('section-consolas-plataforma').classList.add('visible');

      } else if (sectionId.startsWith('juegos-')) {
        // Secciones de juegos por plataforma y categoría
        const partes    = sectionId.replace('juegos-', '').split('-');
        const plataforma = partes[0];
        const categoria  = partes[1] || 'todos';

        const platNames = {
          nintendo:        '🍄 Nintendo',
          xbox:            '🟩 Xbox',
          ps:              '🔵 PlayStation',
          retro:           '👾 Retro',
          'todas-consolas':'🌐 Todas las consolas (menos PC)',
        };

        const catNames = {
          fisicos:   'Físicos',
          digitales: 'Digitales',
          accesorios:'Accesorios',
          preventa:  'Preventas / Bajo pedido',
          todos:     'Todos los títulos',
        };

        const platLabel = platNames[plataforma] || plataforma;
        const catLabel  = catNames[categoria]   || categoria;

        document.getElementById('juegos-plataforma-title').textContent =
          plataforma === 'todas-consolas' ? '🌐 Todas las consolas' : `${platLabel} – ${catLabel}`;
        document.getElementById('juegos-plataforma-sub').textContent =
          `Catálogo de juegos: ${catLabel}`;

        document.getElementById('section-juegos-plataforma').classList.add('visible');

      } else {
        // Fallback: mostrar inicio
        document.getElementById('section-inicio').classList.add('visible');
      }

      // Scroll suave al contenido principal
      document.getElementById('main-content').scrollIntoView({ behavior: 'smooth', block: 'start' });
    }

    /**
     * Abre el detalle de un juego específico
     * @param {string} gameId - ID del juego (para poblar los campos)
     */
    function showGameDetail(gameId) {
      // *** AQUÍ se conectaría con la BD para cargar la info real del juego ***
      // Por ahora muestra datos de ejemplo que se pueden editar:
      // document.getElementById('detail-title').textContent = juego.nombre;
      // document.getElementById('detail-console').textContent = juego.consola;
      // document.getElementById('detail-year').textContent = juego.anio;
      // etc.
      showSection('game-detail');
    }

    /** Regresa a la sección anterior */
    function goBack() {
      showSection('inicio');
    }

    /* ─────────────────────────────────────────────────────────────
       FILTROS DE PRODUCTOS (botones de filtro)
       ───────────────────────────────────────────────────────────── */
    document.querySelectorAll('.filters-bar').forEach(bar => {
      bar.querySelectorAll('.filter-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          // Activa solo el botón clickeado dentro de su barra
          bar.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
          this.classList.add('active');
          // *** AQUÍ iría la lógica de filtrado de productos con JS o fetch a BD ***
        });
      });
    });

    /* ─────────────────────────────────────────────────────────────
       FORMULARIO DE CITAS
       ───────────────────────────────────────────────────────────── */
    function submitCita() {
      const nombre = document.getElementById('cita-nombre').value.trim();
      const tel    = document.getElementById('cita-tel').value.trim();
      const fecha  = document.getElementById('cita-fecha').value;
      const hora   = document.getElementById('cita-hora').value;
      const motivo = document.getElementById('cita-motivo').value;

      if (!nombre || !tel || !fecha || !hora || !motivo) {
        alert('Por favor completa todos los campos obligatorios.');
        return;
      }

      // *** INTEGRACIÓN CON BACKEND ***
      // Aquí iría un fetch() POST a tu endpoint de citas:
      //
      // fetch('/api/citas', {
      //   method: 'POST',
      //   headers: { 'Content-Type': 'application/json' },
      //   body: JSON.stringify({ nombre, tel, fecha, hora, motivo,
      //                          notas: document.getElementById('cita-notas').value })
      // })
      // .then(r => r.json())
      // .then(data => { /* mostrar confirmación */ })
      // .catch(err => { /* manejar error */ });

      // Mientras tanto, confirmación simple:
      alert(`✅ ¡Cita agendada, ${nombre}!\nTe esperamos el ${fecha} a las ${hora}.\nTe contactaremos al ${tel} para confirmar.`);
    }

    /* ─────────────────────────────────────────────────────────────
       CARRITO (contador básico – conectar a BD / localStorage)
       ───────────────────────────────────────────────────────────── */
    let cartCount = 3; // Número inicial de ejemplo

    /** Agrega un ítem al carrito y actualiza el badge */
    function addToCart() {
      cartCount++;
      document.getElementById('cart-count').textContent = cartCount;
    }

    // Asignar addToCart a todos los botones .btn-add-cart
    document.querySelectorAll('.btn-add-cart').forEach(btn => {
      btn.addEventListener('click', function(e) {
        e.stopPropagation(); // Evitar que se active el onclick de la tarjeta
        addToCart();
        // Animación rápida del botón
        this.style.transform = 'scale(1.4)';
        setTimeout(() => { this.style.transform = ''; }, 200);
      });
    });

    /* ─────────────────────────────────────────────────────────────
       BÚSQUEDA (básica – conectar a BD)
       ───────────────────────────────────────────────────────────── */
    document.getElementById('search-input').addEventListener('keydown', function(e) {
      if (e.key === 'Enter' && this.value.trim()) {
        // *** INTEGRACIÓN: fetch a endpoint de búsqueda ***
        // Ej: showSection('busqueda') y llenar resultados
        alert(`Buscando: "${this.value}"\n(Conectar con base de datos de productos)`);
      }
    });
  </script>

</body>
</html>
