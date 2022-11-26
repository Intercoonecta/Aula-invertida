<p align="left">
<strong><a href="../Indice.md">Indice</a></strong>
|
<strong><a href="../Intro a R/R.md">R</a></strong>
|
<strong><a href="../Intro a Python/Python.md">Python</a></strong>
|
<strong><a href="../Intro a Jupyter/Jupyter.md">Jupyter</a></strong>
|
<strong><a href="../Intro a github/Github.md">Github</a></strong>
|
<strong><a href="../enlaces.md">Enlaces</a></strong>
</p>

<img     style="float: left;" src="OHWe.png" width=15% height=15%>

# Ayuda de funciones y paquetes

Podemos acceder al sistema de ayuda de R mediante "?" seguido del nombre de la función que nos interesa o con el comando `help()`. Probemos esto con algunas de las funciones que hemos utilizado hasta el momento:
```r
> ?ls
> help("rnorm")
> help(par)
```

Cuando desconocemos el nombre de la función o buscamos un tema en particular, por ejemplo nos interesa algo sobre modelos lineales, podemos usar `??"linear models"` o bien la función `help.search()`:
```r
> help.search("linear models")
```

<details>
<summary>Ejercicio: busca ayuda sobre la función 'hist'. Dale click para ver la solución</summary>
 ```r
> help("hist")
```
</details>

A partir de la pestaña Help en RStudio  también podemos acceder a la ayuda compilada en html, a los diferentes manuales de R en formato pdf que se crearon durante la instalación, a los archivos en línea de la lista de correo de ayuda de R, etc.
