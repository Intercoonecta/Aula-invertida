<p align="left">
<strong><a href="../Indice.md">Indice</a></strong>
|
<strong><a href="../Intro-a-R/R.md">R</a></strong>
|
<strong><a href="../Intro-a-Python/Python.md">Python</a></strong>
|
<strong><a href="../Intro-a-Jupyter/Jupyter.md">Jupyter</a></strong>
|
<strong><a href="../Intro-a-Markdown/Markdown.md">Markdown</a></strong>
|
<strong><a href="../Intro-a-github/Github.md">Git y GitHub</a></strong>
|
<strong><a href="../enlaces.md">Enlaces</a></strong>
</p>

<img     style="float: left;" src="OHWe.png" width="100"> 

# Breve introducción a Markdown
**Autor:** Emilio Mayorga, Jorge Cornejo, Marian Peña


[Markdown](https://tutorialmarkdown.com/markdown) es un lenguage de marcado en texto plano fácil de aprender. Es como una versión mucho más sencilla de HTML. Markdown permite escribir texto formateado o incluir enlaces, listas, encabezados de secciones, tablas, ecuaciones, imágenes u otro contenido multimedia. En Markdown agregas símbolos de su sintaxis para indicar el tipo de formateo o elementos a incluir. Por ejemplo, rodeando el texto con dos caracteres estrellas lo formatea en negrilla: `**negrilla**` produce **negrilla**. Símbolos numerales al comienzo de una línea convierten la línea en encabezado: `# encabazado de primer nivel`, `## encabazado de segundo nivel`, etc. 

Documentos escritos en Markdown pueden ser leídos directamente sin que los símbolos de marcado de Markdown dificulten la interpretación. Editores y sistemas que interpretan texto con Markdown convierten los símbolos de marcado a un documento formateado o "renderizado".

Aquí mostramos un pequeño texto que demuestra la capacidad de Markdown. **Primero mostramos el texto con el marcado de Markdown, donde el formateo no ha sido ejecutado:**


```
## Definir las variables x e y

Definimos las **variables** `x` e `y`, donde `y` es el [seno](https://es.wikipedia.org/wiki/Seno_(trigonometria)) de `x`:
```

\`\`\`   
y = seno(x)   
\`\`\`   


```
Si calculamos esta función, podemos compilar una tabla con valores de `x` e `y`, con:
- Una hilera de cabecera
- Tres hileras de datos

*Aquí la tabla formateada:*

| x | y |
|---|---|
|0.0|0.0|
|0.1|0.09983342|
|0.2|0.19866933|

```

**Ahora el mismo texto, formateado (renderizado):**

## Definir las variables x e y

Definimos las **variables** `x` e `y`, donde `y` es el [seno](https://es.wikipedia.org/wiki/Seno_(trigonometria)) de `x`:

```
y = seno(x)
```

Si calculamos esta función, podemos compilar una tabla con valores de `x` e `y`, con:
- Una hilera de cabecera
- Tres hileras de datos

*Aquí la tabla formateada:*

| x | y |
|---|---|
|0.0|0.0|
|0.1|0.09983342|
|0.2|0.19866933|

------------------------

A causa de su sintaxis simple y fácil de recordar y aplicar, Markdown es utilizado ampliamente en herramientas de ciencias de datos y para crear documentación técnica. Algunos sistemas permiten crear el contenido de sitios web usando Markdown.

Pare aprender más sobre Markdown, [aquí](https://datosgobar.github.io/portal-andino/markdown-guide/) puedes encontrar una guía breve pero completa. [Este Tutorial Markdown](https://tutorialmarkdown.com/markdown) incluye más explicaciones y ejemplos. Ahí también econtrarás un [editor en línea](https://editormarkdown.com/) donde puedes practicar escribir con códigos Markdown y ver los resultados inmediatamente.

# RMarkdown
Si trabajas en R puedes utilizar R y Markdown en el mismo fichero. Un archivo de RMarkdown (extensión Rmd) tiene 2 lenguajes incluidos: **R** y **Markdown**.  Las **secciones de código R** están rodeadas de 3 tics y `{r LABEL}`. Estas secciones son evaluadas por R, generando una salida de texto o un gráfico. Para ejecutar las secciones de código R  se deben enviar a la consola. ¿Cómo se hace eso?

Hay varias formas de hacerlo: 

1. Copiar y pegar los comandos en la consola.
1. Seleccionar la línea (o poner el curso en ella) y hacer clic en 'Run'. Esto está 
disponible desde:
    a. la barra arriba del archivo (flecha verde).
    b. la barra menú: Code > Run Selected Line(s).
    c. combinación de teclas: control-enter en Windows o command-enter en macOS.
1. Clic en la flecha verde en el lado superior derecho de su sección de código.
Hay muchas tablas de consejos [cheatsheets](https://github.com/adam-p/markdown-here/wiki/Markdown-Here-Cheatsheet) que te puede utilizar para obtener ayuda, una de esas está incluida en RStudio: para abrirla vaya a Help > Markdown Quick Reference.
Ha de tener en cuenta que Markdown tiene diferentes 'flavors' o versiones según la aplicación con pequeñas diferencias. GFM o Github flavored markdown se obtiene desde Rstudio utilizando la opción de exportar a github en lugar de hmtl (ver https://github.com/A1arcon/R_Actuarial/blob/main/R%20Markdown/1.%20Introducci%C3%B3n%20a%20R%20Markdown/GitHub/R-Markdown---GitHub.md).
