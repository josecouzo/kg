# CLAUDE.md — Karen Glamour Website

Este archivo le da contexto completo a Claude Code sobre el proyecto.
Léelo al inicio de cada sesión antes de tocar cualquier archivo.

---

## Qué es este proyecto

Sitio web para **Karen Glamour**, salón de belleza especializado en alisados y tratamientos capilares ubicado en Miami, Florida. El sitio es una **landing page de una sola página** pensada para impresionar a la dueña del negocio como pieza de venta de servicios web, y luego escalar con más funcionalidades.

El objetivo de diseño es: **editorial de lujo** — como una revista de moda de alto nivel, no un sitio genérico de salón.

---

## Estructura de archivos

```
karen-glamour/
├── CLAUDE.md          ← este archivo
├── index.html         ← toda la app (HTML + CSS + JS en un solo archivo)
├── /assets
│   ├── /images        ← fotos reales (aún pendientes del cliente)
│   │   ├── /before-after   ← pares de fotos para los sliders
│   │   └── /gallery        ← trabajos del salón
│   └── /icons         ← favicon KG
└── /docs
    └── KAREN_GLAMOUR_PROJECT.md   ← brief completo del proyecto
```

> Por ahora todo está en `index.html`. Si el proyecto crece, separar en componentes.

---

## Identidad visual — NUNCA romper estas reglas

### Paleta de colores (usar siempre las variables CSS)
```css
--cream:      #FAF8F5   /* fondo principal — secciones claras */
--beige:      #EDE8E0   /* superficies secundarias */
--dark:       #1A1A1A   /* fondo oscuro — hero, services, booking */
--mid:        #2E2E2E   /* variante dark para hovers */
--gold:       #C8A96E   /* acento firma — ÚNICO color de énfasis */
--gold-light: #DFC08A   /* gold en hover */
--light-text: #6B6560   /* texto secundario sobre cream */
--border:     #D4CFC8   /* bordes sutiles */
```

### Tipografía
```
Headings/Display → Cormorant Garamond (serif) — peso 300 normal, italic para énfasis
Body/UI          → Montserrat (sans-serif)     — peso 300 normal, 500 para labels
```

### Reglas de diseño que NO se deben violar
- Bordes siempre `0.5px` — nunca `1px` excepto el stamp VIP free y featured cards
- Sin `border-radius` en elementos rectangulares clave (botones principales, cards de servicios)
- Sin gradientes de fondo — usar colores sólidos de la paleta
- Sin sombras decorativas — solo funcionales (handle del slider)
- Letter-spacing generoso en texto pequeño uppercase: mínimo `0.15em`
- El dorado `--gold` es el ÚNICO color de acento — no agregar azules, rosas, etc.
- Espaciado generoso: padding de secciones mínimo `8rem` vertical en desktop

---

## Secciones del sitio y su estado

| # | Sección | Estado | Notas |
|---|---------|--------|-------|
| 1 | Navigation fixed | ✅ | Transparente → blanco+blur al scroll |
| 2 | Hero animado | ✅ | Partículas canvas + slide-up de palabras |
| 3 | Marquee strip dorado | ✅ | Loop continuo |
| 4 | About / Nosotros | ✅ | 2 columnas + stats |
| 5 | Before & After sliders | ✅ | 3 sliders drag/touch, SVG placeholder |
| 6 | Grid de servicios | ✅ | 3×2, hover con línea dorada |
| 7 | VIP stamp card | ✅ | Visual, sin lógica real aún |
| 8 | Booking form | ✅ | UI lista, sin backend |
| 9 | Footer | ✅ | Links + copyright |

---

## Lo que falta hacer — por prioridad

### 🔴 Prioridad 1 — Antes de mostrarle a Karen
- [ ] **WhatsApp flotante**: botón fijo `bottom: 2rem; right: 2rem` que abra `https://wa.me/17867906547?text=Hola%20Karen%2C%20quiero%20reservar%20una%20cita`
- [ ] **Fotos reales en sliders**: cuando Karen mande fotos, reemplazar los `<svg>` placeholder en `.cs-before` y `.cs-after` por `<img>` con `object-fit: cover; width:100%; height:100%`
- [ ] **Confirmar precios**: los precios actuales son placeholder, verificar con Karen

### 🟡 Prioridad 2 — Para versión funcional
- [ ] **Formulario de reservas funcional**: conectar a Formspree (gratis) o abrir WhatsApp con datos pre-llenados
  ```js
  // Opción simple: al submit, redirigir a WhatsApp
  const msg = `Hola Karen, me llamo ${name}, quiero reservar ${service}. Mi contacto: ${phone}`;
  window.open(`https://wa.me/17867906547?text=${encodeURIComponent(msg)}`);
  ```
- [ ] **Google Maps**: embed del salón en sección de contacto o footer
- [ ] **Meta tags SEO**: title, description, og:image, favicon

### 🟢 Prioridad 3 — Para versión completa
- [ ] Galería de fotos (grid masonry) con fotos del Instagram de Karen
- [ ] Testimonios de clientes (texto o capturas de reseñas de Google)
- [ ] Sección de productos / merch KG (bolsas, productos del salón)
- [ ] Integración Calendly para reservas formales
- [ ] Google Analytics + Meta Pixel

---

## Cómo trabajar el Before/After cuando lleguen las fotos

Cada slider tiene esta estructura. Solo hay que reemplazar el contenido interno:

```html
<!-- ANTES: reemplazar este bloque SVG -->
<div class="cs-before cs-before-1">
  <svg>...</svg>  <!-- ← BORRAR ESTO -->
</div>

<!-- Por esto: -->
<div class="cs-before cs-before-1">
  <img src="assets/images/before-after/alisado-antes.jpg"
       style="width:100%;height:100%;object-fit:cover;object-position:center top;">
</div>

<!-- Igual para cs-after -->
<div class="cs-after cs-after-1">
  <img src="assets/images/before-after/alisado-despues.jpg"
       style="width:100%;height:100%;object-fit:cover;object-position:center top;">
</div>
```

Pedir a Karen fotos en **portrait** (vertical), mínimo 800×1200px.
Idealmente las 3 parejas corresponden a: Alisado · Black Diva · Hidratación.

---

## Cómo agregar el botón de WhatsApp flotante

Agregar justo antes de `</body>`:

```html
<a href="https://wa.me/17867906547?text=Hola%20Karen%2C%20quiero%20reservar%20una%20cita"
   target="_blank"
   id="waBtn"
   style="
     position: fixed;
     bottom: 2rem;
     right: 2rem;
     z-index: 999;
     width: 52px;
     height: 52px;
     background: #25D366;
     border-radius: 50%;
     display: flex;
     align-items: center;
     justify-content: center;
     box-shadow: 0 4px 20px rgba(37,211,102,0.4);
     transition: transform 0.3s, box-shadow 0.3s;
     text-decoration: none;
   "
   onmouseenter="this.style.transform='scale(1.1)'"
   onmouseleave="this.style.transform='scale(1)'"
   aria-label="Contactar por WhatsApp">
  <svg width="26" height="26" viewBox="0 0 24 24" fill="white">
    <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347z"/>
    <path d="M12 0C5.373 0 0 5.373 0 12c0 2.123.554 4.118 1.528 5.855L0 24l6.335-1.508A11.945 11.945 0 0012 24c6.627 0 12-5.373 12-12S18.627 0 12 0zm0 22c-1.844 0-3.576-.49-5.073-1.346l-.364-.215-3.762.895.952-3.67-.237-.378A9.956 9.956 0 012 12C2 6.477 6.477 2 12 2s10 4.477 10 10-4.477 10-10 10z"/>
  </svg>
</a>
```

---

## Deploy

### Opción A — Netlify (recomendada, gratis)
```bash
# Arrastrar la carpeta del proyecto a netlify.com/drop
# O con CLI:
npm install -g netlify-cli
netlify deploy --dir . --prod
```

### Opción B — Vercel
```bash
npm install -g vercel
vercel --prod
```

### Opción C — GitHub Pages
```bash
git init && git add . && git commit -m "Karen Glamour launch"
git remote add origin https://github.com/tuuser/karen-glamour.git
git push -u origin main
# Activar Pages en Settings del repo → Branch: main
```

**Dominio sugerido:** `karenglamour.com` — registrar en Namecheap (~$10/año)

---

## Información del cliente

```
Negocio:    Karen Glamour
Instagram:  @karu_glamour
Dirección:  2750 SW 87th Ave STE 201, Miami, Florida 33165
WhatsApp:   (786) 790-6547
Especialidad: Alisados, Black Diva, tratamientos capilares
```

---

## Convenciones de código

- Todo en **español** para copy/texto visible
- Comentarios en el código en **español**
- Variables CSS siempre con `--` prefix en `:root`
- Clases CSS en kebab-case: `.service-card`, `.cs-after`, `.hero-word`
- IDs solo para JS hooks: `#mainNav`, `#cs1`, `#heroLine`
- Animaciones: preferir CSS transitions sobre JS cuando sea posible
- JS: vanilla, sin frameworks, sin npm para mantenerlo simple

---

## Cómo pedir cambios a Claude Code

Ser específico con la sección y el comportamiento esperado. Ejemplos:

```
✅ "En la sección #services, cambia el padding de 8rem a 6rem en mobile"
✅ "Agrega el botón flotante de WhatsApp siguiendo las instrucciones del CLAUDE.md"
✅ "Reemplaza los SVG del slider cs2 con las imágenes adjuntas"

❌ "Haz el sitio más bonito"
❌ "Cambia los colores" (sin especificar cuáles)
```

---

*Última actualización: Mayo 2026*
