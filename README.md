<div align="center">

```
▊ COBOLDoc
```

**Generador de documentación para proyectos COBOL Mainframe**  
*Lee tus comentarios. Genera un sitio. Sin instalar nada.*

[![GitHub Pages](https://img.shields.io/badge/demo-live-58a6ff?style=flat-square&logo=github)](https://develmdq.github.io/cobol-doc)
[![License](https://img.shields.io/badge/license-MIT-3fb950?style=flat-square)](LICENSE)
[![COBOL](https://img.shields.io/badge/COBOL-Mainframe-d29922?style=flat-square)](https://github.com/Develmdq)

</div>

---

## ¿Qué es?

Un único archivo `HTML` — doble clic, abre en el navegador — que lee tus archivos fuente COBOL y genera documentación navegable lista para publicar en **GitHub Pages**.

No requiere Node.js, Python, ni ninguna dependencia externa.

---

## Formatos soportados

| Extensión | Tipo | Comentarios que extrae |
|-----------|------|------------------------|
| `.cbl` `.cob` | COBOL | Bloques `*>` (COBOLDoc) y bloques `*---*` columna 7 |
| `.jcl` | JCL | Líneas `//*` agrupadas por paso |
| `.cpy` | Copybook | Igual que COBOL |
| `.sql` | SQL | Comentarios `--` y `/* */` |

---

## Uso

**1. Abrí `cobol-doc.html`** en cualquier navegador

**2. Arrastrá tus archivos** fuente en el orden que querés que aparezcan

**3. Hacé clic en Generar documentación**

**4. Exportá** con el botón **Exportar HTML** → obtenés un `index.html` listo para GitHub Pages

---

## Directivas en el código fuente

Dentro de tus comentarios `*>` podés usar estas directivas:

```cobol
*> @see  RUTERRBA https://github.com/Develmdq/Manejo-Errores-BATCH
*> @uses SUBPGM01
```

| Directiva | Resultado |
|-----------|-----------|
| `@see NOMBRE URL` | Badge con link externo — apunta al repo de la rutina |
| `@uses NOMBRE` | Badge de referencia sin link |

Útil para documentar dependencias entre programas sin repetir la documentación de cada rutina en cada main que la usa.

---

## Formato de comentarios soportados

**Encabezado del programa** — bloque `*>` (COBOLDoc):

```cobol
      *>**
      *> <h2>REPORTE DOBLE CORTE DE CONTROL</h2>
      *> @author MARCET EDUARDO
      *> @see RUTERRBA https://github.com/Develmdq/Manejo-Errores-BATCH
      *> <b>FUNCION:</b>
      *>   Procesa datos con doble corte de control desde DB2.
      *>**
```

**Notas en el cuerpo** — bloques `*---*` columna 7:

```cobol
      *----------------------------------------------------------------*
      * NOTA SOBRE EL USO DE GO TO:                                    *
      * Su uso esta segmentado exclusivamente para manejar el flujo    *
      * de ejecucion dentro del estado de error.                       *
      *----------------------------------------------------------------*
```

**Comentarios JCL** — líneas `//*`:

```jcl
//* -----------------------------------------------
//* PASO 1: COMPILACION DEL PROGRAMA PRINCIPAL
//* -----------------------------------------------
//COMPILE EXEC PGM=IGYCRCTL
```

---

## Demo en vivo

👉 **[develmdq.github.io/cobol-doc](https://develmdq.github.io/cobol-doc)**

---

## Publicar en GitHub Pages

```
1. Creá el repo en GitHub
2. Subí cobol-doc.html renombrado como index.html
3. Settings → Pages → Branch: main → / (root)
4. En ~60 segundos está online
```

---

## Parte de

Este generador forma parte de un ecosistema de proyectos COBOL Mainframe:

| Proyecto | Descripción |
|----------|-------------|
| [RPTCLI01](https://github.com/Develmdq) | Reporte batch con doble corte de control y DB2 |
| [Manejo-Errores-BATCH](https://github.com/Develmdq/Manejo-Errores-BATCH) | Rutina centralizada de manejo de errores |

---

<div align="center">
<sub>Hecho con criterio mainframe — Eduardo Marcet · <a href="https://github.com/Develmdq">@Develmdq</a></sub>
</div>
