<p align="left">
<strong><a href="../Indice.html">Indice</a></strong>
|
<strong><a href="../Intro a R/R.html">R</a></strong>
|
<strong><a href="../Intro a Python/Python.html">Python</a></strong>
|
<strong><a href="../Intro a Jupyter/Jupyter.html">Jupyter</a></strong>
|
<strong><a href="../Intro a github/Github.html">Github</a></strong>
|
<strong><a href="../enlaces.html">Enlaces</a></strong>
</p>

<img     style="float: left;" src="OHWe.png" width=15% height=15%>

# Importar datos externos
En los primeros ejemplos vimos la manera de introducir datos y crear objetos a partir del teclado, pero lo mas usual es que tengamos nuestra información en alguna hoja de cálculo o base de datos. 

## Desde el portapapeles
Cuando la cantidad de datos es pequeña y su formato sencillo, podemos pasarlos directamente del archivo a la consola de R por medio del portapapeles. Para ello primero copiamos los datos al portapapeles y después escribimos en la consola la instrucción:
```r
> x <- read.delim("clipboard")
```

## Mediante read.table()
Cuando el tamaño de los datos es importante, es preferible usar otro método para leerlos en R. Los archivos de Excel y de Access pueden ser importados mediante funciones especiales, sin embargo lo más sencillo es exportar nuestros datos en formato ascii, puesto que todas las hojas de cálculo y manejadores de bases de datos tienen esta capacidad. Se sugiere salvar los datos en un archivo de texto, con nombres de columnas que empiecen por una letra y sin espacios (si se desean nombres compuestos se puede usar un guión bajo) y usando tabuladores como separadores de columnas (aunque R puede importar datos sin nombres de columnas y separados por espacios, comas, etc.). 

Uno de los comandos de importación de datos externos que más utilizaremos es `read.table()` y su sintaxis es la siguiente:
```r
> x <- read.table("ruta/archivo", header, sep)
```
Del lado izquierdo del assignment, `x` corresponde al objeto que contendrá los datos del archivo importado. Del lado derecho, `ruta` se refiere a un directorio, por ejemplo `G:/datos` (**nótese la diagonal (/) usada**) y `archivo` al nombre -incluyendo la extension (.txt, .dat)- del archivo externo que contiene los datos. Los argumentos `header` y `sep` indican si el archivo incluye (`TRUE`) o no (`FALSE`) nombres de columnas y el separador de las mismas. Por defecto, este último es un número variable de espacios, pero puede ser también un solo espacio  (`sep = " "`), un tabulador (`sep = "\t"`), una coma (`sep = ","`) o punto y coma (`sep = ";"`). 

Una vez importados los datos, estarán disponibles para ser analizados dentro de R. Es importante señalar que el archivo original permanece sin cambios y que los datos solo están disponibles mientras la sesión actual de R se mantenga abierta. Si en una sesión posterior deseamos usar los mismos datos debemos importarlos nuevamente, a menos que hayamos guardado el workspace y se haya restaurado en la nueva sesión. 

Una sesión formal de R requiere que definamos nuestro directorio de trabajo ("working directory", wd). Eso simplificará mucho la importación y exportación de datos y figuras, ademas de que nos ayudara a mantener organizado nuestro trabajo. Para conocer el directorio de trabajo actual usamos el comando `getwd()`, mientras que definimos uno diferente mediante `setwd()`, por ejemplo:
```r
> setwd('G:/analisis')
```
De esta manera, la sintaxis  puede simplificar son necesidad de escribir toda la ruta al archivo:
```r
> a00 <- read.table("./datos/archivo_00.txt", header = TRUE, sep = "\t")
```
El "." antes de la diagonal inicial sirve para indicar que `datos` es un subdirectorio de `G:/analisis`. 

## Desde archivos Excel

### Con paquete `readxl`
Para importar este tipo de archivos es necesario el uso de paquetes adicionales. Actualmente el más sencillo de instalar y utilizar es `readxl`, el cual permite importar archivos tanto .xls como .xlsx. 

Por ejemplo
```r
> library(readxl)
> datos <- read_excel("./datos/archivo_04.xls", sheet = 1)
```
En este caso `sheet = 1` indica que nos interesa la primera hoja del archivo, la cual también se puede indicar por nombre: `sheet = "A"`.
Se recomienda ver la ayuda de la función `read_excel()` para mayores detalles.

### Con `RODBC`
Otro paquete interesante para este propósito es `RODBC`. La secuencia completa de pasos para importar un archivo de Excel, requiere (1) cargar el paquete, (2) establecer una conexión al archivo, (3) leer los nombres de las hojas del archivo Excel y (4) importar la hoja que nos interesa. 

La sintaxis es la siguiente:
```r
> library(RODBC)
> con <- odbcConnectExcel("./datos/archivo_04.xls")
> sqlTables(con)
> a04pA <- sqlFetch(con, "A_1962")
```
En este ejemplo, `con` es unicamente la conexión al archivo `archivo_04.xls` y es a través de ella que consultamos los nombres de las hojas Excel (`sqlTables(con)`) e importamos aquella que nos interesa (`sqlFetch(con, "A_1962")`). Adicionalmente, si ya no se van a importar mas datos se cierra la conexión y se remueve el paquete de la memoria:
```r
> closeAllConnections()
> detach("package:RODBC")
```
El procedimiento para importar datos de un archivo Access mediante el paquete `RODBC` es equivalente, solamente se requiere sustituir la función que establece la conexión al archivo correspondiente (`odbcConnectAccess()`). Mas detalles acerca de la importación de estos y otros tipos de archivos se pueden consultar en el manual R Data Import/Export (R-data.pdf) que se encuentra bajo la carpeta doc/manual de la instalación de R.
