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
<strong><a href="../Intro-a-github/Github.md">Github</a></strong>
|
<strong><a href="../enlaces.md">Enlaces</a></strong>
</p>

<img     style="float: left;" src="OHWe.png" width="100"> 

# Breve introducción a Markdown
**Autor:** Emilio Mayorga


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
