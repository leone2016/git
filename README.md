CURSO GIT 
===================
![](https://git-scm.com/images/logo@2x.png)
### Datos de git 

* Un dash ( - ) significa que solo se digita un carácter 
* Dos dash ( -- ) significa que va una palabra 
### Ej:
* git status -s **(un dash)**
* git config --global  **(dos dash)**

## Configuracion Global 

	git config --global user.name "leone2016" 
	git config --global user.email "lmedina@gi.com"
	git config --global -e  **(:wq salir)**

ls -al **(lista de todos los archivos y carpetas)**
## Hola Mundo GIT
Código Git  |  Explicación
------------- | -------------
git init | inicia
git status | rojo todo lo que existe nuevo o modificado
git add . | **agrega todos los archivos para que este pendiente del cambio STAGED**
git add *.png | **sube todos los archivos png del directorio actual**
git add "*.png" | **sube todos los archivos png de TODO el proyecto**
git add css/ | **agrega todos los archivos que haya dentro de la carpeta css**
git add -A | **agrega todos los archivos que fueron modificados**
git add --all | **agrega todos los archivos**
git add <lista de archivos> |  **agrega los archivos que listemos**
git add pdf/*.pdf  | **Agrega todos los PDFs dentro de la carpeta Pdf**
git add pdf/ | **Agrega todos los archivos dentro de la carpeta pdf**
git reset *.xml | **quita todos los archivos xml que estén en el STAGE ( despues de git add )**
git status | **todo aparece en verde listo para el snapshot - foto**
git status -s | **muestra una versión resumida del status normal**
git status -s -b | **muestra simplificado y la rama actual**
git commit -m "toma una foto" | **primera foto de los archivos - folders**
git commit --amend -m "edita comit"  | **edita un commit en el caso que se haya cometido un error**
git commit | **permite ingresar un mensaje multilínea, para editar hay que presionar A**

### Recuperar cambio al último punto del commit (local)

`git checkut --.`

## Verificar commits
Código Git  |  Explicación
------------- | -------------
git log |  **muestra de más reciente al más viejo**

## Informacion git log

* cuando se escribe git log se muestran todos los commits que se hayan realizado, (HEAD->master) se refiere al último commit en la rama actual

Código Git  |  Explicación
------------- | -------------
git log --oneline | **muestra una sola línea de git log**
git log --oneline --decorate --all --graph | **all: muestra la información de las diferentes ramas, decorate y graph: se dibija unas viñetas**

## ALIAS para comandos git

git config --global alias.lg "log --oneline --decorate --all --graph" **solo hay que digitar git lg**


# VIAJES EN EL TIEMPO GIT 

Código Git  |  Explicación
------------- | -------------
git diff | **Esto sirve para comparar cómo está el archivo antes y despues**
git diff --staged | **para comparar  el archivo cuando ya se digito git add .**
git reset HEAD nombrearchivo.txt  | **Quita el archivo que se encuentre en stage, HEAD hace referencia al ultimo commit que hayamos hecho**
git reset --soft HEAD^ | (cuando tengo cambios en un archivo debían  ser guardados en un commit pasado (HEAD), ojo no hay)

	Paso 1: git reset --soft HEAD^   **digitar esto es consola**
	Paso 2: git commit -am "poner una descripción"
	No hay que escribir primero git add . ya que esto crearía otro stage para un nuevo commit

	
## Viajes en el tiempo

>clase 20 

## Eliminar o cambiar de nombre a archivos 
Si se elimina es necesario digitar 

	git status
	git add -u **actualiza los archivos**
	git add -A
	git add -m "mensaje" 

## ignorar archivos no deseados

* crear un archivo llamado .gitignore 

	nombre_directorio/ **Todo lo de la carpeta no se agrega**
	*.extAarchivo
 
# Ramas 

Las ramas ayudan cuando se quieren agregar funcionalidades a nuestro programa que eventualmente se unan a la rama principal ó a otra rama.

Una nueva rama es una línea en el tiempo totalmente aparte.


## Merge - uniones
* Fast-forward: se dispara cuando git detecta que no hay ningún cambio en la rama principal y los cambios pueden ser integrados de forma normal o trasparente y cada uno de los commits formaran parte de la rama
* uniones automáticas: git detecta que en la rama principal hubo algun cambio en la rama secundaria, cuando no se modificaron líneas iguales y se visualiza que las ramas se unieron sin problema
* unión  manual: git no puede hacerlo de forma automática 

# Practica de Merge  Fast-forward:

Código Git  |  Explicación
------------- | -------------
git branch nombreNuevaRama  | **suponiendo el caso que tengo una funcionalidad que aun no se si está bien o si se va a implementar**
git branch | **muestra las ramas actuales**
git checkout nombreRamaAcambiar | **para cambiar de una rama a otra**
git checkout -b nombreRamaAcambiar | **para cambiar de una rama a otra (-b) se mueve a la nueva rama**
git branch | **verifica que se haya hecho el cambio de rama**
git merge rama-paralela(desarrollo) | **estando en la rama master -- para unir ramas**
git branch -d nombreRama | **ELIMINA la rama que ya no se necesite**


## TAG - Etiquetas 
> Se utiliza para marcar releases de nuestra aplicación ó programa. 

Código Git  |  Explicación
------------- | -------------
git tag nombreDeltag  | **crear un tag**
git tag | **muestra  los tags que tenga**
git tag -d nombreDelTag | **BOrrar un tag**
git tag -a v1.0.0 -m "versión 1.0.0" | **crear un tag con versión y mensaje**
git tag | **se muestra  solo la versión  del paso anterior**
git push --tags | sube los tags al repositorio en la nube
git tag - v0.1.0 hashCommit -m "mensaje tag" | **AGREGAR UN TAG A UN COMMIT ANTERIOR - hashCommit se lo puede encontrar en git log o en git o bitBucket**
git show v1.0.0 | **muestra el mensaje de la versión **


## STASH 
* Salva todo el proyecto de forma temporal, esto se utiliza por ejemplo cuando se está trabajando en una funcionalidad, pero el Dueño del producto quiere que ya se suba

>ANTES DE HACER COMMIT

Código Git  |  Explicación
------------- | -------------
git stash  ó git stash save | **Salva y restaura el ultimo commit**
git log | **se visualiza un estado WIP (work in Prosses)**
git stash list | **muestra todos los stash creados**
git stash drop | **elimina los stash de la posición  0**
git stash drop | **BORRAR todos los stash**
git stash apply stash@{1} | **restaura el stash den la posición  1**
git stash pop = git stash apply + git stash drop 

* Mensajes en los Stash 

git stash save "mensaje para tener una identificación" 

## GIT REBASE

Se planta un problema para un mejor entendimiento

> Tenemos nuestra línea del tiempo **MASTER** (branch) con un commit y  se crea una rama llamada **misiones-completadas**
>>Después  de trabajar en la rama **misiones-completadas** con dos commits, luego de un tiempo otra persona del equipo agrega dos commits a **Master** que son importantes para la rama **misiones-competadas** aqui se ejecuta :: 

[![](https://wac-cdn.atlassian.com/dam/jcr:d3b2abde-d06a-47b6-8955-5f3ef34e0237/03.svg?cdnVersion=jy)](https://wac-cdn.atlassian.com/dam/jcr:d3b2abde-d06a-47b6-8955-5f3ef34e0237/03.svg?cdnVersion=jy)

-- feature = misiones-completadas --

--explicación general--

Código Git  |  Explicación
------------- | -------------
git checkout rama-feature | **se mueve de rama**
git rebase master	| **luego mueve el puntero de la rama feature a la de master, después agrega los dos commits de la rama misiones**

### Rebase Iteractivo
Mueve el número de commits que se le indique, a un área temporal

Código Git  |  Explicación
------------- | -------------
git rebase -i HEAD~3  | Mueve los tres últimos commits

>**¿Para qué nos serviría eso?**

	1. Ordenar commits
	Corregir mensajes de los commits
	Unir commits
	Separar commits

## Ejercicio práctico Rebase Iteractivo
Código Git  |  Explicación
------------- | -------------
git branch  | visualiza las rama existentes
git chekout rama-misiones-completadas | se mueve de rama
git rebase master | EN la rama-misiones-completadas se mueve todo arriba de master
git chekout mastes | nos movemos a Master para realizar un merge con misiones-completadas
git merge rama-misiones-completadas | en la rama master decimos que se una a la rama-misiones-completadas


![](https://raw.githubusercontent.com/leone2016/git/master/Captura.JPG)
>  Ej. antes del rebase--

![](https://raw.githubusercontent.com/leone2016/git/master/despues.JPG)
>  Ej. después  del rebase

>imagenes tomadas del curso de UDEMY :: GIT+GitHub: Todo un sistema de control de versiones de cero

 ## Rebase - Squash 
 Cuando se desea unir más de un commit, ya sea porque son los mismos o por  algun otro problema
Squash = tener dos cosas que se chocan y se unen.

git rebase -i HEAD~4 | **crea un rebase iteractivo - Muestra los ultimos 4 commits**

> Al ejecutar este comando muestra los 4 commits solicitados ( `pick 158ba9e Descripcion del commit (mas viejo)....`)

>Pasos para Generar Git Squash

	1. git rebase -i HEAD~4
	2. aparece varios pick, poner s en cualquiera de esos pick ya que eso unirá de abajo hacia arriba
	3. ingresar el mensaje para unir los commits que se necesite 
	:wq

# GIT REMOTE 
============

git remote add origin UrlGitremoto
git remote -v | muestra los diferentes lugares donde se guardados
git push -u origin master | -u nos ayuda a que la próxima vez que queramos hacer push, no necesitemos especificar la rama

## Git remote tags 

git push --tags


###### Crear .md modo grafico [Editor.md](https://pandao.github.io/editor.md/en.html "Heading link")


