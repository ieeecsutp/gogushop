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

## Nueva sección: Experiencia K-Pop + Testimonios Reales

- Sección "Experiencia K-Pop" con seis beneficios visuales.
- Sub-sección de reseñas rápidas con íconos dinámicos.
- Sección "Lo Que Dicen Nuestros Fans" con estadísticas y testimonios reales.
- Uso del componente Card extendido con tres variantes:
  - default — cards con íconos e información
  - compact — cards de estadísticas
  - testimonial — cards de reseñas con ícono de usuario
- Optimización del espacio lateral con max-w-[86vw] y px-8.

## Contribuir / Ajustes

- Añade álbumes en la sección `#albums` en `src/pages/index.astro` o en `src/components`.
- Para integrar carrito/estado, dime cómo prefieres manejar estado (localStorage, store, backend) y lo integro en la badge del navbar.

---

Proyecto creado con Astro. Si quieres, aplico la configuración Tailwind y añado un ejemplo de hero con clases Tailwind.
