CURSO GIT 
===================
![](https://git-scm.com/images/logo@2x.png)
###Datos de git 

* Un dash ( - ) significa que solo se digita un caracter 
* Dos dash ( -- ) significa que va una palabra 
### Ej:
git status -s **(un dash)**
git config --global  **(dos dash)**

## Configuracion Global 

git config --global user.name "leone2016" 
git config --global user.email "lmedina@gi.com"
git config --global -e  **(:wq salir)** 

ls -al **(lista de todos los archivos y carpetas)**
## Hola Mundo GIT
Codigo Git  |  Explicación
------------- | -------------
git init | inicia
git status | rojo todo lo que existe nuevo o modificado
git add . | **agrega todos los archivos para que este pendiente del cambio STAGED**
git add *.png | **sube todos los archivos png del directorio actual**
git add "*.png" |**sube todos los archivos png de TODO el proyecto**
git add css/ | **agrega todos los archivos que haya dentro de la carpeta css**
git add -A | ** agrega todos los archivos que fueron modificados**
git add --all | ** agrega todos los archivos **
git add <lista de archivos> |  **agrega los archivos que listemos**
git add pdf/*.pdf  | **Agrega todos los PDFs dentro de la carpeta Pdf**
git add pdf/ | **Agrega todos los archivos dentro de la carpeta pdf**
git reset *.xml | ** quita todos los archivos xml que esten en el STAGE ( despues de git add )**
git status | **todo aparece en verde listo para el snapshot - foto **
git status -s | **muestra una version resumida del status normal **
git status -s -b | ** muestra simplificado y la rama actual
git commit -m "toma una foto" | ** primera foto del los archivos - folders **
git commit --amend -m "edita comit"  | **edita un commit en el caso que se haya cometido un error **
git commit | **permite ingresar un mensaje multilinea, para editar hay que presionar A **

###Recuperar cambio al ultimo punto del commit (local)
 `git chechut --.`

## Verificar commits
Codigo Git  |  Explicación
------------- | -------------
git log |  **muestra de mas reciente al mas viejo** 

## Informacion git log

* cuando se escribe git log se muestran todos los commits que se hayan realizado, (HEAD->master) se refiere al ultimo commit en la rama actual

Codigo Git  |  Explicación
------------- | -------------
git log --oneline |** muestra una sola linea de git log **
git log --oneline --decorate --all --graph | ** all: muestra la informacion de las diferentes ramas, decorate y graph: se dibija unas viñetas 

## ALIAS para comandos git

git config --global alias.lg "log --oneline --decorate --all --graph" ** solo hay que digitar git lg**


# VIAJES EN EL TIEMPO GIT 
git diff **Esto sirve para compara de como esta el archivo antes y despues** 
git diff --staged ** para comopara  el archivo cuando ya se digito git add . **
git reset HEAD nombrearchivo.txt  ** Quita el archivo que se encuentre en stage, HEAD hace referencia al ultimo commit que hayamos hecho** 
git reset --soft HEAD^ (cuando tengo cambios en un archivo debian ser guardados en un commit pasado (HEAD), ojo no hay)
	* Paso 1: git reset --soft HEAD^   **digitar esto es consola**
	* Paso 2: git commit -am "poner una descripcion"
	* No hay que escribir primero git add . ya que esto crearia otro stage para un nuevo commit

	
## Viajes en el tiempo

>clase 20 

## Elimiar o cambiar de nombre a archivos 
Si se elimina es necesario digitar 

	git status
	git add -u **actualiza los artchivos** 
	git add -A
	git add -m "mensaje" 

## ignorar archivos no deseados

* crear un archivo llamado .gitignore 
nombre_directorio/ **Todo lo de la carpeta no se agrega**
*.extAarchivo
 
# Ramas 

Las ramas ayudan cuando se quieren agragar funcionalidades a nuestro programa que eventualmente se unan a la rama principal ó a otra rama.

Una nueva rama es una linea en el tiempo totalmente aparte.


## Merge - uniones
* Fast-forward: se dispara cuando git detecta que no hay ningun cambio en la rama principal y los cambios pueden ser integrados de forma normal o trasparente y cada uno de los commits formaran parte de la rama
* uniones automatica: git detecta que en la rama principal hubo algun cambio en la rama secundaria, cuando no se modificaron lineas iguales y se visualiza que las ramas se unieron sin problema
* union manual: git no puede hacerlo de forma automatica 

# Practica de Merge  Fast-forward:

Codigo Git  |  Explicación
------------- | -------------
git branch nombreNuevaRama  | ** suponiendo el caso que tengo una funcionalidad que aun no se si esta bien o si se va a implementar
git branch | **muestra las ramas actuales**
git checkout nombreRamaAcambiar | ** para cambiar de una rama a otra ** 
git checkout -b nombreRamaAcambiar | ** para cambiar de una rama a otra (-b) se mueve a la nueva rama ** 
git branch | ** verifica que se haya hecho el cambio de rama**
git merge rama-paralela(desarrollo) | **estando en la rama master -- para unir ramas **
git branch -d nombreRama | ** ELIMINA la rama que ya no se necesite **


## TAG - Etiquetas 
> Se utilizapara marcar releases de nuestra aplicacion ó programa. 

Codigo Git  |  Explicación
------------- | -------------
git tag nombreDeltag  | ** crear un tag **
git tag | **muesta los tags que tenga º
git tag -d nombreDelTag | ** BOrrar un tag** 
git tag -a v1.0.0 -m "versión 1.0.0" | **crear un tag con version y mensaje**
git tag | ** se muesta solo la version del paso anterior ** 
git tag - v0.1.0 hashCommit -m "mensaje tag" | **AGREGAR UN TAG A UN COMMIT ANTERIOR - hashCommit se lo puede encontrar en git log o en git o bitBucket**
git show v1.0.0 | ** muestra el mensaje de la version ** 


## STASH 
* Salva todo el proyecto de forma temporal, esto se utiliza por ejemplo cuando se esta trabajando en una funcionalidad pero el Dueño del producto quiere que ya se suba
ANTES DE HACER COMMIT
git stash  ó git stash save ** Salva y restaura el ultimo commit ""

git log ** se visualiza un estado WIP (work in Prosses)
git stash list ** muestra todos los stash creados **
git stash drop **elimina los stash de la posicion 0 **
git stash drop ** BORRAR todos los stash**
git stash apply stash@{1} **restaura el stash den la posicion 1 ** 
git stash pop = git stash apply + git stash drop 

* Mensajes en los Stash 
git stash save "mensaje para tener una identifiacion" 

# GIT REBASE

 

######Crear .md modo grafico [Editor.md](https://pandao.github.io/editor.md/en.html "Heading link")


