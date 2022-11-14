---
toc: true
toc-depth: 4
linkcolor: blue
---

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

<img     style="float: left;" src="OHWe.png"width=15% height=15%>

# Instalación de JupyterLab y Conda

Instalaremos la aplicación `JupyterLab` en tu computadora, utilizando el sistema `conda`. 

[Conda](https://docs.conda.io) es un administrador de paquetes y entornos para cualquier lenguaje de programación, pero especialmente popular en la comunidad de usuarios de Python. Permite la instalación de múltiples versiones de paquetes de software o librerías y de sus dependencias en diferentes entornos, con la capacidad de cambiar fácilmente de un entorno a otro. Puede ser instalado en tu computadora sin necesidad de tener privilegios administrativos. 

Conda funciona tanto en Windows como en macOS y Linux. Conda y los paquetes disponibles a través de conda son gratuitos y bajo licencias de código abierto. Hay diferentes maneras de instalar conda. Aquí utilizaremos [Miniconda](https://conda.io/miniconda.html), una distribución ligera de conda. 

## Instalar Miniconda

Incluimos instrucciones breves para instalar Miniconda.

### Windows

En la página https://docs.conda.io/en/latest/miniconda.html, bajo "Latest Miniconda Installer Links", baja el instalador `Miniconda3 Windows 64bit`. Si tu computadora es vieja, tal vez la versión 32bit es la indicada. En Windows 10:

- Haz doble clic en el archivo instalador después de bajarlo.
- Selecciona la opción para instalar como usuario local solamente (local user only).
- Acepta la ruta (*path*) de archivos de instalación de defecto, que probablemente será: `C:\Users\MIPERFIL\miniconda3`
- En la ventana "Advanced Installation Options", remueve la selección de ambas cajas ("Add Miniconda3 ..." y "Register Miniconda3 ...")
- En la ventana "Completing Miniconda3", remueve la selección de ambas cajas.

Cuando la instalación ha concluído, abre el "Anaconda Powershell Prompt" desde el menú de Start. Puedes comprobar que funciona bien corriendo el comando `conda list`.

### macOS o Linux

En la **terminal** (*shell*, generalmente la terminal tipo "bash"):

```bash
# En macOS
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
# En Linux
url=https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

wget $url -O miniconda.sh
bash miniconda.sh -b -p $HOME/miniconda3
```

Si el instalador te pregunta si quieres que inicialize Miniconda3 corriendo `conda init` ("Do you wish the installer to initialize Miniconda3 by running conda init?"), selecciona "yes". Si concluye sin hacer esa pregunta, ejecuta el siguiente comando: `./miniconda3/bin/conda init`. Por último, ejecuta el comando `conda update conda --yes`

## Crear entorno conda para JupyterLab

Con conda ya instalado, el último paso es crear un entorno de conda que usaremos para correr la aplicación JupyterLab. Además de JupyterLab, este entorno incluirá Python 3.10 y dos paquetes de Python de uso amplio, `Pandas` y `Matplotlib`.

En la terminal donde instalaste miniconnda, corre este comando de `conda create` para crear el entorno: `conda create --yes -n jupyterlab -c conda-forge python=3.10 jupyterlab jupyterlab-language-pack-es-ES nb_conda_kernels pandas matplotlib-base`

Este entorno contiene un "paquete de idioma" (*language pack*) de español que permitirá cambiar el interfaz de JupyterLab al español.

## Referencias y recursos

- En [este sitio (CIDE, Centro de Investigación y Docencias Economicas, A.C., México)](https://rafneta.github.io/CienciaDatosPythonCIDE/Laboratorios/Lab1/instalacion.html) puedes encontrar más información sobre el uso de conda. 
- Para más información sobre el uso de la **terminal** (*shell*) en macOS y Linux, te recomendamos el tutorial [La Terminal de Unix](https://swcarpentry.github.io/shell-novice-es/), de The Carpentries. La terminal PowerShell en Windows se comporta de manera similar.
- Además de información derivada de los enlaces externos ya presentados, esta página contiene algunos materiales del tutorial [Análisis y visualización de datos usando Python](https://datacarpentry.org/python-ecology-lesson-es/index.html), de [The Carpentries](https://carpentries.org).

### En inglés

- [Esta página](https://conda.io/projects/conda/en/latest/user-guide/install/index.html) contiene instrucciones detalladas de instalación de Miniconda.
- [Este excelente tutorial](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/) de [The Carpentries](https://carpentries.org) contiene información aún más extensa sobre conda.
- [Breve reseña](https://foundations.projectpythia.org/foundations/conda.html) sobre el uso de conda para gestionar entornos de Python, de [Project Pythia](https://projectpythia.org/).