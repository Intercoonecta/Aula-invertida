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

## Configurando Git

**El contenido de este taller fue desarrollado por The Carpentries, y lo compartimos aquí
para que sea fácilmente accesible a los participantes de este taller. El contenido de 
este taller puede ser citado de la siguiente manera.**

**Daisie Huang and Ivan Gonzalez (eds): "Software Carpentry: Version
Control with Git."  Version 2016.06, June 2016,
[https://github.com/swcarpentry/git-novice](https://github.com/swcarpentry/git-novice), 
[DOI:10.5281/zenodo.57467](https://zenodo.org/record/57467).**

---

Cuando usamos Git en una computadora por primera vez, es necesario configurar algunas cosas. A continuación se presentan algunos ejemplos  de configuraciones que estableceremos a medida que trabajemos con Git:

*  nombre y correo electrónico,
*  cuál es nuestro editor de texto preferido,
*  y que queremos utilizar estos ajustes globalmente (es decir, para cada proyecto).

En la línea de comandos, los comandos de Git se escriben como "git verb", 
donde "verb" es lo que queremos hacer. Así es como 
Drácula configura su nueva computadora:

~~~
$ git config --global user.name "Vlad Dracula"
$ git config --global user.email "vlad@tran.sylvan.ia"
~~~


Utiliza tu propio nombre y dirección de correo electrónico en lugar de los de Drácula. El nombre de usuario y el correo electrónico se asociarán con tu actividad posterior de Git, lo que significa que cualquier cambio realizado en [GitHub](http://github.com/), [BitBucket](http://bitbucket.org/), [GitLab](http://gitlab.com/) u
otro servidor de Git en una lección posterior incluirá esta información.

## Finales de línea
Al igual que con otras teclas, cuando haces click en la tecla 'Enter' de tu teclado,
tu computadora codifica este input como un caracter.
Por razones que son demasiado largas para explicar aquí, diferentes sistemas operativos usan diferentes caracteres para representar el final de una línea.
(También son conocidas como *newlines* o *line breaks*.)
Como Git usa éstos caracteres para comparar archivos,
esto puede causar problemas inesperados cuando se edita un archivo en máquinas diferentes. 
 
Puedes cambiar el modo en que Git reconoce y codifica finales de línea
usando el comando "core.autocrlf" con "git config".
Se recomiendan las siguientes configuraciones:

En OS X y Linux:

~~~
$ git config --global core.autocrlf input
~~~


Y en Windows:

~~~
$ git config --global core.autocrlf true
~~~

 
Puedes leer más sobre este tema [en esta página de GitHub](https://help.github.com/articles/dealing-with-line-endings/) (en inglés).


Para estas lecciones, estaremos interactuando con [GitHub](http://github.com/), por lo tanto la dirección de correo electrónico utilizada debe ser la misma que utilizaste al configurar tu cuenta de GitHub. Si te preocupa la privacidad, revisa [las instrucciones de GitHub en inglés para mantener tu dirección de correo electrónico privada](https://docs.github.com/es/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address).
Si eliges utilizar una dirección de correo electrónico privada con GitHub, usa la misma dirección de correo electrónico para el valor "user.email", por ejemplo, "username@users.noreply.github.com"  reemplazando" username" con tu nombre de usuario de GitHub. Puedes cambiar la dirección de correo electrónico posteriormente utilizando el comando "git config" nuevamente.

Drácula también tiene que establecer su editor de texto favorito, siguiendo esta tabla:

| Editor             | Comando de configuración                            |
|:-------------------|:-------------------------------------------------|
| Atom | $ git config --global core.editor "atom --wait"|
| nano               | $ git config --global core.editor "nano -w"    |
| TextWrangler (Mac)      | $ git config --global core.editor "edit -w"    |
| Sublime Text (Mac) | $ git config --global core.editor "subl -n -w" |
| Sublime Text (Win, 32-bit) | $ git config --global core.editor "'c:/program files (x86)/sublime text 3/sublime_text.exe' -w" |
| Sublime Text (Win, 64-bit) | $ git config --global core.editor "'c:/program files/sublime text 3/sublime_text.exe' -w" |
| Notepad++ (Win, 32-bitl)    | $ git config --global core.editor "'c:/program files (x86)/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"|
| Notepad++ (Win, 64-bit)    | $ git config --global core.editor "'c:/program files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"|
| Kate (Linux)       | $ git config --global core.editor "kate"       |
| Gedit (Linux)      | $ git config --global core.editor "gedit --wait --new-window"   |
| Scratch (Linux)       | $ git config --global core.editor "scratch-text-editor"  |
| emacs              | $ git config --global core.editor "emacs"   |
| vim                | $ git config --global core.editor "vim"   |
| Visual Studio Code | $ git config --global core.editor "code --wait" |

Es posible reconfigurar el editor de texto para Git siempre que quieras.

## Saliendo de Vim

Ten en cuenta que "vim" es el editor por defecto para muchos programas, si no has utilizado" vim" antes y deseas salir de una sesión, presiona la tecla "Esc" y posteriormente escribe ": q!" y "Enter".


Los cuatro comandos que acabamos de ejecutar sólo se tienen que ejecutar una vez: la flag "--global" le dice a Git que use la configuración para cada proyecto, en tu cuenta de usuario, en esta computadora.

Puedes comprobar tu configuración en cualquier momento:

~~~
$ git config --list
~~~


Puedes cambiar la configuración tantas veces como quieras: sólo usa los mismos comandos para elegir otro editor o actualizar tu correo electrónico.

## Proxy

En algunas redes es necesario usar un
[proxy](https://en.wikipedia.org/wiki/Proxy_server). Si este es el caso, es
posible que también necesites proporcionarle a Git el proxy:

~~~
$ git config --global http.proxy proxy-url
$ git config --global https.proxy proxy-url
~~~

Para deshabilitar el proxy, utiliza

~~~
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
~~~


## Ayuda y manual de Git

Ten presente que si no recuerdas algún comando de  "git", puedes acceder a la lista de comandos utilizando la opción "-h" y al manual de Git con la flag "--help".

~~~
$ git config -h
$ git config --help
~~~
