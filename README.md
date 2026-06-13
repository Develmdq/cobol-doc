<div align="center">

##  COBOL-DOC

**Generador de documentación para proyectos COBOL**   
*Lee los comentarios del código fuente y genera un sitio navegable, sin necesidad de instalar nada.*

[![GitHub Pages](https://img.shields.io/badge/demo-live-58a6ff?style=flat-square&logo=github)](https://develmdq.github.io/cobol-doc/)
![License](https://img.shields.io/badge/license-MIT-3fb950?style=flat-square)

</div>

---

## ¿Comó funciona?

App web que escanea archivos fuente y genera documentación en formato HTML y/o PDF.

---

## Uso rápido

1. Abrir `index.html` en cualquier navegador o pinchar [aquí](https://develmdq.github.io/cobol-doc/).
2. Ingresar el nombre del proyecto.
3. Ingresa URL del repositorio en GITHUB.
4. Arrastrar los archivos fuente.
5. Clic en **Generar documentación**.
6. **Exportar HTML**.
   **Exportar PDF**.

---

## Formatos soportados

`.cbl` `.cob` `.cpy` `.jcl` `.sql` `.txt` `.rex` `.rexx`

---

### Reglas principales

**El input "Nombre del proyecto"**
Se renderizará como h1 como título de la documentación del proyecto.

**El input "URL del repositorio (GitHub)"**
Se vincula a un botón en el HTML final para acceder al repositorio documentado.

**Solo se documenta lo que está dentro de un bloque `*>**`.**
Todo lo que esté fuera — comentarios técnicos, notas de código — es ignorado por el generador.
Cada bloque `*>**` genera una sección en el HTML.

```cobol
      *>**
      aquí va la documentación
      *>**
```
---

### Marcas disponibles dentro del bloque

| Marca | Resultado |
|-------|-----------|
| `*= Texto` | **Título H2** — color azul, aparece en el índice lateral |
| `*-* Texto` | **Subtítulo H3** — color violeta, aparece en el índice lateral |
| `* @directiva: valor` | Render especial según la directiva (ver abajo) |
| `* Texto libre` | Párrafo de documentación |
| `*-` | Separador horizontal |
| `*` | Línea en blanco |

---

### Directivas `@`

Las directivas se escriben con `* @nombre: valor`. El símbolo `@` no se renderiza.

#### Metadatos

```cobol
      *>**
      *= MI PROGRAMA
      * @autor:        Nombre Apellido
      * @fecha:        2026-01-15
      * @version:      1.0
      * @licencia:     MIT
      * @modificacion: 2026-05-28
      *>**
```

#### Entradas, salidas y DB2

```cobol
      * @input:  DDNAME_ENTRADA  Descripción del dataset de entrada
      * @output: DDNAME_SALIDA   Descripción del dataset de salida
      * @db2:    NOMBRE_TABLA    Descripción de la tabla o recurso DB2
```

#### Historial de cambios

```cobol
      * @change: 2026-01-15 AUTOR_1 Versión inicial
      * @change: 2026-03-10 AUTOR_2 Agrega validación de FILE STATUS
```

Cada línea `@change` genera una fila en la tabla de historial. Formato: `fecha autor descripción`.

#### Referencias a rutinas

```cobol
      * @see:  NOMBRE_RUTINA https://github.com/usuario/repositorio
      * @uses: NOMBRE_RUTINA
```

`@see` genera un badge con link al repositorio de la rutina referenciada.
`@uses` genera un badge sin link — útil cuando la rutina no tiene repositorio publicado.

Esto permite documentar dependencias entre programas sin repetir la documentación de cada rutina en cada programa que la utiliza.

---

### Ejemplo completo

```cobol
      *>**
      *= REPORTE MENSUAL DE VENTAS
      *-
      * @autor:        _nombre_autor_
      * @fecha:        2026-01-15
      * @version:      1.0
      * @licencia:     Uso interno
      * @modificacion: 2026-05-28
      *-
      * @input:  VENTAS   Dataset de ventas del período
      * @input:  PARAMS   Parámetros de ejecución
      * @output: REPORTE  Archivo de salida paginado
      * @db2:    CLIENTES Tabla de clientes — JOIN con VENTAS
      *-
      * Genera reporte mensual agrupado por región y vendedor.
      * Aplica doble corte de control con totalizadores y promedios.
      *-
      * @change: 2026-01-15 _autor_1_ Versión inicial
      * @change: 2026-05-28 _autor_2_ Agrega totales por región
      *-
      * @see: _NOMBRE_RUTINA_ https://github.com/_usuario_/_nombre_proyecto_
      *>**

      *>**
      *-* NOTA SOBRE EL USO DE GO TO
      * Su uso está segmentado exclusivamente para manejar el flujo
      * de ejecución dentro del estado de error.
      * No interfiere en el flujo de la lógica de negocio.
      *>**
```

---

## Publicación en GitHub Pages

```
1. Crear el repositorio en GitHub
2. Renombrar el archivo exportado como index.html
3. Settings → Pages → Branch: main → / (root)
4. En aproximadamente 60 segundos el sitio está disponible
```

---


