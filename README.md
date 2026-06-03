<div align="center">

```
▊ COBOLDoc
```

**Generador de documentación para proyectos COBOL Mainframe**  
*Lee los comentarios del fuente. Genera un sitio navegable. Sin instalar nada.*

[![GitHub Pages](https://img.shields.io/badge/demo-live-58a6ff?style=flat-square&logo=github)](https://develmdq.github.io/cobol-doc)
[![License](https://img.shields.io/badge/license-MIT-3fb950?style=flat-square)](LICENSE)

</div>

---

## ¿Qué es?

Un único archivo HTML — doble clic, abre en el navegador — que procesa archivos fuente COBOL y genera documentación navegable lista para publicar en **GitHub Pages**.

No requiere Node.js, Python, ni ninguna dependencia externa.

---

## Uso rápido

1. Abrir `cobol-doc.html` en cualquier navegador
2. Ingresar el nombre del proyecto
3. Arrastrar los archivos fuente
4. Clic en **Generar documentación**
5. **Exportar HTML** → `index.html` listo para GitHub Pages  
   **Exportar PDF** → versión imprimible

---

## Formatos soportados

`.cbl` `.cob` `.cpy` `.jcl` `.sql` `.txt`

---

## Cómo documentar el código fuente

### La regla principal

**Solo se documenta lo que está dentro de un bloque `*>**`.**  
Todo lo que esté fuera — comentarios técnicos, notas de código — es ignorado por el generador.

```cobol
      *>**
      aquí va la documentación
      *>**
```

Un archivo puede tener tantos bloques como sea necesario. Cada bloque `*>**` genera una sección en el HTML.

---

### Marcas disponibles dentro del bloque

| Marca | Resultado |
|-------|-----------|
| `*= Texto` | **Título H1** — color azul, aparece en el índice lateral |
| `*-* Texto` | **Subtítulo H2** — color violeta, aparece en el índice lateral |
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

El primer token después de la directiva es el DDname o nombre de tabla. El resto es la descripción.

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

<div align="center">
<sub>COBOLDoc — documentación generada desde comentarios de código fuente</sub>
</div>
