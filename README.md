# Calendario de remates ganaderos 2026

Calendario interactivo de remates ganaderos y exposiciones rurales en Buenos Aires, Chaco, Santa Fe, Entre Ríos, Córdoba, Corrientes, Misiones, Formosa y Santiago del Estero. Vista de calendario, lista y mapa estático liviano, con filtros por firma, provincia y tipo de hacienda.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La aplicación completa (React vía CDN). Es lo que se abre en el navegador. |
| `remates.json` | **Los datos.** Editá este archivo para agregar, cambiar o borrar remates. |
| `sucursales.geojson` | Fuente de polígonos de zonas de sucursales. La app no lo carga en el navegador; usa una asignación liviana precalculada para evitar trabas. |
| `.nojekyll` | Evita que GitHub Pages procese la carpeta con Jekyll (necesario). |

> **Importante:** el `index.html` lee `remates.json` con `fetch()`. Por seguridad del navegador, esto **NO funciona abriendo el HTML con doble clic** (`file://`). Funciona servido desde un servidor web: GitHub Pages, Netlify, o un servidor local.

## Publicar en GitHub Pages

1. Creá un repositorio nuevo en GitHub (por ejemplo `remates-2026`).
2. Subí los archivos (`index.html`, `remates.json`, `sucursales.geojson`, `.nojekyll`) a la raíz del repo.
   - Podés arrastrarlos en **Add file → Upload files**.
3. Andá a **Settings → Pages**.
4. En **Source**, elegí la rama `main` y la carpeta `/ (root)`. Guardá.
5. Esperá 1-2 minutos. El sitio queda en:
   `https://TU-USUARIO.github.io/remates-2026/`

## Probar en local (opcional)

Si querés verlo en tu compu antes de subirlo, abrí una terminal en la carpeta y corré:

```bash
python3 -m http.server 8000
```

Después entrá a `http://localhost:8000` en el navegador. (Con doble clic sobre el HTML **no** carga el JSON.)

## Cómo actualizar los datos

Editá `remates.json`. Cada evento es un objeto con esta forma:

```json
{
  "id": "afa-c01",
  "firma": "AFA",
  "grupo": "AFA",
  "cabana": "Gordos, Conserva e Invernada",
  "fecha": "2026-07-28",
  "hora": "10:00",
  "loc": "Totoras",
  "prov": "Santa Fe",
  "lat": -32.58,
  "lng": -61.17,
  "tipo": "Invernada/Gordo",
  "modalidad": "Presencial + YouTube",
  "confianza": "confirmado",
  "fuente": "consignatarias.com.ar"
}
```

Reglas de los campos:

- **`grupo`** debe ser uno de: `e-Brangus`, `Bellamar`, `Cabañas`, `PKF`, `AFA`, `Pastore`, `Charles`, `Lehmann`, `Rosgan`, `La Ganadera`, `Tres Colonias`, `Exposiciones`. Es lo que controla el color y el filtro de firma. (Si agregás un grupo nuevo, avisá para sumarle color.)
- **`prov`** debe ser: `Buenos Aires`, `Chaco`, `Santa Fe`, `Entre Ríos`, `Córdoba`, `Corrientes`, `Misiones`, `Formosa` o `Santiago del Estero`.
- **`fecha`** en formato `AAAA-MM-DD`.
- **`confianza`**: `confirmado` (fecha publicada por la fuente) o `estimado` (proyección de recurrencia o fecha publicada a confirmar; se muestra atenuado y con la etiqueta “estimado”).
- **`lat` / `lng`**: coordenadas de la localidad, para ubicarla aproximadamente en el mapa estático. Si la fuente no publica localidad, pueden quedar como `null`.

En GitHub podés editar `remates.json` directo desde el navegador (botón del lápiz ✏️). Al confirmar el cambio, GitHub Pages actualiza el sitio en 1-2 minutos.

## Fuentes de los datos

e-brangus.com · braford.org.ar · angussantalucia.com.ar · angusdigital.com.ar · bellamar.com.ar · pkf.com.ar · cooperativalehmann.coop (PDF calendario 2026) · consignatarias.com.ar · instagram.com/estancialalucila · rosgan.com.ar · todolecheria.com.ar · FARER 2026 · exporural.com.ar

Generado: 11/08/2026. Las fechas marcadas “estimado” provienen de recurrencias declaradas o están publicadas a confirmar, y deben validarse con la firma antes de asistir.
