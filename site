import React, { useState, useEffect } from 'react';

/**
 * Jade & Milo — Gallery (React component)
 *
 * Purpose:
 * - Fix the SyntaxError that was caused by an HTML file placed inside a `code/react` textdoc.
 * - Provide a valid React component (default export) that renders the same gallery UI.
 *
 * How to use:
 * - This file is a React component. If you want a static `index.html`, tell me and I will export it.
 * - To preview locally: create a new CRA/Vite app (or paste into an existing React app) and import this component.
 *
 * Notes on tests:
 * - A small runtime "self-test" runs in the console to validate the image list (basic sanity checks).
 * - If you want unit tests (Jest) or an HTML export, tell me which you prefer.
 */

export default function JadeMiloGallery() {
  // Default image list (replace with your local images in /images/ or with URLs)
  const defaultImages = [
    '/images/1.jpg',
    '/images/2.jpg',
    '/images/3.jpg',
    '/images/4.jpg',
    '/images/5.jpg',
    '/images/6.jpg',
  ];

  const [images] = useState(defaultImages);
  const [lightboxSrc, setLightboxSrc] = useState(null);

  useEffect(() => {
    // Run a few lightweight runtime "tests" (sanity checks) and report to console
    const results = runSanityChecks(images);
    console.group('Gallery sanity checks');
    results.forEach(r => console.log(r.pass ? '✔️' : '❌', r.name, '-', r.message));
    console.groupEnd();
  }, [images]);

  function runSanityChecks(imgs) {
    const results = [];
    results.push({ name: 'Has images', pass: Array.isArray(imgs) && imgs.length > 0, message: `${imgs.length} image(s) configured` });
    const allStrings = imgs.every(src => typeof src === 'string');
    results.push({ name: 'All src are strings', pass: allStrings, message: allStrings ? 'OK' : 'One or more src are not strings' });
    const reachableLike = imgs.every(src => src.startsWith('/') || src.startsWith('http'));
    results.push({ name: 'Src look like valid paths/URLs', pass: reachableLike, message: reachableLike ? 'Looks good' : 'Some src may be invalid (not starting with / or http)' });
    return results;
  }

  function openLightbox(src) {
    setLightboxSrc(src);
  }
  function closeLightbox() {
    setLightboxSrc(null);
  }

  function scrollToSection(id) {
    const el = document.getElementById(id);
    if (el) el.scrollIntoView({ behavior: 'smooth' });
  }

  return (
    <div className="jm-root">
      <style>{`
        :root{ --bg:#fbfaf8; --card:#fff; --muted:#6b6b6b; --accent:#7aa582; --radius:14px; --gap:14px; }
        *{box-sizing:border-box}
        .jm-root{font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; background:var(--bg); color:#111; padding:24px}
        header{display:flex;align-items:center;gap:16px;max-width:1100px;margin:0 auto}
        .logo{width:84px;height:84px;border-radius:12px;overflow:hidden;flex:0 0 84px;box-shadow:0 6px 18px rgba(0,0,0,.06)}
        .logo img{width:100%;height:100%;object-fit:cover}
        h1{margin:0;font-size:28px}
        p.lead{margin:6px 0 0;color:var(--muted)}
        .hero{max-width:1100px;margin:20px auto;border-radius:16px;overflow:hidden;box-shadow:0 10px 30px rgba(17,17,17,.06);background:var(--card)}
        .banner{width:100%;height:260px;object-fit:cover;display:block}
        nav{display:flex;gap:12px;margin-top:12px}
        nav button{padding:8px 12px;border-radius:999px;background:transparent;border:0;color:var(--muted);font-weight:600;cursor:pointer}
        nav button.active{background:var(--accent);color:white}
        main{max-width:1100px;margin:22px auto}
        .gallery{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:var(--gap)}
        .photo{background:var(--card);border-radius:var(--radius);overflow:hidden;position:relative;cursor:pointer;box-shadow:0 8px 20px rgba(11,11,11,.06)}
        .photo img{width:100%;height:100%;object-fit:cover;display:block;transition:transform .35s ease}
        .photo:hover img{transform:scale(1.06)}
        .caption{position:absolute;left:12px;bottom:12px;padding:6px 10px;border-radius:999px;background:rgba(0,0,0,.45);color:#fff;font-size:13px}
        .about{color:var(--muted);max-width:780px}
        footer{margin-top:30px;padding:18px;text-align:center;color:var(--muted);font-size:14px}
        /* Lightbox */
        .lm-modal{position:fixed;inset:0;background:rgba(0,0,0,.75);display:flex;align-items:center;justify-content:center;padding:20px;opacity:1}
        .lm-content{max-width:90%;max-height:90%;border-radius:12px;overflow:hidden}
        .lm-content img{display:block;width:100%;height:auto;max-height:85vh;object-fit:contain;background:#000}
        .lm-close{position:absolute;top:18px;right:18px;background:rgba(255,255,255,.1);border:0;color:white;padding:8px 10px;border-radius:8px;cursor:pointer}
        @media (max-width:640px){ .banner{height:160px} h1{font-size:22px} }
      `}</style>

      <header>
        <div className="logo">
          <img src="https://images.unsplash.com/photo-1518791841217-8f162f1e1131?q=80&w=400&auto=format&fit=crop&ixlib=rb-4.0.3&s=000" alt="logo" />
        </div>
        <div>
          <h1>Jade & Milo</h1>
          <p className="lead">Photos, instants & tendresse — Une galerie à personnaliser.</p>
          <nav>
            <button onClick={() => window.scrollTo({ top: 0, behavior: 'smooth' })} className="active">Accueil</button>
            <button onClick={() => scrollToSection('gallery')}>Galerie</button>
            <button onClick={() => scrollToSection('about')}>À propos</button>
          </nav>
        </div>
      </header>

      <section className="hero" id="home" style={{ marginTop: 18 }}>
        <img className="banner" alt="bannière" src="https://images.unsplash.com/photo-1503264116251-35a269479413?q=80&w=1600&auto=format&fit=crop&ixlib=rb-4.0.3&s=000" />
        <div style={{ padding: 18 }}>
          <p style={{ margin: 0 }}>Bienvenue sur notre site — remplace les images par celles de ton compte Instagram / Facebook.</p>
        </div>
      </section>

      <main>
        <section id="gallery" style={{ marginTop: 18 }}>
          <h2 style={{ margin: '0 0 12px' }}>Galerie</h2>
          <div className="gallery" id="galleryGrid">
            {images.map((src, idx) => (
              <div key={idx} className="photo" onClick={() => openLightbox(src)}>
                <img src={src} alt={`Photo ${idx + 1}`} />
                <div className="caption">Photo {idx + 1}</div>
              </div>
            ))}
          </div>
        </section>

        <section id="about" style={{ marginTop: 22 }}>
          <h2>À propos</h2>
          <p className="about">Nous sommes Jade & Milo — amoureux de la nature et des petits riens qui font la vie. Ce site est une base : pour mettre tes photos, copie-les dans <code>/images</code> et garde le même nom (ex : 1.jpg, 2.jpg...).</p>
        </section>
      </main>

      <footer>
        <div>Crée avec ❤ — Remplace les images par celles de tes comptes Instagram / Facebook.</div>
      </footer>

      {/* Lightbox */}
      {lightboxSrc && (
        <div className="lm-modal" role="dialog" aria-modal="true" onClick={closeLightbox}>
          <div className="lm-content" onClick={e => e.stopPropagation()}>
            <button className="lm-close" onClick={closeLightbox}>Fermer ✕</button>
            <img src={lightboxSrc} alt="Agrandir" />
          </div>
        </div>
      )}
    </div>
  );
}
