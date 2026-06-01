# Karen Glamour — Website Project Brief

## Contexto del negocio

**Cliente:** Karen Glamour (Instagram: @karu_glamour)
**Dueña:** Karen Estrada — Especialista en Alisados, formada en cosmetología (American Beauty Schools)
**Ubicación:** 2750 SW 87th Ave STE 201, Miami, Florida 33165
**Contacto:** (786) 790-6547
**Servicios principales:** Alisados, Black Diva, hidratación profunda, peinados, color & mechas, cortes
**Objetivo del sitio:** Landing page de alto impacto para adquisición de clientes + reservas + programa VIP

---

## Identidad visual

### Paleta de colores
```
--cream:      #FAF8F5   → Fondo principal
--beige:      #EDE8E0   → Superficies secundarias
--dark:       #1A1A1A   → Fondo oscuro / texto principal
--mid:        #2E2E2E   → Variante oscura
--gold:       #C8A96E   → Acento dorado (color firma)
--gold-light: #DFC08A   → Gold hover
--light-text: #6B6560   → Texto secundario
--border:     #D4CFC8   → Bordes sutiles
```

### Tipografía
- **Display / Headings:** Cormorant Garamond (serif, Google Fonts) — pesos 300, 400, 600; itálica para acentos
- **Body / UI:** Montserrat (sans-serif) — pesos 200, 300, 400, 500
- Estilo editorial: mezcla de serif elegante + sans minimalista, inspirado en Vogue

### Logo
- Monograma **KG** en serif bold con "Karen Glamour" en script cursiva debajo
- Usar como elemento decorativo en fondo a gran escala (muy transparente)
- Color: negro sobre blanco / crema sobre oscuro

### Tono de diseño
- **Editorial de lujo** — mínimo, sofisticado, espacios negativos generosos
- NO gradientes llamativos, NO colores saturados, NO rounded corners exagerados
- Bordes de 0.5px, tipografía espaciada, animaciones suaves

---

## Arquitectura del sitio (Single Page)

### 1. Navigation (fixed)
- Logo "Karen Glamour" en Cormorant
- Links: Nosotros · Resultados · Servicios · VIP
- CTA button: "Reservar"
- Comportamiento: transparente sobre hero oscuro → blanco + blur al hacer scroll

### 2. Hero (sección principal)
**Animaciones implementadas:**
- `KG` gigante en fondo con opacidad ~2.5% como elemento decorativo
- Partículas doradas flotantes (canvas)
- Entrada escalonada de palabras con slide-up: "Karen" → "Glamour" (italic dorado)
- Línea dorada que se expande animada
- Subtítulo: *"Tu cabello merece lo mejor"*
- CTAs: `Reservar ahora` (dorado) + `Ver transformaciones` (ghost)
- Mouse scroll indicator animado

### 3. Marquee strip
- Franja dorada con texto scrolling continuo
- Contenido: servicios + keywords de la marca

### 4. About / Nosotros
- Layout dos columnas: monograma KG grande a la izquierda + texto derecha
- Stats: 8K+ seguidores · 500+ publicaciones · 100% dedicación
- Corner decorativo dorado

### 5. Before & After (Transformaciones) ⭐ Feature principal
- Sección sobre fondo oscuro
- **3 sliders de comparación interactivos** (drag/touch)
- Al entrar en viewport: animación automática de izquierda → 50% (reveal)
- Luego arrastrable libremente
- Servicios: Alisado Brasileño / Black Diva / Hidratación Profunda
- Badges: "Antes" (gris) y "Después" (dorado)
- **TODO: reemplazar SVG placeholder por fotos reales de clientes**

### 6. Servicios
- Grid 3x2 sobre fondo oscuro
- Numerados 01–06
- Hover: borde dorado top que se expande de izquierda a derecha
- Precio en itálica dorada
- Servicios: Alisado Brasileño ($150+) · Black Diva ($200+) · Hidratación ($80+) · Peinados ($60+) · Color & Mechas ($120+) · Corte & Estilo ($45+)

### 7. VIP Membership ⭐
- Tarjeta de sellos estilo loyalty card
- 10 stamps: 5 rellenos (ejemplo) + 4 vacíos + 1 "GRATIS" con borde dorado
- CTA: "Quiero ser VIP"
- **TODO: definir reglas reales del programa (cada cuántas visitas, qué descuento)**

### 8. Booking / Reservas
- Formulario minimalista sobre fondo oscuro
- Campos: Nombre · Teléfono/WhatsApp · Servicio deseado
- CTA dorado: "Solicitar cita →"
- **TODO: conectar a WhatsApp API, Calendly, o sistema de reservas real**

### 9. Footer
- Logo + tagline
- Links internos
- Copyright

---

## Funciones ya implementadas

| Feature | Estado |
|---|---|
| Hero animado con partículas | ✅ Completo |
| Animaciones de entrada (palabras) | ✅ Completo |
| Nav inteligente (scroll behavior) | ✅ Completo |
| Marquee strip | ✅ Completo |
| Scroll reveal en todas las secciones | ✅ Completo |
| Sliders Before/After (3 unidades) | ✅ Funcional (SVG placeholder) |
| Grid de servicios con hover | ✅ Completo |
| Stamp card VIP | ✅ Visual completo |
| Formulario de reservas | ✅ UI lista, sin backend |
| Responsive mobile | ✅ Básico |

---

## Features pendientes / próximas fases

### Fase 2 — Contenido real
- [ ] Reemplazar SVG placeholders en sliders por **fotos reales** de clientes (antes/después)
- [ ] Galería de Instagram embebida o grid de fotos
- [ ] Testimonios / reviews de clientes
- [ ] Foto de Karen + historia personal

### Fase 3 — Funcionalidad
- [ ] **WhatsApp CTA** flotante (botón fijo bottom-right)
- [ ] **Integración de reservas** (Calendly embed, Square Appointments, o form → email)
- [ ] **Formulario de contacto** funcional con notificación
- [ ] **Google Maps embed** con ubicación del salón

### Fase 4 — E-commerce / Productos
- [ ] Sección Shop para bolsas y merch KG
- [ ] Integración con Shopify o WooCommerce (si aplica)

### Fase 5 — SEO & Performance
- [ ] Meta tags, Open Graph, favicon con logo KG
- [ ] Lazy loading de imágenes
- [ ] Performance audit (Lighthouse)
- [ ] Google Analytics / Meta Pixel

### Fase 6 — Nice to have
- [ ] Sección de precios expandible / acordeón
- [ ] Lightbox para galería
- [ ] Cookie banner
- [ ] Página 404 personalizada

---

## Stack técnico (recomendado para producción)

```
Framework:    HTML + CSS + Vanilla JS  (ya construido, listo para exportar)
              O React + Vite si se prefiere componetización
Fonts:        Google Fonts CDN (Cormorant Garamond + Montserrat)
Hosting:      Vercel, Netlify, o GitHub Pages (gratis)
Dominio:      karenglamour.com o karenglamour.net
Reservas:     Calendly embed (gratis) o Square Appointments
WhatsApp:     wa.me/17867906547
```

---

## Notas de implementación

- El archivo HTML actual es **autocontenido** (sin dependencias externas excepto Google Fonts)
- Los sliders usan `clip-path: inset()` para el efecto de revelación — compatible con todos los browsers modernos
- Las partículas son canvas vanilla JS, muy ligeras
- El scroll reveal usa `IntersectionObserver` nativo
- Los precios son placeholder — **confirmar con Karen antes de publicar**

---

*Proyecto iniciado: Mayo 2026 · Diseño y desarrollo: [tu nombre]*
