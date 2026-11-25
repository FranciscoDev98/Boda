# Invitación de boda · Aura & Francisco

Página estática (HTML + JavaScript, sin servidor). Cada invitado recibe un enlace con su
código y la invitación muestra su nombre en el sobre y en "Confirma tu asistencia".

## Qué hay en la carpeta

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La invitación completa (sobre, música, cuenta regresiva, botones). |
| `invitados.json` | Lista de invitados: `código -> nombre y cupos`. Trae 3 de ejemplo. |
| `assets/portada.jpg` | Foto de la portada y de la carta del sobre. |
| `assets/beso.jpg`, `assets/anillo.jpg`, `assets/si.jpg`, `assets/atardecer.jpg` | Fotos que aparecen a lo largo de la invitación. |
| `assets/cancion.mp3` | Canción de fondo. |
| `assets/vista-previa.jpg` | Imagen que aparece al pegar el enlace en WhatsApp. |
| `herramientas/enlaces.html` | Generador de enlaces: convierte tu lista en `invitados.json` y te da el enlace de cada invitado. |
| `.nojekyll` | Le dice a GitHub Pages que publique los archivos tal cual. |

## Publicar en GitHub Pages

1. En github.com crea un repositorio nuevo, por ejemplo `boda` (público; GitHub Pages gratis lo exige).
2. Sube **todo el contenido de esta carpeta** a la raíz del repositorio
   (botón *Add file → Upload files*, o con git):

   ```bash
   git init
   git add .
   git commit -m "Invitación de boda"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/boda.git
   git push -u origin main
   ```
3. En el repositorio: **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   rama `main`, carpeta `/ (root)`, y **Save**.
4. En uno o dos minutos queda en `https://TU-USUARIO.github.io/boda/`.
5. Abre `index.html`, busca `og:image` y cambia `TU-USUARIO.github.io/TU-REPOSITORIO` por tu
   dirección real. Sin esto la invitación funciona igual; solo no saldría la imagen de vista
   previa en WhatsApp.

## Crear los enlaces de los invitados

1. Abre `https://TU-USUARIO.github.io/boda/herramientas/enlaces.html`
   (o el archivo directamente en tu computador).
2. Pega tu lista, un invitado por línea: `Nombre ; cupos ; teléfono (opcional)`.
   Puedes copiar las columnas desde Excel: también acepta tabulaciones.
3. Pulsa **Generar enlaces** y luego **Descargar invitados.json**.
4. Reemplaza el `invitados.json` del repositorio por el descargado y súbelo.
5. Envía a cada invitado su enlace (botón **WhatsApp** de cada fila, o el CSV).

Si más adelante agregas invitados, carga primero tu `invitados.json` actual en el paso 3 de la
herramienta: así se conservan los códigos que ya enviaste.

## Formas de enlace

| Enlace | Resultado |
|---|---|
| `…/boda/?i=k7p2m` | Busca el código en `invitados.json` (recomendada). |
| `…/boda/#k7p2m` | Igual que la anterior. |
| `…/boda/?para=Familia%20Pérez&cupos=3` | Nombre directo en el enlace, sin tocar la lista. |
| `…/boda/` | Invitación general, sin nombre. |

## Para tener en cuenta

- **Todo lo del repositorio es público**: la foto, la canción y `invitados.json` (nombres y cupos;
  los teléfonos nunca se guardan ahí).
- **Los cupos son informativos**: quien conozca el formato `?para=…&cupos=…` puede escribir otro
  número. La lista real es la tuya.
- **La música empieza al tocar el sobre**; los celulares no permiten que suene sola.
- **Probar en tu computador**: `invitados.json` solo se lee desde un servidor. En la carpeta
  ejecuta `python -m http.server 8000` (o `dotnet serve`) y abre `http://localhost:8000/?i=demo1`.
- **Cambiar una foto**: reemplaza el archivo en `assets/` por otro con el mismo nombre.
- **Cambiar fecha, hora o número de WhatsApp**: están al inicio del bloque `<script>` de
  `index.html`, en la sección CONFIGURACIÓN. Los textos visibles se editan en el mismo archivo.
