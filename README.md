# SGSA AQUAA v3.0

Aplicación web para registrar solicitudes de materiales e insumos de AQUAA.

## Cambios principales de la versión 3.0

- Se eliminó definitivamente la funcionalidad de adjuntar archivos.
- Se corrigió la estructura semántica del formulario.
- Se mejoró la accesibilidad mediante etiquetas ARIA, navegación por teclado y estados de error.
- Se evitó el envío duplicado de solicitudes.
- Se reforzó el manejo de errores y tiempos de espera.
- Se reorganizó y documentó la lógica de JavaScript.
- Se añadió el código del material al envío para preparar el modelo relacional.
- Se eliminó la dependencia del favicon externo.
- Se agregó `noindex` porque se trata de una aplicación interna.
- Se preparó un backend v3.0 sin permisos de Google Drive.

## Estructura

```text
index.html
css/
  styles.css
js/
  app.js
  catalogos.js
img/
  LOGO-AQUAA.png
  favicon.svg
  logo-institucional-aquaa.png
backend/
  GoogleAppsScript.gs
```

## Publicación en GitHub Pages

Sube a la raíz del repositorio:

- `index.html`
- `css/`
- `js/`
- `img/`
- `README.md`

La carpeta `backend/` puede conservarse en el repositorio como código fuente, pero GitHub Pages no la ejecuta.

## Google Sheets

### Hoja `Solicitudes`

| Columna | Encabezado |
|---|---|
| A | Folio |
| B | Fecha |
| C | Hora |
| D | Nombre |
| E | Área |
| F | Correo |
| G | Sucursal |
| H | Observaciones |
| I | Estatus |

### Hoja `Detalle`

| Columna | Encabezado |
|---|---|
| A | Folio |
| B | Código |
| C | Categoría |
| D | Material |
| E | Cantidad |
| F | Unidad |

> La columna `Código` es nueva en v3.0 y permitirá relacionar posteriormente el detalle con el catálogo de materiales.

## Actualización de Google Apps Script

1. Abre el archivo de Google Sheets.
2. Ve a **Extensiones → Apps Script**.
3. Sustituye el código por `backend/GoogleAppsScript.gs`.
4. Guarda los cambios.
5. Ve a **Implementar → Administrar implementaciones**.
6. Edita la implementación, selecciona **Nueva versión** y vuelve a implementar.
7. Comprueba que la URL de implementación coincida con `CONFIG.appsScriptUrl` en `js/app.js`.

## Catálogo actual

- Limpieza: 68 materiales.
- Papelería: 66 materiales.
- Ferretería: 82 materiales.
- Equipo de Protección Personal: 62 materiales.
- Total documentado: 278 materiales.

## Nota de seguridad

Esta versión no utiliza `DriveApp`, no recibe archivos y no requiere permisos de Google Drive. El endpoint de Apps Script sigue siendo público para permitir solicitudes desde GitHub Pages; las siguientes fases deberán considerar controles adicionales contra abuso automatizado.
