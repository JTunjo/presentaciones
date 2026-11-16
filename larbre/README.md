# Diagnóstico Tunjo — puesta en marcha

## 1. Hoja y carpeta
1. Crea una Google Sheet vacía (las pestañas `Respuestas` y `Detalle` se crean solas). Copia su ID de la URL: `docs.google.com/spreadsheets/d/<ID>/edit`.
2. Crea una carpeta privada en Drive para las fotos. Copia su ID: `drive.google.com/drive/folders/<ID>`.

## 2. Apps Script
1. En la hoja: **Extensiones → Apps Script**. Pega `Code.gs`.
2. En `CONFIG` pon `SHEET_ID`, `FOLDER_ID` y un `TOKEN` propio.
3. **Implementar → Nueva implementación → Aplicación web**
   - Ejecutar como: **Yo**
   - Quién tiene acceso: **Cualquier usuario**
4. Autoriza los permisos y copia la URL que termina en `/exec`.
5. Prueba: abre esa URL en el navegador; debe responder `{"ok":true,...}`.

Si cambias `Code.gs` después, usa **Gestionar implementaciones → Editar → Nueva versión**, así la URL no cambia.

## 3. Formulario
En `index.html`, bloque `CONFIG` al inicio:
- `endpoint`: la URL `/exec`
- `token`: el mismo `TOKEN` de `Code.gs`
- `leads`: código → nombre visible (ya está `LAAC: "L’Arbre à Café"`)

Las reglas de la pantalla final están en `PHOTO_RULES` y `NDA_RULES`, en el mismo bloque.

## 4. GitHub Pages
Sube `index.html` al repo (por ejemplo `presentaciones/diagnostico/index.html`). Enlace para el lead:

`https://jtunjo.github.io/presentaciones/diagnostico/?lead=LAAC`

## Notas
- Cada reenvío agrega filas nuevas con `version` +1; no sobrescribe.
- Si el envío falla, el lead puede descargar una copia JSON de sus respuestas.
- El token evita envíos casuales, pero es visible en el HTML: no es una contraseña.
