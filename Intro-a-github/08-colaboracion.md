<p align="left">
<strong><a href="../Indice.md">Indice</a></strong>
|
<strong><a href="../Intro-a-R/R.md">R</a></strong>
|
<strong><a href="../Intro-a-Python/Python.md">Python</a></strong>
|
<strong><a href="../Intro-a-Jupyter/Jupyter.md">Jupyter</a></strong>
|
<strong><a href="../Intro-a-github/Github.md">Git y GitHub</a></strong>
|
<strong><a href="../enlaces.md">Enlaces</a></strong>
</p>

<img     style="float: left;" src="OHWe.png" width="100"> 

# Trabajos en colaboración

**El contenido de este taller fue desarrollado por The Carpentries, y lo compartimos aquí
para que sea fácilmente accesible a los participantes de este taller. El contenido de 
este taller puede ser citado de la siguiente manera.**

**Daisie Huang and Ivan Gonzalez (eds): "Software Carpentry: Version
Control with Git."  Version 2016.06, June 2016,
[https://github.com/swcarpentry/git-novice](https://github.com/swcarpentry/git-novice), 
[DOI:10.5281/zenodo.57467](https://zenodo.org/record/57467).**

---

¿Cómo puedo usar el control de versiones para colaborar con otras personas?

Para el siguiente paso, formen parejas. Una persona será el "dueño" y la otra el "colaborador". El objetivo es que el colaborador 
agregue cambios al repositorio del dueño. Vamos a cambiar roles al final, de modo que ambas personas puedan participar como dueño y colaborador.

> ## Practicando por tu cuenta
>
> Si estás trabajando en esta lección por tu cuenta, puedes hacerlo abriendo una segunda sesión en la 
> ventana de la terminal. Esta ventana representará a tu compañero trabajando en otra computadora. No necesitas darle acceso a nadie en GitHub, pues tú serás ambos "compañeros".
{: .callout}

El dueño debe dar acceso al colaborador. En GitHub, haz clic en el botón de configuración arriba a la derecha,
luego selecciona "Collaborators" e ingresa el nombre de tu colaborador.

![Adding Collaborators on GitHub](https://raw.githubusercontent.com/swcarpentry/git-novice-es/gh-pages/fig/github-add-collaborators.png)

Para aceptar la invitación de acceso al repositorio, el colaborador
debe ingresar a [https://github.com/notifications](https://github.com/notifications).
Una vez allí, se puede aceptar la invitación a dicho repositorio.

Luego, el colaborador debe descargar una copia del repositorio del dueño a su máquina. Esto se conoce como "clonar un repositorio". Para clonar el repositorio del dueño en su carpeta de `Desktop`, el colaborador debe ejecutar las siguientes líneas:

~~~
$ git clone https://github.com/vlad/planets.git ~/Desktop/vlad-planets
~~~

Reemplaza 'vlad' con el nombre de usuario del dueño.

![After Creating Clone of Repository](https://raw.githubusercontent.com/swcarpentry/git-novice-es/gh-pages/fig/github-collaboration.svg)

El colaborador puede ahora hacer cambios en la versión clonada del repositorio del dueño, en la misma forma en que se hacían previamente:

~~~
$ cd ~/Desktop/vlad-planets
$ nano pluto.txt
$ cat pluto.txt
~~~

~~~
It is so a planet!
~~~

~~~
$ git add pluto.txt
$ git commit -m "Add notes about Pluto"
~~~

~~~
 1 file changed, 1 insertion(+)
 create mode 100644 pluto.txt
~~~

Luego enviar los cambios hacia el *repositorio del dueño* en GitHub haciendo **push**:

~~~
$ git push origin master
~~~

~~~
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 306 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/vlad/planets.git
   9272da5..29aba7c master -> master
~~~

Nota que no es necesario crear un directorio remoto llamado `origin`: Git utiliza este nombre de manera automática
cuando clonamos un repositorio. (Esta es la razón por la cual `origin` era una opción sensata a la hora de configurar
directorios remotos a mano).

Ahora echa un vistazo al repositorio del dueño en su sitio de Github (quizá debas actualizar la página). Deberás ver 
el nuevo **commit** hecho por el colaborador.

Para descargar los cambios hechos por el colaborador desde GitHub, el dueño debe correr las siguientes líneas:

~~~
$ git pull origin master
~~~

~~~
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0)
Unpacking objects: 100% (3/3), done.
From https://github.com/vlad/planets
 * branch master -> FETCH_HEAD
Updating 9272da5..29aba7c
Fast-forward
 pluto.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 pluto.txt
~~~

Ahora hay tres repositorios sincronizados (el local del dueño, el local del colaborador y el del dueño en GitHub).

## Un flujo de trabajo colaborativo básico

Es considerado buena práctica estar seguro de que tienes una versión actualizada del repositorio en el que colaboras. 
Para ello deberías hacer un `git pull` antes de hacer cambios. El enfoque sería:
 
 
* actualizar el repositorio local `git pull origin master`,
* realizar cambios `git add`,
* realizar un **commit** `git commit -m`, y
* cargar las actualizaciones a GitHub con `git push origin master`
 
 Es mejor hacer varias actualizaciones pequeñas que un **commit** grande con cambios enormes. **Commits** pequeños son 
 más fáciles de leer y revisar.

## Cambiar roles
 
Cambien los roles y repitan todo el proceso.

## Revisar cambios
 
El dueño hace un **push** de los **commits** al repositorio sin dar información al colaborador. ¿Cómo puede este saberlo 
desde la línea de comandos y desde GitHub?

## Solución

En la línea de comandos, el colaborador puede usar ```git fetch origin master``` para acceder a los cambios remotos en el 
repositorio local, sin hacer un **merge**. Luego, corriendo ```git diff master origin/master```, el colaborador verá los 
cambios en la terminal.  
 
En GitHub, el colaborador puede realizar su propio **fork** y hallar la barra gris que indica "This branch is 1 commit behind 
Our-Respository:master.". Lejos, a la derecha de la barra gris, hay un link para comparar. En la página para comparar, el 
colaborador debe cambiar el **fork** hacia su propio repositorio, luego hacer click en el link para "comparar entre forks" y, 
finalmente, cambiar el **fork** al repositorio principal. Esto mostrará todos los **commits** que sean distintos. 

## Comentar cambios en GitHub
 
El colaborador podría tener algunas preguntas sobre cambios en una línea hechos por el dueño. 
 
Con GitHub, es posible comentar la diferencia en un **commit**. Sobre la línea de código a comentar aparece un botón azul
para abrir una ventana. 
 
El colaborador puede escribir sus comentarios y sugerencias usando la interfaz de GitHub.
