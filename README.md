# Gogushop Music — Landing page

Landing page sencilla hecha con Astro que muestra productos coreanos, en particular discos (álbumes) de grupos musicales K‑Pop. Toda la página es una single-page con navegación interna (smooth scroll) hacia secciones: Inicio, Álbumes, Fans, FAQ, Contacto y Footer.

## Estructura principal

- public/ — recursos públicos (favicon, imágenes).
- src/
  - components/ — Navbar.astro, Welcome.astro, otros componentes.
  - layouts/ — Layout.astro (inserta Navbar globalmente).
  - pages/ — index.astro (contenido de la landing).
  - styles/ — global.css (estilos globales y directivas Tailwind cuando se use).
- package.json, tsconfig.json, astro.config.mjs

## Requisitos

- Node.js (v16+ recomendada)
- pnpm (recomendado) — también funciona con npm/yarn si adapta los comandos.

## Instalación (Windows / PowerShell)

1. Abrir terminal en la carpeta del proyecto:
   cd "d:\Voluntariado C-Proyectos\Proyect_Web\app_gogushop"
2. Instalar dependencias:
   pnpm install

## Ejecutar en desarrollo

pnpm run dev

- Abre http://localhost:4321
- Los enlaces del Navbar apuntan a secciones con ids: `#inicio`, `#albums`, `#fans`, `#faq`, `#contact`, `#footer`. Al hacer clic se realiza smooth scroll dentro de la misma página.

## Build / Previsualización

- Construir producción:
  pnpm run build
- Previsualizar build:
  pnpm run preview

## Tailwind (opcional)

Si quieres usar Tailwind:

1. Instalar:
   pnpm install -D tailwindcss postcss autoprefixer
2. Crear/configurar:
   npx tailwindcss init -p
3. Asegúrate de que `tailwind.config.(cjs|js)` incluya:
   ./src/\*_/_.{astro,html,js,ts,jsx,tsx}
4. Añadir al inicio de `src/styles/global.css`:
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
5. Reinicia el servidor dev.

## Notas rápidas para desarrollo

- La navegación interna está implementada en `src/components/Navbar.astro` — cierra el menú móvil al navegar y hace scroll suave cuando la sección existe.
- Si mueves contenido de Welcome.astro a index.astro, asegúrate de no renderizar Navbar dos veces (uno en Layout y otro en Welcome).
- Para activar la clase `.active` según la sección visible puedo añadir un IntersectionObserver — dime si lo quieres.

## Contribuir / Ajustes

- Añade álbumes en la sección `#albums` en `src/pages/index.astro` o en `src/components`.
- Para integrar carrito/estado, dime cómo prefieres manejar estado (localStorage, store, backend) y lo integro en la badge del navbar.

---

Proyecto creado con Astro. Si quieres, aplico la configuración Tailwind y añado un ejemplo de hero con clases Tailwind.

---

## ✨ Actualizaciones de diseño y componentes

### 🎶 Sección: Álbumes — Experiencia K-Pop
- Añadida sección “Experiencia K-Pop” con seis beneficios visuales que muestran por qué elegir Gogushop.  
- Incluye una sub-sección de reseñas rápidas con valoraciones, cantidad de fans y años en el mercado.  
- Implementa el componente Card con íconos e información de beneficios.  
- Ajustes de diseño centrado, degradados y espaciado optimizado.

### 💜 Sección: Fans — Testimonios Reales
- Añadida la sección “Lo Que Dicen Nuestros Fans” con estadísticas y testimonios detallados.  
- Incluye cuatro métricas visuales de satisfacción y cuatro testimonios de fans reales.  
- Implementada una sub-sección final con llamada a la acción (Join) que invita a unirse a la comunidad K-Pop.  
- Incluye ícono SVG de comillas decorativas y textos cursivos para las transformaciones.

### 💬 Sección: Preguntas Frecuentes (FAQ)
- Añadida sección “Preguntas Frecuentes” con íconos principales para Álbumes, Envíos, Devoluciones y Soporte.  
- Implementado componente reutilizable `FaqItem.astro` con propiedades dinámicas (`icon`, `tag`, `tagColor`, `gradient`, `question`, `answer`).  
- Usa animaciones nativas de apertura/cierre con rotación de ícono y transiciones suaves.  

### 🧩 Componente: FaqItem.astro
- Nuevo componente modular que representa cada bloque de pregunta/respuesta.  
- Props: `icon`, `tag`, `tagColor`, `gradient`, `question`, `answer`.  
- Animación con `addEventListener` sin dependencias externas, 100% compatible con Astro.

### 🪄 Componente: Card.astro
- Extendido con variantes `testimonial`, `compact` y `join`.  
- Nuevas props: `note`, `time`, `badges`, `rating`, `reviews`, `transformation`.  
- Incluye soporte para íconos SVG coloreables mediante `mask` y `-webkit-mask`.  
- Textos transformados en cursiva (`italic`) y citas visuales con ícono `quote.svg`.

### ⚙️ Integración en la estructura principal
- Modularización completa:
  - `Albums.astro` → sección de experiencia K-Pop.  
  - `Fans.astro` → testimonios y métricas.  
  - `Faq.astro` → preguntas frecuentes.  
- En `welcome.astro` se integran directamente:

  ```astro
  import Albums from "../pages/albums.astro";
  import Fans from "../pages/fans.astro";
  import Faq from "../pages/faq.astro";

  <section id="albums"><Albums /></section>
  <section id="fans"><Fans /></section>
  <section id="faq"><Faq /></section>
