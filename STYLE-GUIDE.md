# ELES · Style Guide
**Not for Everyone** — Premium Boutique Fitness Platform

---

## Identidad de Marca

| Atributo | Valor |
|----------|-------|
| Nombre | ELES |
| Tagline | Not for Everyone |
| Subtítulo | Fitness de Élite |
| Logo | `ELES.` con punto en rojo (#70000e) |
| Audiencia | Mujeres exigentes, enfocadas en excelencia |
| Estética | Lujo minimalista, dark mode, premium |

---

## Paleta de Colores

### Tokens CSS
```css
--c-bg:       #1d1d1d           /* Fondo principal */
--c-surface:  #242424           /* Superficie de cards */
--c-surface2: #181818           /* Footer / superficie alternativa */
--c-border:   rgba(255,255,255,0.08)  /* Bordes sutiles */
--c-red:      #70000e           /* Rojo de marca (PRIMARY) */
--c-red-glow: rgba(112,0,14,0.65)    /* Glow del rojo */
--c-red-dim:  rgba(112,0,14,0.10)    /* Rojo muy tenue */
--c-white:    #ffffff
--c-muted:    #888888           /* Texto secundario */
--c-light:    #cccccc           /* Texto cuerpo */
```

### Resumen Visual

| Rol | Color | Hex |
|-----|-------|-----|
| Accent / CTA | ![#70000e](https://placehold.co/16x16/70000e/70000e) Burgundy Red | `#70000e` |
| Background | ![#1d1d1d](https://placehold.co/16x16/1d1d1d/1d1d1d) Near Black | `#1d1d1d` |
| Surface | ![#242424](https://placehold.co/16x16/242424/242424) Dark Gray | `#242424` |
| Surface Alt | ![#181818](https://placehold.co/16x16/181818/181818) Darker Gray | `#181818` |
| Text Primary | ![#ffffff](https://placehold.co/16x16/ffffff/ffffff) White | `#ffffff` |
| Text Body | ![#cccccc](https://placehold.co/16x16/cccccc/cccccc) Light Gray | `#cccccc` |
| Text Muted | ![#888888](https://placehold.co/16x16/888888/888888) Mid Gray | `#888888` |

---

## Tipografía

### Fuentes
```
DM Serif Display — titulares, hero, logo, cursiva para móvil
DM Sans — cuerpo, navegación, botones, UI
```
> Google Fonts: `DM+Serif+Display:ital,wght@0,400;1,400` + `DM+Sans:wght@300;400;500;600`

### Escala Tipográfica

| Elemento | Tamaño | Propiedades |
|----------|--------|-------------|
| Hero Title | `clamp(52px, 9vw, 120px)` | DM Serif Display, normal |
| Section Title | `clamp(28px, 5.5vw, 80px)` | DM Serif Display |
| Card Title | `clamp(22px, 3vw, 34px)` | DM Serif Display |
| Body | `15–18px` | DM Sans 400 |
| Nav Links | `12.5px` | DM Sans 500, uppercase, `ls: 0.08em` |
| Labels / Tags | `9–11px` | DM Sans 600, uppercase, `ls: 0.18–0.25em` |
| Footer | `11.5–13.5px` | DM Sans 400/300 |

### Reglas de Texto

- `text-transform: uppercase` en navegación y etiquetas
- `letter-spacing` extensivo para feel premium (`0.04em` a `0.28em`)
- `-webkit-font-smoothing: antialiased` siempre activo
- `line-height`: 1 en títulos hero / 1.6–1.8 en cuerpo

---

## Espaciado

```css
--pad: clamp(20px, 5vw, 60px)   /* Padding horizontal de contenedor */
```

| Contexto | Valor |
|----------|-------|
| Header padding | `28px 48px` |
| Section padding | `80px–120px 0` |
| Card padding | `24px–40px` |
| Footer padding | `80px 48px 40px` |
| Gap en grids | `24px–60px` |

---

## Easing & Animaciones

```css
--ease-out: cubic-bezier(0.16, 1, 0.3, 1)   /* Elegante, botón de rebote */
--ease:     cubic-bezier(0.25, 0.46, 0.45, 0.94)  /* Smooth general */
```

| Tipo | Duración | Uso |
|------|----------|-----|
| Hover rápido | `0.3s` | Color, opacity, border |
| Hover medio | `0.4–0.5s` | Header scroll, nav underline |
| Imagen zoom | `0.7s` | Cards, fotos neon |
| Drawer móvil | `0.55s` | Apertura de menú |
| Marquee footer | `30s` | Loop infinito |
| Shine CTA | `0.6s` | Barrido de brillo en botón |

---

## Componentes

### Botón Primario (CTA)
```css
background: #70000e;
color: #ffffff;
padding: 13px 24px;
font-size: 11–13px;
font-weight: 700;
text-transform: uppercase;
letter-spacing: 0.1em;
border-radius: 2px;
transition: 0.35s var(--ease-out);

/* Hover */
transform: translateY(-2px);
box-shadow: 0 6px 24px rgba(112,0,14,0.65), 0 0 0 1px rgba(112,0,14,0.4);
/* + shine sweep: gradient de -100% a 150% en 0.6s */
```

### Botón Ghost
```css
border: 1px solid rgba(255,255,255,0.25);
background: transparent;
color: #ffffff;
padding: 16px 34px;
border-radius: 2px;

/* Hover */
border-color: rgba(255,255,255,1);
background: rgba(255,255,255,0.06);
transform: translateY(-3px);
```

### Header / Navegación
```css
/* Estado inicial */
position: fixed; z-index: 999;
padding: 28px 48px;
background: transparent;
border-bottom: 1px solid transparent;

/* Al hacer scroll (>50px) */
background: rgba(29,29,29,0.92);
backdrop-filter: blur(20px) saturate(150%);
border-bottom-color: var(--c-border);
```

**Links de nav — underline hover:**
```css
/* ::after pseudo-element */
content: '';
height: 1.5px;
background: #70000e;
width: 0 → 100% on hover;
box-shadow: 0 0 8px rgba(112,0,14,0.65);
transition: 0.4s var(--ease-out);
```

### Card de Curso
```css
background: var(--c-surface);
border: 1px solid var(--c-border);
overflow: hidden;

/* Imagen */
height: 240px;
filter: brightness(0.7) grayscale(20%);
transform: scale(1);
transition: 0.7s var(--ease-out);

/* Hover imagen */
filter: brightness(0.85) grayscale(0%);
transform: scale(1.06);

/* Hover card */
border-color: rgba(112,0,14,0.4);
```

### Efecto Foto Neon
```css
/* Hover */
border: 2px solid #70000e;
box-shadow:
  inset 0 0 30px rgba(112,0,14,0.2),
  0 0 30px rgba(112,0,14,0.5),
  0 0 80px rgba(112,0,14,0.18);

/* Overlay */
background: radial-gradient(ellipse at center, rgba(112,0,14,0.18) 0%, transparent 70%);
```

### Inputs de Formulario
```css
background: rgba(255,255,255,0.05);
border: 1px solid rgba(255,255,255,0.08);
color: #ffffff;
font-size: 14px;
padding: 16px 20px;
border-radius: 2px;
outline: none;

/* Focus */
border-color: rgba(112,0,14,0.55);
background: rgba(112,0,14,0.04);
```

### Social Icons (Footer)
```css
width: 42px; height: 42px;
border: 1px solid var(--c-border);
border-radius: 4px;
color: #888888;

/* Hover */
color: #70000e;
border-color: #70000e;
transform: translateY(-3px);
box-shadow: 0 0 12px rgba(112,0,14,0.5), inset 0 0 12px rgba(112,0,14,0.07);
```

---

## Layout & Grid

### Contenedor
```css
max-width: 1440px;  /* max en páginas anchas */
padding: 0 var(--pad);
margin: 0 auto;
```

### Grids Clave

| Sección | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Footer | `2.2fr 1fr 1fr 1fr` | `2col` | `1col` |
| Cursos | `3 col` | `2 col` | `1 col` |
| Planes | `2 col` | `2 col` | `1 col` |
| Wellness Card | `1fr 1.1fr` | `1col` | `1col` |

### Breakpoints
```
1100px — ajustes de header y grids grandes
1024px — cambio a tablet layout
700px  — cambio a 2 col → 1 col
640px  — mobile full, hamburger activo
```

---

## Convención de Nombres (BEM)

```
.eles-[componente]__[elemento]--[modificador]

Ejemplos:
.eles-header
.eles-header__nav
.eles-header__cta
.eles-footer__grid
.eles-footer__social
.eles-photo-neon
```

---

## Estructura de Archivos

```
/
├── inicio.html          — Homepage (hero, statement, gateway)
├── cursos.html          — Listado de cursos
├── curso-detalle.html   — Detalle de curso
├── planes.html          — Precios / membresías
├── tienda.html          — E-commerce
├── producto.html        — Detalle de producto
├── metodo.html          — Filosofía / método
├── faq.html             — Preguntas frecuentes
├── privacidad.html      — Política de privacidad
├── terminos.html        — Términos de servicio
├── header.html          — Componente header (copy-paste)
├── footer.html          — Componente footer (copy-paste)
├── components.html      — Librería de componentes
└── logo.png             — Logo de marca
```

> Todo el CSS es vanilla inline en `<style>` tags. Sin frameworks, sin SCSS. Variables CSS en `:root`.

---

## Sombras / Glow de Referencia

```css
/* Rojo estándar */
box-shadow: 0 6px 24px rgba(112,0,14,0.65);

/* Rojo profundo (wellness card) */
box-shadow: 0 20px 60px rgba(112,0,14,0.3), 0 0 0 1px rgba(112,0,14,0.6);

/* Neon foto */
box-shadow: inset 0 0 30px rgba(112,0,14,0.2), 0 0 30px rgba(112,0,14,0.5), 0 0 80px rgba(112,0,14,0.18);

/* Social icon hover */
box-shadow: 0 0 12px rgba(112,0,14,0.5), inset 0 0 12px rgba(112,0,14,0.07);
```

---

*Generado: 2026-04-21 · Proyecto ELES Fitness · Dominacode*
