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


# Operaciones básicas

Con R podemos realizar cualquier operación aritmética usando los operadores habituales para sumas (+), restas (-), multiplicaciones (\*), divisiones (/) y potencias (^). Todos los ejemplos que siguen se pueden teclear en la consola, aunque de preferencia hay que hacerlo en un script donde podemos añadir comentarios con el símbolo `#`, ya sea en la misma línea de la operación o función, o en una línea aparte.

**Recuerda que el símbolo `>` es el prompt y no debe teclearse**

```r
> 3+6 # suma
[1] 9 
> 8*9 # multiplicación
[1] 72
> 10-8 # resta
[1] 2
> 5/2 # cociente
[1] 2.5
> 4^2 # potencia
[1] 16
```
En R operan las reglas de precedencia normales, es decir que la multiplicación y la división se evalúan antes que la suma y la resta, por lo que podemos usar paréntesis para  obtener un resultado deseado, por ejemplo:

```r
> 5 + 2 * 3
[1] 11
# los paréntesis garantizan que la suma se evalua primero
> (5 + 2) * 3
[1] 21
```

Otras operaciones frecuentes  hacen uso de funciones dedicadas cuyos nombres son bastante intuitivos y no cambian independientemente del lenguaje en el que R se haya instalado. Por ejemplo, el logaritmo natural de 100 se obtiene con la función `log()`.

```r
> log(100) # logaritmo natural de 100 (base e)
[1] 4.60517
```
La sintaxis formal sería  `log(x = 100)`, donde `x` es el único **argumento** que la función requiere para dar un resultado. Esta función puede usarse para obtener logaritmos con diferentes bases, por ejemplo `log(x = 100, base = 10)` (o bien `log(100, 10)`) produce el mismo resultado que `log10(100)`:

```r
> log(100, 10)
[1] 2
> log10(100) # logaritmo base 10
[1] 2
```
Otros ejemplos de funciones de este tipo podrían ser la exponencial ($e^x$) y la raiz cuadrada:
```r
> exp(2)
[1] 7.389056
> sqrt(16)
[1] 4
```
También se pueden calcular funciones trigonométricas usando los nombres abreviados en inglés, por ejemplo para el seno de un ángulo `x` : `sin(x)`. 

<details>
<summary>Ejercicio: calcula el seno y coseno de 90. **Dale click para ver la solución**</summary>
 ```r
# las funciones trigonométricas en R esperan los ángulos en radianes
> sin(90*pi/180) 
[1] 1
> cos(90*pi/180)
[1] 6.123032e-17
```
</details>
