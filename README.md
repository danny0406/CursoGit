# Curso de Git y Github

## Indice


## 1. Introduccion a Git
### 1.1. ¿Qué es git?

Es importante dejar claro que git no es lo mismo que GitHub, git es un sistema de control de versiones Open Source creado en el año 2005 por Linus Torvalds, el creador de Linux, por otro lado GitHub es un servicio de alojamiento para proyectos versionados con git, de esta forma podemos tener una copia local y una remota de nuestros repositorios.

Con git podemos entre otras cosas: tener un control de ediciones versionadas, regresar a versiones anteriores de nuestros proyectos, revisar el registro de cambios y crear ramas experimentales o mejoras paralelas al proyecto troncal.
- **¿Qué es el control de versiones?**
    Los sistemas de control de versiones son un tipo de software que ayuda a hacer un seguimiento de los cambios realizados en el código a lo largo del tiempo. 

    **Articulo :** (Learn Microsoft, ¿Qué es el control de versiones?) https://learn.microsoft.com/es-es/devops/develop/git/what-is-version-control
### 1.2. Instalación 
#### 1.2.1. Instalacion en Windows de Git y GitBash

Cuando instales Git Bash en Windows debes elegir si prefieres trabajar con la forma de Windows o la forma de UNIX (Linux y Mac).
Los comandos de UNIX son los más comunes entre los equipos de desarrollo.

#### Pasos

1. **Ir a la página de Github:** https://git-scm.com/downloads
2. **Descargar el instalador de Windows**
3. **Se debe iniciar el instalador con las siguientes configuraciones**
    - Asegurarse de marcar la opción **Git Bash**
    - **Activar TrueType** (Mejora las fuentes cuando usas la línea de comandos)
    - Marcar **Git from the command line and also from 3rd party software** (Recomendado)
    - Marcar **use the OpenSSL library**
    - Marcar **checkout Windows-style, commit unix-style line endings** (Compatibilidad con UNIX y Linux)
    - Marcar **MinTTY**
    - Ejecutar **Git Bash**

#### 1.2.2. Instalacion de Git en Linux

Este realiza con la ejecucion de un comando especifico para cada distribucion de Linux.

**Cada distribución tiene su comando especial y debes averiguar cómo funciona para poder instalar Git.**

- En las distribuciones derivadas de Debian **(como Ubuntu)** el comando especial es **`apt-get`** 
- En **Red Hat** es **`yum`** y en **`ArchLinux`** es **`pacman`**.

Antes de hacer la instalación, debemos hacer una actualización del sistema. En nuestro caso, los comandos para hacerlo son **`sudo apt-get update`** y **`sudo apt-get upgrade`**.

Con el sistema actualizado, ahora sí podemos instalar Git y, en este caso, el comando para hacerlo es **`sudo apt-get install git`**. 

Para verificar que Git fue instalado correctamente con el comando **`git --version`**.


### 1.3. Configuración básica
Es importante configurar al menos un nombre de usuario y un correo electrónico, para ello escribes en la terminal `git config --global user.name ‘tunombre’`, pasando entre comillas tu nombre de usuario y `git config --global user.email tuemail` pasando sin comillas tu email.

### 1.4. Inicializar un repositorio
Para que la carpeta de un proyecto en tu equipo pase a ser un repositorio de git debes inicializarla, en la terminal debes posicionarte en la carpeta del proyecto y escribir `git init`, esto creará una carpeta oculta de nombre .git la cual contiene toda la información del versionamiento.

A continuación se hace necesario comprender los estados de git en nuestro repositorio local y los comando necesarios para movernos entre ellos.

En la imagen de referencia se describen tres estados: el working directory, este es el sistema de archivos en el cual trabajamos, el staging area, un área temporal en el que añadimos los archivos cuyos cambios estamos por enviar a git y el repository, donde se versiona nuestro trabajo.
## 2. States y commits
### 2.1. ¿Qué es el staging?
 Crear un área en la memoria RAM, que conocemos como **Staging**, que guardará temporalmente nuestros archivos **(cuando ejecutemos un comando especial para eso)** y nos permitirá, más adelante, guardar estos cambios en el repositorio **(también con un comando especial)**.
 ### 2.2. Ciclo de vida de los archivos en Git:

![ciclo de vida en git](https://git-scm.com/book/en/v2/images/lifecycle.png "ciclo de vida en git")

Cuando trabajamos con Git, nuestros archivos pueden vivir y moverse entre **4 diferentes estados:**

- **Archivos Untracked:** Son archivos que NO viven dentro de Git, solo en el disco duro. Nunca han sido afectados por **`git add`**, así que Git no tiene registros de su existencia.

- **Archivos Unstaged:** Entiendelos como archivos **“Tracked pero Unstaged”**. Son archivos que viven dentro de Git pero no han sido afectados por el comando **`git add`** ni mucho menos por **`git commit`**. Git tiene un registro de estos archivos pero está desactualizado, sus últimas versiones solo están guardadas en el disco duro.

- **Archivos Staged:** Son archivos en Staging. Viven dentro de Git y hay registro de ellos porque han sido afectados por el comando **`git add`**, aunque no sus últimos cambios. Git ya sabe de la existencia de estos últimos cambios pero todavía no han sido guardados definitivamente en el repositorio porque falta ejecutar el comando **`git commit`**.

**`git add <archivo>`** Añade el archivo que le pasemos a staging area, y que luego estará en el commit.

**`git add <archivo1> <archivo2>`** Añade varios archivos a staging.

**`git add .`** El **"."** agrega todo a staging.

- **Archivos Tracked:** Son los archivos que viven dentro de Git, no tienen cambios pendientes y sus últimas actualizaciones han sido guardadas en el repositorio gracias a los comandos **`git add`** y **`git commit`.**

**Recuerda que hay un caso muy raro donde los archivos tienen dos estados al mismo tiempo: Staged y Untracked.**  
Esto pasa cuando guardas los cambios de un archivo en el área de **Staging (con el comando `git add`)** pero, antes de hacer commit para guardar los cambios en el repositorio, haces nuevos cambios que todavía no han sido guardados en el área de **Staging .**

Para comprobar el estado de los archivos escribimos **`git status`**, de esta forma sabrás cuales están en el staging area listo para ser enviados al repositorio.
## 3. Ramas, merge y conflictos.
### 3.1. Ramas o Branch's
![Image of git branch schema](https://s3.amazonaws.com/media-p.slid.es/uploads/843308/images/4760613/git-flow-commands-without-flow.png)
###  ¿Qué es un Branch (Rama)?
Una rama o branch es una versión del código del proyecto sobre el que estás trabajando. Estas ramas ayudan a mantener el orden en el control de versiones y manipular el código de forma segura.
 
                        **Insertar imagen**

En otras palabras, un branch o rama en Git es una rama que proviene de otra. Imagina un árbol, que tiene una rama gruesa, y otra más fina, en la rama más gruesa tenemos los commits principales y en la rama fina tenemos otros commits que pueden ser de hotfix, devlopment entre otros.ㅤ
### Para crear una nueva rama
**`git branch <nombre_rama>`**

 Por ejemplo: **`git branch someTest`**

### Para cambiarse de rama
**`git checkout <nombre_rama>`** 

Por ejemplo: **`git checkout mi-rama`**

**`git switch <nombre_rama>`** 

Por ejemplo: **`git switch mi-rama`**

### Trabaja en tu rama
Dentro de tu rama puedes trabajar normal, hacer tus commits y avanzar en el proyecto, pero lo que haces está sólo en esa rama.

Si cambias de rama sin más lo que hayas hecho en esa rama no lo vas a ver.

Para poder juntar todo tienes que **mergear** (fundir o fusionar) las ramas.

### 3.2. Merge
### ¿Qué es un Merge?
Hacer un merge es la fusion de dos ramas, debes estar sobre la rama que quieres que permanezca (Por ejemplo: hacer un merge de un feature a la rama develop).

**`git merge <Nombre rama a fusionar>`**

**Crear un nuevo commit en la rama master combinando**
**los cambios de la rama cabecera:**

- **`git checkout master`**
- **`git merge cabecera`**


**Crear un nuevo commit en la rama cabecera combinando los cambios de cualquier otra rama:**

- **`git checkout cabecera`**
- **`git merge <cualquier-otra-rama>`**

Debemos tomar en cuenta que al fusionar dos ramas, pueden ocasionarse **conflictos.**
### 3.3. Conflictos
### Solución de conflictos al hacer un merge

**Git nunca borra nada a menos que nosotros se lo indiquemos.** Cuando usamos los comandos **`git merge`** o **`git checkout`** estamos cambiando de rama o creando un nuevo commit, no borrando ramas ni commits **(recuerda que puedes borrar commits con `git reset` y ramas con `git branch -d`)**.

Git es muy inteligente y puede resolver algunos conflictos automáticamente: cambios, nuevas líneas, entre otros. Pero algunas veces no sabe cómo resolver estas diferencias, **por ejemplo, cuando dos ramas diferentes hacen cambios distintos a una misma línea.**

Esto lo conocemos como conflicto y lo podemos resolver manualmente, solo debemos **hacer el merge, ir a nuestro editor de código y elegir si queremos quedarnos con alguna de estas dos versiones o algo diferente.** Algunos editores de código como **VSCode** nos ayudan a resolver estos conflictos sin necesidad de borrar o escribir líneas de texto, basta con hundir un botón y guardar el archivo.

Recuerda que siempre debemos crear un nuevo commit para aplicar los cambios del merge. Si Git puede resolver el conflicto hará commit automáticamente. Pero, en caso de no pueda resolverlo, debemos solucionarlo y hacer el commit.

Los archivos con conflictos por el comando **`git merge`** entran en un nuevo estado que conocemos como **Unmerged**. Funcionan muy parecido a los archivos en estado **Unstaged**, algo así como un estado intermedio entre **Untracked** y **Unstaged**, solo debemos ejecutar **`git add`** para pasarlos al área de staging y **`git commit`** para aplicar los cambios en el repositorio.
