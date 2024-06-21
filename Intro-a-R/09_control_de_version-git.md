---
editor_options: 
  markdown: 
    wrap: 72
---

# Control de versiones con git y GitHub

## Objetivos

En este capítulo veremos:

-   ¿Por qué **git** es útil para análisis reproducibles?
-   ¿Cómo usar **git** para registrar los cambios que se hacen en el
    tiempo?
-   ¿Cómo usar **GitHub** para colaborar?
-   ¿Cómo estructurar los “*commits*” para que los cambios sean claros
    para otros?
-   ¿Cómo escribir mensajes de “*commits*” que sean efectivos?

## El problema con los nombres de archivo

<img src="imagenes/GIT4RStudio/3.1_phd_comics_final.png " alt="El dilema de usar nombres como descriptor de versiones." width="80%"/>

<p class="caption">

El dilema de usar nombres como descriptor de versiones.

</p>

Cada archivo en un proceso científico sufre de cambios. Los manuscritos
son editados. Las figuras son revisadas. Los códigos se corrigen cuando
se encuentran problemas. Los archivos de datos se combinan, los errores
son corregidos, se dividen y combinan nuevamente. En el curso de un
análisis simple, uno puede esperar miles de cambios en los archivos. Y
aún así, todo lo que usamos para identificas este sinnúmero de cambios
son los simples **nombres de archivos**. Teniendo esto en consideración,
es lógico pensar que debe existir una forma mejor… Y si la hay, se
conoce como **Control de Versiones**.

Un **sistema de control de versiones** ayuda a seguir lso cambios que se
realizan a nuestros archivos, sin el desastre que resulta de utilizar
sólo el nombre de los archivos. En los sistemas de control de versiones
como `git`, se registra no sólo el nombre del archivo, si no que además
su contenido, de esta forma, cuando el contenido cambia, se puede
identificar que partes estaban y donde. El registro además contiene la
relaciones entre las versiones, de esta forma se tiene un historial de
todos los cambios deribados de las cada una de las versiones y es fácil
dibujar un gráfico que muestre los cambios que ha sufrido un archivo,
con sus versiones previas y aquellas derivadas.

<img src="imagenes/GIT4RStudio/3.2_version-graph.png" alt="Evolución de las versiones de un archivo." width="40%"/>

<p class="caption">

Evolución de las versiones de un archivo.

</p>

Los sistemas de control de versiones asignan un identificador a cada
versión de cada archivo, manteniendo un registro de como están
relacionados entre ellos. Además, estos sistemas permiten generar ramas
laterales a una versión, la que puede ser fusionada de regreso a la
tronco principal. Es posible además tener *múltiples copias* en
múltiples computadores como respaldos y para trabajar colaborativamente.
Finalmente, se pueden incluir etiquetas (tags) a versiones particulares,
de esta forma es fácil retornar la versión que tenían los archivos
cuando fueron etiquetados. Esto es particulamente útil para identificar
una versión exacta de los datos, código y texto, por ejemplo, de un
manuscrito que fue enviado para ser publicado, este puede ser el caso de
la etiqueda `R2` en la figura anterior.

## Control de versiones y colaboración usando Git and GitHub

Es importante hacer la distinción entre **git** y **GitHub**.

-   **git**: Software para el control de versiones que monitorea los
    archivos de un directorio (repositorio).
    -   git crea el historial de versiones del repositorio.
-   **GitHub**: Sitio web que permite a los usuarios almacenar sus
    repositorios git y compartirlos con otros usuarios.

<img src="imagenes/GIT4RStudio/6.3_vc-local-github.png" alt="Diferencia entre git y GitHub." width="60%"/>

<p class="caption">

Diferencia entre git y GitHub.

</p>

## Veamos un repositorio de GitHub

La captura de pantalla en la figura que se presenta a continuación,
muestra una copia de un repositorio almacenado en GitHub, con el listado
de archivos y directorios, indicando cuando fueron modificados,
incluyendo información acerca de quien hizo los cambios y una pequeña
descripción de los cambios realizados.

<img src="imagenes/GIT4RStudio/6.4_ss3sim-github.png" alt="Captura de pantalla de un repositorio en GitHub." width="100%"/>

<p class="caption">

Captura de pantalla de un repositorio en GitHub.

</p>

Si nos metemos en los “commits” del repositorio, podemos ver la historia
de los cambios que se le han realizado. Por ejemplo, se ve que
`kellijohnson` y `seananderson` hicieron algunos cambios durante junio y
julio:

<img src="imagenes/GIT4RStudio/6.5_ss3sim-commits.png" alt="Captura de pantalla de los Commits de un repositorio en GitHub." width="100%"/>

<p class="caption">

Captura de pantalla de los Commits de un repositorio en GitHub.

</p>

Si entramos ahora a ver los cambios realizados el 13 de julio, podemos
saber exactamente cuales fueron los cambios realizados a cada archivo:

<img src="imagenes/GIT4RStudio/6.6_ss3sim-diff.png" alt="Captura de pantalla donde se presentan las diferencias entre dos versiones alojadas en un repositorio de GitHub." width="100%"/>

<p class="caption">

Captura de pantalla donde se presentan las diferencias entre dos
versiones alojadas en un repositorio de GitHub.

</p>

Monitorear estas modificaciones, como se relacionan a cada una de las
versiones de un software en particular y a los archivos es exactamente
para lo que fueron diseñados git y GitHub. Vamos a mostrar como estos
sistemas pueden ser realmente efectivos para monitorear las versiones de
códigos científicos, figuras y manuscritos y de esta forma tener flujos
de trabajo reproducibles.

## El ciclo de vida de Git

Como usuario de git usted tiene que entender algunos conceptos básicos
asociados a los sets de cambios con versiones y como estos son
almacenados y se mueven a través del repositorio. Cualquier repositorio
de git puede ser clonado, de esta forma existe en forma local y remota.
Pero cada uno de estos repositorios clonados son una copia simple de
todos los archivos y del historial de los cambios que se han realizado,
lo que son almacenados en un forma repositio git particular. Para
nuestros propósitos, tenemos que considerar un repositorio de git
simplemente como un directorio que contiene adicionalmente un set de
metadatos relacionado las versiones.

En un directorio local donde git fue habilitado, el directorio contiene
la versión actual de todos los archivos del repositorio. Estos archivos
de trabajo están unidos a un directorio escondido que contiene el
‘Repositorio local’, el que a su vez contiene todos los otros cambios
que se han realizado a los archivos y los metadatos sobre las versiones.

De esta forma, cuando se está usando git para trabajar con archivos, se
pueden usar los comandos de git para indicar específicamente que cambios
a los archivos de trabajo deben ser definidos para las versiones (usando
el comando `git add`) y cuando grabar estos cambios como una versión en
el repositorio local (usando el comando `git commit`).

Los demás conceptos se relacionan a la sincronización de los cambios en
el repositorio local a un repositorio remoto. El comando `git push` se
usar para enviar los cambios realizados en forma local a un repositorio
remoto (posiblemente en GitHub) y el comando `git pull` es usado para
traer los cambios del repositorio remoto y unirlos al repositorio local.

<img src="imagenes/GIT4RStudio/6.7_git-flowchart.png" alt="Diagrama de flujo del ciclo de vida de git." width="70%"/>

<p class="caption">

Diagrama de flujo del ciclo de vida de git.

</p>

-   `git clone`: Copia todo el repositorio remoto a uno local.
-   `git add` (stage): Notifica a git de monitorear un set particular de
    cambios.
-   `git commit`: Almacena los cambios realizados como una versión.
-   `git pull`: Combina los cambios de un repositorio remoto a nuestro
    repositorio local.
-   `git push`: Copia los cambios de nuestro repositorio local al
    repositorio remoto.
-   `git status`: Determina el estado de los archivos en el repositorio
    local.
-   `git log`: Imprime el historial de cambios en el repositorio.

Estos siete comandos son la mayoría de los comando que va a necesitar
para utilizar git en forma exitosa. Pero todo esto es demasiado
abstracto, mejor exploremos estos conceptos utilizando ejemplos reales.

## Cree un repositorio remoto en GitHub

Empecemos creando un repositorio en GitHub, luego editaremos algunos
archivos.

-   Ingrese al sitio [GitHub](https://github.com).
-   Clic en el botón de repositorio nuevo (New repository).
-   Nómbrelo como `sasap-test`.
-   Cree un archivo README.md.
-   Defina la licencia a Apache 2.0.

<img src="imagenes/GIT4RStudio/6.8_new-repo-github.png" alt="Captura de pantalla de la creación de un repositorio nuevo en GitHub." width="100%"/>

<p class="caption">

Captura de pantalla de la creación de un repositorio nuevo en GitHub.

</p>

¡Usted acaba de crear su primer repositorio! Este repositorio fue creado
con un par de archivos que GitHub hace por usted, son los archivos
README.md, LICENSE y .gitignore.

<img src="imagenes/GIT4RStudio/6.9_sasap-test-repo.png" alt="Captura de pantalla con el repositorio recién creado llamado sasap-test." width="100%"/>

<p class="caption">

Captura de pantalla con el repositorio recién creado llamado sasap-test.

</p>

Para hacer cambios menores a archivos de texto se puede utilizar la
interfase web de GitHub. Navegue al archivo `README.md` en el listado de
archivos y habilite la edición haciendo clic en el icono del *lápiz*.
Este es un archivo normal con el formado Markdown, ahora se puede
editar, agregando o removiendo texto. Cuando haya terminado, incluya un
mensaje de commit y luego haga clic en el botón `Commit changes`.

<img src="imagenes/GIT4RStudio/6.10_sasap-test-edit.png" alt="Captura de pantalla con la interfase web de GitHub para la edición de documentos de texto." width="100%"/>

<p class="caption">

Captura de pantalla con la interfase web de GitHub para la edición de
documentos de texto.

</p>

<img src="imagenes/GIT4RStudio/6.11_sasap-test-commit.png" alt="Captura de pantalla con la interfase web de GitHub para la confirmar de los cambios realizados al documento de texto (commit changes)." width="100%"/>

<p class="caption">

Captura de pantalla con la interfase web de GitHub para la confirmar de
los cambios realizados al documento de texto (commit changes).

</p>

Felicitaciones, ahora usted acaba de confirmar (commit) los cambios,
ahora es el autor de la primera versión de este archivo. Si navega de
regreso a la página del repositorio GitHub, puede ver la lista de los
cambios confirmados (commits) ahí, así como la visualización del
documento generado a partir del archivo README.md.

![Captura de pantalla con la interfase web los cambios corfimados
(commits) y de la visualización de la página
README.md.](imagenes/GIT4RStudio/6.12_sasap-test-displayed.png){alt="Captura de pantalla con la interfase web los cambios corfimados (commits) y de la visualización de la página README.md."
width="100%"}

<p class="caption">

Captura de pantalla con la interfase web los cambios corfimados
(commits) y de la visualización de la página README.md.

</p>

Expliquemos algunas cosas sobre esta ventana. Representa una vista del
repositorio que acaba de crear, hasta ahora mostrando todos sus
archivos. Para cada archivo, muestra la fecha de la última modificación
y el mensaje asociado al *commit* que se utilizó para describir los
cambios realizados. Esta es la razón por qué es tan importante escribir
buenos mensajes, que contengan información relevante cuando se hace el
*commit*. Además, el título azul sobre el listado de archivos muestra el
*commit* más reciente, con su mensaje asociado y su identificados SHA.
Ese identificador SHA es la clave para el set de versiones. Si hace clic
en el identificador SHA (*810f314*), va a mostrar los cambios que se
hicieron en ese *commit* en particular.

En la siguiente sección vamos a usar el URL de GitHub del repositorio
que acaba de crear y lo usaremos plara clonarlo (`clone`) a un
repositorio en nuestra máquina local y así editar los archivos con
**RStudio**. Para eso, primero tenemos que copiar el URL de GitHub, que
representa la dirección del repositorio:

<img src="imagenes/GIT4RStudio/6.13_sasap-test-clone-url.png" alt="Captura de pantalla para clonar un repositorio GitHub." width="100%"/>

<p class="caption">

Captura de pantalla para clonar un repositorio GitHub.

</p>

## Trabajando localmente con Git en RStudio

RStudio incluye soporte para Git como sistema de control de versiones,
pero esto **sólo** ocurre si estamos trabajando en un *Proyecto de
RStudio* (RStudio project folder). En esta sección vamos a clonar el
repositorio que se creó en GitHub y lo vamos a dejar un repositorio
local de un proyecto de RStudio.

Esto es lo que vamos a hacer:

1.  Crear un proyecto nuevo.
2.  Inspeccionar el panel Git y el historial de versiones.
3.  Confirmar una modificación (commit) al archivo README.md.
4.  Commit las modificaciones que hicieron en RStudio.
5.  Inspeccionar el historial de versiones.
6.  Crear y commit un archivo Rmd.
7.  Enviar (*Push*) estos cambios a GitHub.
8.  Ver el historial de cambios en GitHub.

### Crear nuevo Proyecto (Create a New Project)

Comience creando un *New Project…* en RStudio, seleccione la opción
*Version Control* y pegue el URL de GitHub que copió en el espacio para
repositorio remoto (*Repository URL*). Si bien usted puede darle el
nombre que quiera al repositorio local, se usa típicamente el mismo
nombre que el que se tiene en GitHub, de esta forma se mantiene un grado
de correspondencia. Usted puede elegir cualquier directorio para su
copia local, en mi caso use el directorio `development`
(fig. @ref(fig:githubClone)).

<img src="imagenes/GIT4RStudio/6.14_rstudio-clone-repo.png" alt="Captura de pantalla para la creasción de un proyecto de RStudio clonando un repositorio remoto." width="100%"/>

<p class="caption">

Captura de pantalla para la creasción de un proyecto de RStudio clonando
un repositorio remoto.

</p>

Un vez que haga clic en `Create Project` (crear proyecto), una nueva
página de RStudio se abrirá con todos los archivos copiados localmente
desde el repositorio remoto. Dependiendo de como esté configurada la
versión de RStudio, la posición y tamaño de los paneles puede cambiar,
pero generalmente todos van a estar presentes, incluyendo los paneles
*Git* y el listado de archivos (*Files*) que fueron creados en el
repositorio remoto.

<img src="imagenes/GIT4RStudio/6.15_rstudio-sasap-test.png" alt="Captura de pantalla de la interfase del projecto de RStudio con el clon local de repositorio." width="100%"/>

<p class="caption">

Captura de pantalla de la interfase del projecto de RStudio con el clon
local de repositorio.

</p>

En la figura @ref(fig:githubCloneLocal) puede ver que apareció un
archivo llamado `sasap-test.Rproj` y que están los otros 3 archivos que
se crearon con el repositorio remoto de GitHub (`.gitignore`, `LICENSE`
y `README.md`).

En el panel *Git* en RStudio se pueden ver 2 archivos. Este es el panel
de estatus donde se se muestran todos los archivos del repositorio en
los cuales se han realizado modificaciones. En este caso, el archivo
`.gitignore` se muestra con una *M* que significa *Modificado* y
`sasap-test.Rproj` con un *? ?* para indicar que este archivo no está
siendo monitoreado. Esto significa que git no tiene registro de ninguna
version para este archivo y que no sabe nada acerca de el. A medida que
usted vaya tomando decisiones sobre el control de versiones en RStudio,
estos iconos van a ir cambiando para reflejar el estatus de la versión
actual de cada uno de los archivos.

### Inspeccionar el historial (history)

A continuación vamos a hacer clic en el botón *History* (historial, es
el reloj que aparece en la primera fila al interior del panel ed Git),
esto despliega una ventana con el registro de los cambios que se han
realizado y, en este caso, deben ser idénticos a lo que usted vio en
GitHub. Al hacer clic en cada fila del historial, podrá ir viendo
exactamente que fue agregado y cambiado en cada uno de los commits en
este repositorio.

<img src="imagenes/GIT4RStudio/6.16_rstudio-history-1.png" alt="Historial de los cambios realizados en el repositorio local." width="100%"/>

<p class="caption">

Historial de los cambios realizados en el repositorio local.

</p>

### Confirme cambios haciendo clic en *commit* al archivo README.md (Commit a README.md change)

Ahora hagamos algunos cambios al archivo README.md en RStudio. Agregue
una sección nueva con un block de *markdown* como este:

```{=html}
<pre><code>

## Git desde RStudio

Desde la interfase de RStudio, es posible hacer las mismas acciones con el sistema de versiones que se hicieron en  GitHub
y mucho más. Además en RStudio se tienen las ventajas propias de programar en un IDE con completación de comandos y otras
características que hacen nuestro trabajo más fácil.

- Agregar archivos al control de versiones
- Ccommit cambios
- Push commits a GitHub

</code></pre>
```
Una vez que los haya guardado, podrá ver en forma inmediata el archivo
*README.md* en el panel Git (fig. @ref(fig:rstudioPanelStatus)), marcado
con una **M** de modificación. Ahora usted puede seleccionar este
archivo en el panel de Git y hacer clic en *Diff* para ver los cambios
(comparando las diferencias) que guardó (note que estos cambios no se
han confirmado (*commit*) aun a su repositorio local).

<img src="imagenes/GIT4RStudio/6.17_rstudio-status-pane.png" alt="Panel de estado de los cambios en los archivos." width="100%"/>

<p class="caption">

Panel de estado de los cambios en los archivos.

</p>

En la figura @ref(fig:rstudioDiferencias) se muestra como se ven los
cambios comparados con el archivo original. La líneas nuevas se destacan
en color verde y en rojo las que fueron eliminadas.

<img src="imagenes/GIT4RStudio/6.18_rstudio-diff.png" alt="Ventana que presenta las diferencias entre la versión almacenada en el repositorio y los últimos cambios realizados." width="100%"/>

<p class="caption">

Ventana que presenta las diferencias entre la versión almacenada en el
repositorio y los últimos cambios realizados.

</p>

### Commit los cambios hechos en Rstudio

Para confirmar los cambios que se acaban de hacer en el archivo
README.md, selecciones la caja de selección *Staged* a lado del nombre
del archivo, este le dice a Git cuales son los cambios que quiere sean
incluidos en el commit, escriba un mensaje describiendo que cambios se
hicieron y por qué y finalmente haga clic en boton *Commit*
(fig. @ref(fig:rstudioCommit1)).

<img src="imagenes/GIT4RStudio/6.19_rstudio-commit-1.png" alt="Captura de pantalla con un mensaje describiendo la confirmación (commit) que se realizará." width="100%"/>

<p class="caption">

Captura de pantalla con un mensaje describiendo la confirmación (commit)
que se realizará.

</p>

Note que algunos de los cambios en el repositorio, `.gitignore` y
`aula-ejemplo.Rproj`, aun no se han confirmado y no serán parte del
*commit*. En otras palabras, aun existen cambios pendientes para ser
registrados en el repositorio. Usted vará una notificación que indica
(en inglés):

<code>Your branch is ahead of ‘origin/master’ by 1 commit.</code>

Lo que se traduce a: <code>\_Su rama esta más avanzadada que el
‘maestro/origen’ por una confirmación</code>

Esto significa que hemos commit **1** cambio en el repositorio local,
pero que este no se está en el repositorio de origen (`origin`), no se
ha hecho push, donde origen es el nombre que se usa típicamente para el
repositorio en GitHub. Entonces, confirmemos los cambios pendientes,
para esto seleccione la caja *staged* y luego escriba el mensaje
describiendo el commit (fig. @ref(fig:rstudioCommit2)).

<img src="imagenes/GIT4RStudio/6.20_rstudio-commit-2.png" alt="Captura de pantalla con los archivos a confirmar sus cambios y el texto descriptivo de la confirmación." width="100%"/>

<p class="caption">

Captura de pantalla con los archivos a confirmar sus cambios y el texto
descriptivo de la confirmación.

</p>

Cuando haya terminado no habrán mas cambios pendientes en el panel *Git*
y el repositorio estará completamente limpio.

### Inspeccionando el historial

Fíjese que ahora el mensaje dice:

<code>Your branch is ahead of ‘origin/master’ by 2 commits.</code>

<code>\_Su rama esta más avanzadada que el ‘maestro/origen’ por 2
confirmación</code>

Estas 2 confirmaciones son las dos que acabamos de hacer y no se han
empujado (push) aun a GitHub. Haciendo clic en el botón *History*
(historial), podemos ver que hay un total de 3 commit en el repositorio
local, mientras hay sólo 2 en GitHub (fig. @ref(fig:rstudioCommit3)).

<img src="imagenes/GIT4RStudio/6.21_rstudio-history-2.png" alt="Captura de pantalla con 4 commits." width="100%"/>

<p class="caption">

Captura de pantalla con 4 commits.

</p>

### Enviar (Push) cambios a GitHub

Ahora que se han hecho todos los cambios deseados en el repositorio
local, usted puede empujar (*push*) los cambios a GitHub usando el botón
*Push*. Se abrirá una ventana donde se pregunta por su usuario y
password de GitHub, luego los cambios serán enviados. Esto dejará su
repositorio local en un estado totalmente limpio y sincronizado con el
repositorio remoto. Terminado esto, en el historial (en GitHub) se
muestran todos los commits, incluyendo los 1 que fueron hechos en GitHub
y los 2 que se hicieron en forma local con RStudio.

<img src="imagenes/GIT4RStudio/6.22_rstudio-history-3.png" alt="Captura de pantalla con los 4 modificaciones confirmadas." width="100%"/>

<p class="caption">

Captura de pantalla con los 4 modificaciones confirmadas.

</p>

Ahora puede ver que las etiquetas del repositorio local (`HEAD`) y del
remoto (`origin/HEAD`) están apuntando a la misma versión en el
historial. De esta forma, si miramos el historial de los commits en
GitHub serán iguales a los que tenemos en forma local.

<img src="imagenes/GIT4RStudio/6.23_github-history.png" alt="Captura de pantalla con el historial de cambios en github." width="100%"/>

<p class="caption">

Captura de pantalla con el historial de cambios en github.

</p>

## Sobre (buenos) mensajes de confirmación (commit)

Es claro que una buena documentación es crítica para hacer del historial
de versiones significativo y útil. Es tentador saltarse la escritura del
mensaje asociado al commit o escribir algo por defecto como
‘Actualización!’. Sin embargo es importante escribir mensajes que sean
para entender en el futuro que se hizo y por qué. Ademas, los mensajes
que se usan en commits son en general más fáciles de entender si usan
una convención de verbos activos. Por ejemplo, se puede ver que los
mensajes de commit en las capturas de pantallas comienzan siempre con un
verbo en pasado (en inglés!) y que explican que fue lo que se cambió.

Si bien muchos de los cambios que aquí se hicieron son simples y se
explican por si mismos, para cambios más complejos, es mejor entregar un
mensaje completo y auto-contenido. La convención, sin embargo, es tratar
de usar mensajes cortos, con una sentencia breve, seguido de una
explicación más detallada y racional para el cambio. Esto permite que el
nivel de detalles sea legible en el registro de las versiones (version
log). No puedo contar el número de veces que he visto los registro d e
commits de hace 2, 3 o 10 años y agradecido el nivel de diligencia de
los colaboradores que se tomaron el tiempo de describir el trabajo que
se realizó.

## Flujos de trabajo colaborativos y libres de conflictos (relacionados con Git)

Hasta ahora nos hemos enfocado al uso de Git y GitHub para el uso
personal, como ya se demostró esto es extremadamente útil. Sin embargo
donde git y GitHua brilla es cuando se comparte un repositorio GitHub
con colaboradores, de esta forma se pede trabajar en un código, análisis
y modelos en forma colaborativa. Cuando se trabaja de esta manera con
otros investigadores, es muy importante poner atención al estado del
repositorio remoto para evitar potenciales conflictos al combinar el
trabajo. Un *merge conflict* ocurre cuando dos colaboradores hacen 2
commits en forma separada donde se ha(n) cambiado(s) la(s) misma(s)
línea(s) de código de un archivo. Cuando esto ocurre, git no puede
combinar los cambios en forma automática y arroja un error preguntando
como resolver el conflicto. Esto no es grave, no es necesario tenerle
miedo a los *merge conflicts* ya que son muy fáciles resolver y aquí hay
algunas
[guías](https://help.github.com/articles/resolving-a-merge-conflict-using-the-command-line/)
[geniales](https://stackoverflow.com/questions/161813/how-to-resolve-merge-conflicts-in-git).
de como hacerlo (por ahora sólo en inglés).

Dicho esto, es siempre mejor evadir este tipo de conflictos, lo que se
pueden minimizar siguiendo las siguientes sugerencias:

-   Asegúrese de traer (*pull down*) todos los cambios antes de
    confirmarlos (commit).
    -   Asegurese que tiene los cambios más recientes.
    -   Pero puede ser que necesite arreglar su código si ocurren
        conflictos.
-   Coordínese con con sus colaboradores con quien va a trabajar.
    -   Usted **tiene** que comunicarse para colaborar.

## Actividad

Use RStudio para agregar un nuevo archivo al repositorio `sasap-test`,
desarrolle una estructura básica y guárdela.

A continuación *stage* y *commit* el archivo en forma local y luego
*push it* a GitHub.

## Tópicos avanzados

Hay mucho que no hemos visto en este tutorial. Existen tutoriales muy
completos que cubren tópicos mas avanzados. Algunos de estos temas son:

-   Usando git en la linea de comándos.

-   Resolviendo conflictos.

-   *Branching* y *merging*.

-   *Pull requests* versus contribuciones directas por colaboradores.

-   Usando *.gitignore* para proteger datos sensitivos.

-   *GitHub Issues* y por que son útiles.

-   y más, mucho más.

-   [Try Git](https://try.github.io) es un tutorial interactivo muy
    bueno y completo.

-   Software Carpentry [Version Control with
    Git](http://swcarpentry.github.io/git-novice/)

-   Codecademy [Learn Git](https://www.codecademy.com/learn/learn-git)
    (some paid)
