# Tutorial de Github

Sean bienvenidos a este tutorial. El propósito aquí es describir las instrucciones mínimas necesarias para poder usar git y github para crear un historial de desarrollo y colaborar en el desarrollo de proyectos. 

Inicialmente vamos a configurar todo con la tecnología HTTPS para facilitar las cosas. Posteriormente usaremos la tecnología SSH. 

Al final haré un resumen de las lineas de codigo necesarias para tener un repositorio en github conectado a tu pc y listo para producción y colaboración. 

# Cómo seguir este tutorial
En el "How to do" hay información de cómo hacer cosas puntuales. La mayor parte de la información está contenida en esta sección.

Para navegar el documento, usar usar el Índice. 

Si tienen comentarios para mejorar la organización y/o redacción de este documento, agradezco sus aportes (idealmente por pull requests). 


# Índice
 ^e4291a
- [Ejemplos](#Ejemplos) 
- [Resumen de manejo de Git](#Resumen%20de%20manejo%20de%20Git)
- [How to do](#How%20to%20do)

# Ejemplos

[Índice](#Índice)


## Ejemplo con proyecto existente

```bash
git init 
git branch -m main
git add . 
git commit -m "First commit to add current proyect files"
git remote add origin https://github.com/blackcuarzo/GithubExampleHTTPS.git
git pull origin main --allow-unrelated-histories
git push origin main 
```

## Ejemplo con proyecto fullstackOpen


Primero creo un par de carpetas de acuerdo a la estructura de https://fullstackopen.com/en/part0/fundamentals_of_web_apps#exercises-0-1-0-6

Para empezar a hacer desarrollo local con Git:

```bash
git init 
git branch -m main
git add . 
git commit -m "First commit to add current proyect files"
```

Luego cuando quiera montar el desarrollo en GitHub uso: 

```sh
git remote add origin <url repositorio remoto>
git pull origin main --allow-unrelated-histories
```

Ejemplo con HTTPS: 
```sh
git remote add origin https://github.com/blackcuarzo/FullStackOpen.git
git pull origin main --allow-unrelated-histories
git push origin main
```

# Resumen de manejo de Git: 
[Índice](#Índice)

Supongamos que vamos a implementar un proyecto sencillo para el seguimiento de un proyecto con varias carpetas y archivos. 

- Carpeta madre, contenedora del proyecto
	- Archivo A
	- Carpeta Hija 1
		- Archivo A1
		- Archivo B1
	- Carpeta Hija 2
	- Carpeta Hija 3
	- ....


El procedimiento para tener este proyecto listo para el desarrollo seria:

1. Añade los archivos

`git init`: Nos sirve para iniciar un repositorio en la carpeta actual 

`git branch -m main`: para cambiar de master a main, un requerimiento de github

`git add .`: Incluimos por primera vez todos los archivos presentes en nuestra carpeta del proyecto

`git commit -m 'First commit'`: Primer commit para añadir todos los archivos y carpetas del proyecto.

![](Media/Pasted%20image%2020211128202046.png)

Si te arroja un error en este punto que dice "Please tell me who you are...", es porque aun no tienes configurado git, para esto usa los comandos 

`git config --global user.email "tu@email.com"` 
`git config --global user.name "Tu Nombre"`
`git config --list` : para ver la informacion de la configuracion
Otra forma de hacer un mensaje de commit: 
Cuando usamos el comando `git commit` sin el mensaje de commit, git nos abre una ventana en el editor `VIM`. Para empezar a escribir en esta ventana se debe usar 
`Esc` + `i`: Con esto entramos en el modo insersion de texto
`Esc` + `Shift`+ `z` +`z`: Con esto se guarda. 

**Otros comandos útiles**
`git show` nos muestra los cambios hechos con el último commit
`git log`: con esto vemos el historial de cambios hechos por cada commit. Hay un código asociado a cada commit, un número de identificación. 
`git diff <identificacion1> <identificacion2>`: Con esto me doy cuenta de cuales son las diferencias entre dos commits

`git checkout` + `ID del commit`: Con esto cargamos un commit previo a partir de su ID o código de identificación, es como si nos transportaramos en el tiempo. 

`git checkout` + `ID del commit` + `nombre-archivo`: Esta es una manera de ir al pasado SOLO con un archivo. 

`git reset --soft` : Recomendado usar `--soft` porque de esta forma 

`git config --list` : para ver la informacion de la configuracion


# How to do:
[Índice](#Índice)

**Previamente**
- Crea una cuenta de github
* Instala **git** en tu pc


## Cómo crear un repositorio en GitHub

- Escribe en tu navegador: github.com/new
- Define tu repositorio como público, dale un nombre a tu gusto y selecciona crear.

## Cómo descargar el repositorio en tu pc:

En una carpeta de tu PC donde desees guardar el repositorio, abre una ventana de comando y usa  el comando: 

`git clone <url>`
Donde `<url>` es la dirección de tu repositorio en github. Esta es la dirección HTTPS de tu repositorio

![[Media/Pasted image 20211125165139.png]]

## Cómo añadir archivos al repositorio

Supongamos que hemos creado un archivo dentro de mi repositorio local. Para añadir los archivos a los cuales git *le va a hacer seguimiendo* o 'tracking', debemos usar el comando `git add`, el cual le 'toma una foto' al archivo o archivos de interés

`git add <nombre_archivo>`

Ej: `git add foo.py`. Donde foo.py es el nombre de mi archivo que voy a guardar en el próximo *commit*

Si queremos empezar a hacer tracking a todos los archivos dentro del repositorio, usamos.

`git add .`

## Cómo hacer un commit al repositorio local

Un commit consiste en un 'guardado fuerte', algo así como cuando jugabas videojuegos y hacías un 'save' del juego en uno de los slots disponibles. 
Commit y add están fuertemente relacionados porque solo se va a hacer un guardado de aquellos archivos que previamente fueron añadidos por medio de add.

Digamos quiero hacer un save a cambios hechos en un archivo llamado `hello.html`. Previamente debo añadirlo: 

`git add hello.html`

Luego debo hacer el commit: 

`git commit -m "message"`

Donde `"message"` es una descripción de los cambios hechos en dicho archivo.

Alternativamente se pueden combinar los comandos add y commit: 

`git commit -am "message"`

Este comando dice: Haga un commit de todos (all) los archivo que han sido cambiados con el mensaje "message"

## Cómo hacer un commit al repositorio remoto

Digamos que previamente hiciste cambios a un archivo local y que además hiciste un git commit. Estos cambios se hacen en el repositorio local y no se ven reflejados en el repositorio remoto. Una forma de ver esto es usando `git status`, donde puedes recibir un mensaje como: 

`On branch Main 
Your branch is ahead of 'origin/main' by 1 commit (use "git push" to publish your local commits)
`

Para hacer un commit al repositorio remoto debemos usar otro comando llamado `git push` para que el repositiorio remoto sea actualizado con los recientes cambios hechos en el repositorio local. 

## Cómo descargar cambios hechos en un repositorio remoto

El comando `git pull` se encarga de esto, haciendo que tu repositiorio local sea igual al repositorio remoto.

`git pull`

## ¿Cómo lidiar con conflictos?

Supongamos que estas trabajando con un colega y ambos hacen cambios a *la misma línea de código*. ¿Cómo solucionar estos coflictos, llamados 'merge conflicts'?

Esto puede ocurrir por ejemplo al usar `git pull` y te encuentras con conflictos con tu repositorio local. 

Un ejemplo (obtenido de las diapositivas de Cs50) sería: 

![[Media/Pasted image 20211127175014.png]]


## Cómo hacer branches y por qué son importantes

A veces quieres hacer un código experimental, o a veces dos personas están haciendo cambios al mismo tiempo en un código, cambios que pueden interferir en lo que está haciendo el otro... Aquí viene el concepto de branch, una forma de desviarse del 'main branch' para hacer estos cambios y posteriormente decidir si incluir estos cambios en la base de código principal o no. 

`git branch` sirve para darme cuenta de donde esta el HEAD, el cual es un apuntador que me dice en que 'rama' o 'branch' de desarrollo estoy. La rama por defecto es 'main', previamente llamado 'master'.  Es común ramificar durante el desarrollo para crear nuevas funcionalidades.

La forma de crear un nuevo branch es usando el comando

`git checkout -b <nombre del branch>` 

La forma de cambiar el 'HEAD' a otro branch, es decir, moverme entre ramas es:

`git checkout <nombre del branch>` 

Para hacer un merge entre dos ramas, por ejemplo para traer los cambios hechos de una nueva funcionalidad a mi rama principal es:

1. Moverme a la rama que va a recibir el código, usualmente la rama de mayor jerarquía. Ej, si tengo las ramas `style` y `main`, me muevo a `main` con `git checkout main`.
2. Luego uso el comando `merge` con la rama de menor jerarquía de donde proceden la funcionalidad. En el ejemplo anterior sería `git merge style`.
3. Si hay 'merge conflicts', solucionarlos y proceder a hacer un commit con la resolución. Ej `git commit -am "Fixed merge conflicts"`

El resultado final será un merge con las nuevas funcionalidades implementadas en un nuevo commit de la rama principal.






## Cómo vincular un repositorio remoto

Digamos no tienes ningún proyecto local creado y tienes una carpeta donde guardas tu desarrollo.

- Carpeta de proyectos
	- Proyecto 1
	- Proyecto 2
	- ....

Y quieres usar un proyecto remoto desde el principio, para esto te recomiendo usar el comando `git clone` en tu **Carpeta de proyectos**

```sh
git clone <url repositorio remoto> NuevoProyecto
```

- Carpeta de proyectos
	- NuevoProyecto
	- Proyecto 1
	- Proyecto 2
	- ....

Si además digamos que llevabas tiempo desarrollando localmente dentro de Proyecto 1, es cuestion de copiar y pegar el contenido de interés desde Proyecto 1 al NuevoProyecto que creaste. Y dentro de NuevoProyecto, usar los comandos add y commit para añadir los nuevos archivos: 

```bash
git add .
git commit -m "First local commit to add pre-existent proyect files"
```

### Alternativa

Otra forma de hacer lo anterior, cuando ya tenemos la carpeta NuevoProyecto con los archivos que hemos desarrollado.

- Carpeta de proyectos
	- NuevoProyecto
	- Proyecto 1
	- Proyecto 2
	- ....

Ubicandonos en la carpeta **NuevoProyecto**

1. Traer el repositorio remoto
```bash
git clone <url repositorio remoto> temp
mv temp/.git .
rm -rf temp
git reset --hard
```

2. Se añaden las carpetas locales presentes.

```bash
git add .
git commit -m "First commit to add current proyect files"
```

### Cuando tienes un repositorio local

Supongamos tienes un proyecto local en el cual estas trabajando, al cual llevas un tiempo haciendole seguimiento por medio de Git. Digamos que quieres subir este proyecto a Github. Para lograrlo debes:

1. Crear un proyecto en Github, asignarle un nombre.
2. Si no tienes un repositorio de Git local, se puede usar el método mencionado anteriormente, o sino usar: 

```bash
git init 
git branch -m main
git add . 
git commit -m "First commit to add current proyect files"
```

3. Una vez tienes un repositorio local de git,  

```bash
git remote add origin <url repositorio remoto>
```

4. Hacer un pull o un fetch + merge

```bash
git fetch origin main 
git merge origin/main --allow-unrelated-histories
```

Lo cual es igual a:

```bash
git pull origin main --allow-unrelated-histories
```

**En resumen tenemos:**

```bash
git remote add origin <url repositorio remoto>
git pull origin main --allow-unrelated-histories
```

## Cómo subir cambios al repositorio remoto

Para este punto tenemos el repositorio local vinculado con el repositorio remoto y podemos subir cualquier cambio hecho en el repositorio local (nuestros commits) al repositorio remoto así:

```bash
git push origin main
```

## SSH

Bueno muchachos iba a explicar esta sección más a fondo, pero me doy cuenta que hay personas que lo han explicado mucho mejor en la internet. Si quieren más detalles de cómo configurar llaves SSH de forma segura, les recomiendo ver el tutorial de git de platzi, hay dos vídeos llamados "Configura tus llaves SSH en local" y  "Conexión a GitHub con SSH" que tienen toda la información necesaria. 

Aqui voy escribir un resumen para futuras referencias: 

1. Crear llaves en el local: 

```bash
ssh-keygen -t rsa -b 4096 -C "tu@email.com"
eval $(ssh-agent -s)
ssh-add ~/.ssh/id_rsa  #o sino la ruta donde se guardo la llave privada ssh
```

2. Luego vas y copias tu llave pública a GitHub 

![](Media/Pasted%20image%2020211130215451.png)

![](Media/Pasted%20image%2020211130215044.png)

![](Media/Pasted%20image%2020211130214631.png)

![](Media/Pasted%20image%2020211130214714.png)

![](Media/Pasted%20image%2020211130214827.png)

Lo unico que cambia es al usar el comando `git remote add`, vas a usar la url SSH

```bash 
git remote add origin <url SSH>
```

Si ya has estado usando una URL HTTPS entonces debes cambiar 

```bash
git remote set-url origin <url ssh de github>
```

Recuerda que puedes verificar la nueva url con `git remote -v`

### Ventajas/importancia de SSH:
- No vas a tener que volver a usar una contraseña para autenticarte al subir un commit, la llave se encarga de todo.
- Es importante el uso de SSH sobretodo a nivel laboral para proteger los datos de la empresa donde trabajas 
- Vas a contar con una seguridad muy fuerte, si además añades una contraseña al momento de crear la llave (es algo que te pide al crearla), es muy dificil sino imposible que te roben una llave privada incluso si te roban tu PC.


## Cómo colaborar con otros

Próximamente más detalles. Por lo pronto se sabe que cada repositorio en Github tiene un dueño y esto se relaciona con el concepto de los pull requests.


