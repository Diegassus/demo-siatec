# SIATEC S.A.: sitio institucional (demo)

Demo navegable del sitio de **SIATEC S.A. · Servicio de ingeniería y auditorías técnicas**: inspecciones técnicas, ensayos no destructivos, cámara acústica y emisión acústica, en Argentina y países limítrofes.

Lo que falta definir aparece en el sitio como **[PENDIENTE]** (datos de la empresa) o **[A completar]** (contenido de servicios).

**Este repo tiene solo el sitio generado.** Las páginas se arman con el generador de `D:\Proyectos\Veatec\generador\`, con el comando `python build.py siatec`. Los cambios se hacen allá y se vuelve a generar.

## Cómo verlo

- **En local:** abrí `index.html` en el navegador.
- **Online:** en GitHub, entrá a *Settings → Pages* y elegí la rama `main` y la carpeta raíz (`/`).

## Mapa del sitio

| Página | Archivo |
|---|---|
| Inicio | `index.html` |
| Empresa | `empresa.html` |
| Servicios | `servicios.html` |
| ↳ Inspecciones técnicas (Res. 277/25 SE · API 653) | `inspecciones-tecnicas.html` |
| ↳ Ensayos no destructivos | `ensayos-no-destructivos.html` |
| ↳ Cámara acústica | `camara-acustica.html` |
| ↳ Emisión acústica | `emision-acustica.html` |
| Proyectos | `proyectos.html` |
| Contacto y cotización | `contacto.html` |

```
/
├── *.html
├── css/estilos.css           estilos (bloque "TEMA SIATEC" al final: colores, tipografías y composición)
├── js/main.js                menú móvil, preselección de servicio, aviso de formularios
├── js/proyectos.js           galería de proyectos y filtros desde data/proyectos.json
├── data/proyectos.json       lista editable de proyectos
├── img/marca/                logo, versión horizontal, isotipo, imagen para redes, ícono
├── img/fotos/                fotos de obra optimizadas (WebP)
├── img/clientes/             logos de clientes
├── favicon.svg
├── sitemap.xml · robots.txt
└── .htaccess                 HTTPS, compresión y caché (hosting Apache)
```

## Identidad visual (propuesta para validar)

**Colores (tomados del logo)**

| Uso | Color |
|---|---|
| Azul del isotipo | `#8EAEC4` |
| Gris del isotipo | `#CFD3D6` |
| Azul de acento (botones y detalles) | `#2E6A96` |
| Azul para enlaces sobre blanco | `#2A5F87` |
| Azul oscuro | `#1C3550` |
| Azul noche (barra superior, bandas) | `#13263A` |

**Tipografías:** Barlow Semi Condensed (títulos) y Source Sans 3 (texto), de Google Fonts.

**Logo**
- `img/marca/logo-siatec.png`: completo, con fondo transparente.
- `img/marca/logo-siatec-horizontal.webp`: isotipo + nombre, para el header.
- `favicon.svg` / `img/marca/isotipo-siatec.svg`: isotipo redibujado en plano, para el ícono y como motivo gráfico.

Los dos primeros salen de la imagen enviada (JPG). **Conviene pedir el logo original en vector (AI, EPS, PDF o SVG).**

## Cargar o quitar proyectos

Los trabajos de **Proyectos** y los tres de **Inicio** salen de `data/proyectos.json`. Para sumar uno, se agrega un bloque en la lista `proyectos`:

```json
{
  "titulo": "Inspección de tanque · Planta X",
  "servicios": ["inspecciones", "end"],
  "imagen": "img/proyectos/tanque-planta-x.jpg",
  "alt": "Inspector midiendo espesores en el techo del tanque",
  "destacado": false
}
```

- `servicios`: uno o más de `inspecciones`, `end`, `camara` y `ea`.
- `destacado: true`: aparece en Inicio (los tres primeros).

**Si se edita el JSON en este repo, hay que copiarlo también a `generador\datos\siatec\proyectos.json`.** Si no, la próxima vez que se genere el sitio se pisa.

## Pendiente del cliente

- **Logo en vector** y confirmación de los colores.
- **Dominio** (se asumió `siatecservicios.com.ar`) y hosting.
- **Formulario:** ¿las consultas llegan a comercial@ o a administracion@?
- **Inicio:** título y presentación definitivos. Hoy hay un texto provisorio.
- **Empresa:** historia, misión y visión.
- **Proyectos:** confirmar las fotos y si hay un caso destacado.
- **Ensayos no destructivos:** comentarios del cliente y descripción de Crawler Magnético.
- **Cámara acústica:** fotos propias, para el fondo y para cada aplicación.
- **Procesos y preguntas frecuentes** de los 4 servicios.

## Antes de publicar

1. **Generar con `demo_noindex=False`** (en `generador\sitios\siatec.py`).
2. **Formularios:** pasarlos a PHP con PHPMailer, al correo que se defina.
3. **Google:** registrar el sitio en Search Console y enviar `sitemap.xml`.
   - Perfil de Google Business propio. Comparte dirección y teléfono con otra empresa, así que hay que cuidar que el nombre y la categoría estén bien diferenciados.
