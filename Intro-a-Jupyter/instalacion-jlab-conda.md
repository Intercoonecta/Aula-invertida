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

<img style="float: left;" src="OHWe.png" width="100"> 

# Instalación de Conda, Python y JupyterLab

Instalaremos en tu computadora la aplicación `JupyterLab` con Python y algunos paquetes útiles, utilizando el sistema `conda`. 

[Conda](https://docs.conda.io) es un administrador de paquetes y entornos para cualquier lenguaje de programación, pero especialmente popular en la comunidad de usuarios de Python. Permite la instalación de diferentes combinaciones y versiones de paquetes de software o librerías y de sus dependencias en diferentes [entornos](https://exponentis.es/creacion-de-entornos-en-anaconda), con la capacidad de cambiar fácilmente de un entorno a otro. Cada entorno contiene una configuración aislada de Python y paquetes que uno escoge, con versiones específicas; un entorno puede estar relacionado a un proyecto específico. `Conda` da acceso a miles de paquetes, y puede ser instalado en tu computadora sin necesidad de tener privilegios administrativos.

`Conda` funciona tanto en Windows como en macOS y Linux. `Conda` y los paquetes disponibles a través de `conda` son generalmente gratuitos y accesibles bajo licencias de código abierto. Hay diferentes maneras de instalar `conda`. Aquí utilizaremos [Miniconda](https://www.anaconda.com/docs/getting-started/miniconda/main), una distribución ligera de `conda`. Otra manera popular de instalar `conda` es a través de la distribución [Anaconda](https://www.anaconda.com/docs/getting-started/anaconda/main), que pre-instala una gran cantidad de paquetes comunes de Python. **Recomendamos `Miniconda`** porque se instala más rápidamente, requiere menos espacio en el disco, y promueve la inclusión selectiva de paquetes necesarios para proyectos específicos en entornos bien definidos.

> **Nota sobre la licencia:** Recientemente [Anaconda Inc.](https://www.datacamp.com/es/blog/anaconda-alternatives#c%C3%B3digo-abierto-y-licencias-aunqu), la compañía que distribuye `Anaconda` y `Miniconda`, ha [modificado su licencia con términos más restrictivos para uso comercial o en organizaciones grandes](https://www.datacamp.com/es/blog/anaconda-alternatives#c%C3%B3digo-abierto-y-licencias-aunqu). Esto no es ningún problema para uso individual o de grupos pequeños, pero para el futuro recomendamos el uso de la distribución [Miniforge](https://conda-forge.org/download/) que es 100% Código Abierto.

En estos tutoriales iniciales no profundizaremos sobre `conda` más allá de lo necesario. Entraremos en más detalles durante el hackatón. Si quieres aprender más, visita los enlaces al final de esta página.

## Instalar Miniconda

Incluimos instrucciones breves para instalar `Miniconda`. Puedes consultar los enlaces en "Referencias y recursos" para obtener ayuda adicional, incluyendo algunos videos en YouTube.

### Windows

En [esta página](https://www.anaconda.com/download/success#miniconda), bajo "Miniconda Installers" y "Windows", descarga el archivo en el enlace `64-Bit Graphical Installer` (alrededor de 90 MB). Ahora:

- Ejecuta el archivo instalador (`.exe`) después de bajarlo. 
- Continua hasta la ventana que da a escoger el tipo de instalación. Selecciona la opción para instalar como usuario local solamente (*Just me (recommended)*).
- Acepta la ruta (*Destination Folder*) de archivos de instalación de defecto, probablemente: `C:\Users\MIPERFIL\AppData\Local\miniconda3`
- En la ventana *Advanced Installation Options*, desactiva la selección de ambas cajas (*Add Miniconda3 ...* y *Register Miniconda3 ...*)
- En la ventana *Completing Miniconda3*, desactiva la selección de ambas cajas.

Cuando la instalación ha concluido, abre el *Anaconda PowerShell Prompt* o *Anaconda Prompt* desde el menú de `Start`. Puedes comprobar que funciona bien corriendo el comando `conda env list`.

### macOS o Linux

En la **terminal** (*shell*, generalmente la terminal tipo "bash"), corre estos comandos:

```bash
# En macOS
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
# En Linux
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

wget $url -O miniconda.sh
bash miniconda.sh -b -p $HOME/miniconda3
```

Si el instalador te pregunta si quieres que inicialize Miniconda3 corriendo `conda init` ("Do you wish the installer to initialize Miniconda3 by running conda init?"), selecciona "yes". Si concluye sin hacer esa pregunta, ejecuta el siguiente comando: `./miniconda3/bin/conda init`. Por último, ejecuta el comando `conda update conda --yes`

## Entornos con conda

### Crear entorno de conda para JupyterLab

Con conda ya instalado, el último paso es crear un entorno de conda que usaremos para correr la aplicación `JupyterLab`. Además de `JupyterLab`, este entorno incluirá **Python 3.12** y tres paquetes de Python de uso amplio que también son utilizados en el tutorial de Python: `matplotlib`, `pandas` y `netcdf4`.

En la terminal donde instalaste miniconda, corre este comando de `conda create` para crear el entorno con el nombre `jupyterlab`: 
```bash
conda create --yes -n jupyterlab -c conda-forge python=3.12 jupyter jupyterlab-language-pack-es-ES nb_conda_kernels matplotlib pandas netcdf4
```

[**conda-forge**](https://conda-forge.org) es un repositorio y "canal" de paquetes de `conda` administrado por una amplia comunidad internacional, que actualmente contiene casi 30 mil paquetes de código abierto. Recomendamos usar siempre este canal. El entorno contiene un "paquete de idioma" (*language pack*) de español que permite cambiar el interfaz de JupyterLab al español.

En la terminal, el nuevo entorno `jupyterlab` se activa con el comando `conda activate jupyterlab`, y se desactiva con el comando `conda deactivate`.

### Entorno básico de Python

Un entorno minimalista con Python (3.12) y nada más puede ser creado con este comando: `conda create --yes -n python -c conda-forge python=3.12`. Si omites la versión de Python, la versión más reciente será instalada. Si omites el argumento `--yes`, tendrás que dar tu aprobación para completar la instalación.

### Añadir más paquetes a un entorno

Podemos añadir paquetes adicionales a un entorno utilizando `conda install` luego de activar el entorno, manteniendo la referencia a `conda-forge`. Por ejemplo:
```bash
conda install -c conda-forge seaborn
```

## Alternativas a conda

`conda` es muy popular en ámbitos científicos y de ciencia de datos, ya que aborda muy bien el tipo de necesidades y desafíos comunes en estas áreas. En el uso de Python más general, el ecosistema de herramientas para la instalación de paquetes y gestión de entornos es más complejo.

Para la instalación y gestión de paquetes, la herramienta más universal es [**pip**](https://es.wikipedia.org/wiki/Pip_(administrador_de_paquetes)) (ver también [este excelente artículo](https://www.programaenpython.com/avanzado/gestion-de-dependencias-en-python-con-pip/)). Actualmente, la herramienta [**uv**](https://www.mostapha.dev/blog/uv-gestor-paquetes-python-2025) está cobrando auge, ya que es mucho más rápida y cubre más capacidades, incluyendo la gestión de entornos.

## Referencias y recursos

- En [este sitio (CIDE, Centro de Investigación y Docencias Economicas, A.C., México)](https://rafneta.github.io/CienciaDatosPythonCIDE/Laboratorios/Lab1/instalacion.html) puedes encontrar más información sobre el uso de conda. 
- Aquí ponemos unos videos en YouTube que muestran el proceso de instalación de Miniconda en Windows
    - [Descargar e instalar miniconda](https://www.youtube.com/watch?v=oE0JFNipLkA).
    - [Instalación Miniconda Python y Jupyter](https://www.youtube.com/watch?v=E2fKTS8slLo). Este video también muestra un poco sobre el uso de conda
    - [Descarga e Instalación de Miniconda y Visual Studio Code](https://www.youtube.com/watch?v=sT44XmAuSsE). Ignorar la parte sobre instalación de Visual Studio Code.
- Para más información sobre el uso de la **terminal** (*shell*) en macOS y Linux, te recomendamos el tutorial [La Terminal de Unix](https://swcarpentry.github.io/shell-novice-es/), de The Carpentries. La terminal PowerShell en Windows se comporta de manera similar.
- Además de información derivada de los enlaces externos ya presentados, esta página contiene algunos materiales del tutorial [Análisis y visualización de datos usando Python](https://datacarpentry.org/python-ecology-lesson-es/index.html), de [The Carpentries](https://carpentries.org).

### En inglés

- [Esta página](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) contiene instrucciones detalladas de instalación de Miniconda.
- [Este excelente tutorial](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/) de [The Carpentries](https://carpentries.org) contiene información aún más extensa sobre conda.
- [Breve reseña](https://foundations.projectpythia.org/foundations/conda.html) sobre el uso de conda para gestionar entornos de Python, de [Project Pythia](https://projectpythia.org/).
