# CoffeeHouse kiosk

Versión autónoma de CoffeeHouse para el Moto G100 de la barra: PWA instalable, pantalla completa apaisada, funciona sin conexión, con timer de preparación, modo oscuro y backup de datos.

## Archivos

- `index.html` — la app completa (datos en localStorage del navegador)
- `manifest.json` — identidad de la PWA (pantalla completa, orientación apaisada)
- `sw.js` — service worker: la app funciona offline después de la primera carga
- `icon-192.png` / `icon-512.png` — íconos de la app instalada

## Paso 1 — Publicar en GitHub Pages (una sola vez, desde la PC)

1. Entrá a github.com y creá una cuenta usando el Gmail de CoffeeHouse (así todo el ecosistema del celu queda bajo esa identidad).
2. Botón **New repository** → nombre `coffeehouse` → visibilidad **Public** → Create repository.
3. En el repo: **Add file → Upload files** → arrastrá los 5 archivos de esta carpeta → **Commit changes**.
4. **Settings → Pages** → en "Build and deployment" elegí **Deploy from a branch** → branch `main`, carpeta `/ (root)` → Save.
5. Esperá 1–2 minutos y va a aparecer la URL: `https://TU-USUARIO.github.io/coffeehouse/`

Para futuras versiones: repetís el paso 3 subiendo el `index.html` nuevo (y subí el número de versión del caché (p. ej. `v2` → `v3`) en `sw.js` para que el caché se renueve).

## Paso 2 — Instalar en el G100

1. Abrí Chrome en el celu (logueado con la cuenta CoffeeHouse) y entrá a la URL.
2. Menú **⋮ → Instalar aplicación** (o "Agregar a pantalla de inicio").
3. Abrila desde su ícono: pantalla completa, sin barra de navegación, orientación apaisada.
4. La primera vez que uses el timer, aceptá el permiso de notificaciones.

## Paso 3 (opcional) — Kiosk total

**Ajustes → Seguridad → Fijar aplicaciones** (o "App pinning"): con la app fijada, el celu no sale de CoffeeHouse ni por accidente. Para salir: gesto de Recientes sostenido.

## Cómo funciona lo importante

**Timer.** Guarda la hora de finalización real, no una cuenta regresiva: si la pantalla se suspende a mitad de los 4 minutos de la prensa, al despertar el conteo está donde debe estar. Mientras corre, la app pide mantener la pantalla encendida (wake lock); al terminar suena, vibra y notifica, y el wake lock se libera para no castigar la batería.

**Datos.** Viven en el navegador del celu (localStorage). **⇪ Exportar** copia un backup JSON al portapapeles; **⇩ Importar** lo pega en otra copia de la app. Hacé un export cada tanto por las dudas.

**Modo barra.** El botón 🌙 alterna el tema oscuro para que de noche el celu se funda con el mueble en vez de brillar. La elección queda guardada.

**Offline.** Después de la primera visita, la app abre sin internet.
