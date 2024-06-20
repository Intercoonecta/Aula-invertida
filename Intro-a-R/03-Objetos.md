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

<img     style="float: left;" src="OHWe.png" width=15% height=15%>

# Objetos en R

R opera a través de estructuras de datos que tienen nombre. Pueden ser de diferentes tipos, dependiendo de su estructura y de los datos que contengan, así podemos distinguir entre vectores, matrices, data frames y listas, principalmente (aunque las funciones también son objetos). 

Conocer el tipo de objeto es importante porque determina en gran medida las operaciones que podemos efectuar con ellos.

Para ilustrar las diferentes estructuras de datos utilizaremos el operador de asignación (`assignment`): `<-`, el cual permite asignar un valor o una colección ordenada de valores a un objeto determinado.

Por ejemplo, la instrucción
```r
> b <- 5
```
asigna el valor `5` al objeto denominado `b`. Ese vector (de longitud uno) estará disponible para operaciones subsecuentes:
```r
> 10*b
[1] 50
> sqrt(b)
[1] 2.236068
```
##  Vectores

Los vectores son el tipo de estructura más simple en R. Asignemos por ejemplo una serie de números del 1 al 6 a un objeto que llamaremos `w`. Para ello utilizamos la instrucción:
```r
> w <- 1:6
```
Para verificar el contenido de `w` simplemente escribimos su nombre:
```r
> w
[1] 1 2 3 4 5 6
```
Como se puede inferir del ejemplo anterior, ":" sirve para crear una secuencia de números de uno en uno. Si deseamos crear secuencias con intervalos diferentes, por ejemplo cada 0.5 unidades, podemos usar la función `seq()`:
```r
> seq(1, 6, 0.5)
[1] 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0 5.5 6.0
```
En este ejemplo indicamos el inicio (`from = 1`) y el final (`to = 6`) de la secuencia, así como el incremento (`by = 0.5`). Al inicio de la secuencia anterior aparece `[1]`, lo que nos indica que R desplegó el resultado a partir del primer valor del vector. Si en un renglón hubiera espacio para únicamente 20 números, una secuencia que ocupara dos renglones comenzaría en `[1]` en el primer renglón y en `[21]` en el segundo.

Regresando a nuestro ejemplo, `w` es un vector numérico, pero también podemos tener vectores de caracteres:
```r
> x <- c("a", "a", "a", "b", "b", "b")
> x
[1] "a" "a" "a" "b" "b" "b"
```

En este ejemplo, usamos la instrucción combine `c()` para combinar las letras en un solo objeto. De manera similar, el vector de nuestro primer ejemplo puede crearse también usando la instrucción: `w <- c(1, 2, 3, 4, 5, 6)`. 

En el caso de la creación del vector `x` usamos comillas para indicar que se trata de texto y no de objetos ya existentes. Imaginemos que en algún momento de la sesión se hicieron las asignaciones `a <- 2.5` y `b <- 3.6` y después lo olvidamos. Si en un momento posterior de la misma sesión deseáramos crear el vector de caracteres del ejemplo anterior pero olvidásemos usar las comillas, el resultado sería totalmente diferente:

```r
> xx <- c(a, a, a, b, b, b)
> xx
[1] 2.5 2.5 2.5 3.6 3.6 3.6
```

Ademas de los vectores numéricos y de caracteres que acabamos de ejemplificar, también hay vectores lógicos que resultan de la evaluación de expresiones:

```r
> ww <- w > 4
> ww
[1] FALSE FALSE FALSE FALSE TRUE TRUE
```

Este ultimo tipo de vector es muy útil para indexar otros vectores, pues nos permite, por ejemplo, extraer elementos específicos que cumplen con cierta condición (en este caso, aquellos que son mayores que 4):

```r
> w[ww]
[1] 5 6
```

## Matrices

El siguiente tipo de objeto que nos interesa es la matriz:
```r
> y <- matrix(1:20, ncol = 4)
> y
     [,1] [,2] [,3] [,4]
[1,]    1    6   11   16
[2,]    2    7   12   17
[3,]    3    8   13   18
[4,]    4    9   14   19
[5,]    5   10   15   20
```

Nótese como hemos indicado el número de columnas que queríamos con el argumento `ncol`. También podemos precisar como queremos que los datos sean ordenados en la matriz al incluir el argumento `byrow`, que instruye a la función `matrix()` a llenar primero los renglones:

```r
> matrix(1:20, byrow = TRUE, ncol = 4)
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12
[4,]   13   14   15   16
[5,]   17   18   19   20
```

Incluso podemos asignar nombres a las columnas y renglones de la matriz, para lo cual añadimos el argumento `dimnames`:

```r
> y <- matrix(1:20, byrow = TRUE, ncol = 4, dimnames = list(
        paste("r", 1:5, sep = ""), paste("c", 1:4, sep = ".")))
> y
   c.1 c.2 c.3 c.4
r1   1   2   3   4
r2   5   6   7   8
r3   9  10  11  12
r4  13  14  15  16
r5  17  18  19  20 
```

El valor de `dimnames` en la función anterior utiliza otras funciones (`list()` y `paste()`) con sus respectivos argumentos. Para comprender su propósito podemos evaluarlas de  manera independiente. Para ello, las seleccionamos con el cursor, cuidando de incluir los paréntesis necesarios en la selección, y pulsamos **Run**   o `Ctrl+Enter`.

<details>
<summary>Ejercicio: selecciona la segunda función `paste()` del código anterior y evaluala en la consola para comprender su finalidad. **Dale click para ver la solución**</summary>
     
 ```r
> paste("c", 1:4, sep = ".")
[1] "c.1" "c.2" "c.3" "c.4"
```
     
</details>

## Data frames

Una característica que comparten los vectores y las matrices es que solo pueden contener el mismo tipo de valores (numéricos, caracteres o lógicos). En muchas ocasiones, nuestros datos contienen una mezcla de variables numéricas y factoriales. Esta información puede manejarse por medio de un data frame, muy similar a la matriz pero que puede contener mas de un tipo de datos:

```r
> z <- data.frame(x, w)
> z
  x w
1 a 1
2 a 2
3 a 3
4 b 4
5 b 5
6 b 6
```

## Listas

Una lista pude combinar cualquier tipo de objetos, incluyendo otras listas.
```r
> Z <- list(V.w = 2*w, V.x = x, M.y = log(y))
> Z
$V.w
[1] 2 4 6 8 10 12

$V.x
[1] "a" "a" "a" "b" "b" "b"

$M.y
        c.1       c.2      c.3      c.4
r1 0.000000 0.6931472 1.098612 1.386294
r2 1.609438 1.7917595 1.945910 2.079442
r3 2.197225 2.3025851 2.397895 2.484907
r4 2.564949 2.6390573 2.708050 2.772589
r5 2.833213 2.8903718 2.944439 2.995732
```

Es importante mencionar que R es sensible al uso de mayúsculas/minúsculas, de tal forma que nuestros objetos z y Z son diferentes.
