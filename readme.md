## Git - Práctica 1
---
#### 1. ¿Qué comando utilizaste en el paso 11? ¿Por qué?
* **git reset --hard HEAD~1**

`git reset` mueve el puntero y la rama al punto que indiquemos, con "HEAD~1", retrocedemos al commit anterior y con `--hard ` modificamos el working copy dejándolo en el estado en el que estaba en ese punto.

***
#### 2. ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?
* **git reflog**

* **git reset --hard** ***id_commit***

A través de `git reflog` accedemos a todos los estados por los que ha ido pasando nuestro repositorio.

Posteriormente para desplazarnos al commit anterior a la ejecución del `git reset --hard HEAD~1`, podemos copiar el id de dicho commit y ejecutar otro `git reset --hard` seguido de ese identificador. De esta manera volveremos a estar situados en la rama "styled" y no en un *"detached HEAD"*.

NOTA: También podríamos haberlo hecho a través de un "git checkout" seguido del id del commit. Sin embargo, en este caso, tendríamos que crear una "rama temporal" que contenga al fichero y posteriormente mergearlo en la rama styled, para conservar el contenido del fichero.

***
#### 3. El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?
* **git merge --no-ff master**

Tras realizar el `git merge --no-ff` se lanzó por consola el siguiente mensaje: *"Already up-to-date"*.

Lo que significa que la historia (commits) de la rama master ya estaba contenida en styled. De modo que git no realiza dicho merge.

***
#### 4. El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?
* **git merge htmlify**

Tras ejecutar el comando `git merge` apareció el mensaje *"CONFLICT (content): Merge conflict in git-nuestro.md"* 

Este conflicto surge del hecho de que se han modificado las mismas líneas en ambos ficheros. Git no realiza el merge para que podamos resolverlo manualmente.

*NOTA: Para finalizar el merge habría hay que realizar un nuevo commit.

***
#### 5. El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

No, en este caso se realizó un merge *fast-forward*. Lo que quiere decir que el HEAD de master se ha actualizado al HEAD de la rama styled, sin crear un commit de merge adicional. El merge "fast-forward" se puede realizar cuando la rama absorbida (styled) contiene ya el histórico de commits de la rama que absorbe (master). 

***
#### 6. ¿Qué comando o comandos utilizaste en el paso 25?
He ejecutado el comando **git graph** que en realidad es un alias creado a través de las opciones de configuración de git. El script es el siguiente:

`git config --global alias.graph "log --graph --decorate --pretty=oneline"`

Podría haber utilizado también este otro alias que genera un gráfico con ligeras diferencias: 
`git config --global alias.superlog "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"***`

***
#### 7. El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
Sí. Al realizar el merge ha aparecido por consola el mensaje *"Merge made by the 'recursive' strategy."*
Este tipo de merge difiere ligeramente del anterior de tipo "fast-forward", ya que se genera un nuevo commit como resultado del merge.

Este merge podría haber sido "fast-forward" porque bastaría con avanzar el puntero de la rama master al HEAD de la rama styled, para tener mergeados todos los cambios de ambas ramas. Esto es así, porque styled, en el momento de ser absorbida, contenía todos los commits de la rama master.

***
#### 8. ¿Qué comando o comandos utilizaste en el paso 27?
* **git reset HEAD~1**

He utilizado `git reset HEAD~1` en lugar de `git reset --hard HEAD~1` para no perder los cambios del working copy.

***
#### 9. ¿Qué comando o comandos utilizaste en el paso 28?
* **git checkout git-nuestro.md**

He utilizado `git checkout` porque este comando nos permite descartar cambios de nuestro working copy.

***
#### 10. ¿Qué comando o comandos utilizaste en el paso 29?
* **git branch -D title**

He utilizado `git branch -D title`, en lugar de `git branch -d title` porque el parámetro "-D" fuerza el borrado de una rama no fusionada.

Si hubieramos tratado de eliminar la rama mediante utilizando el parámetro "-d" nos habría aparecido el siguiente mensaje *"error: The branch 'title' is not fully merged."* que nos indica que dicha rama no se puede eliminar porque existen modificaciones que se perderían si no hiciéramos un merge. 

***
#### 11. ¿Qué comando o comandos utilizaste en el paso 30?
* **git reflog**
* **git reset --hard** ***id_commit***

A través de `git reflog` tenemos acceso al identificador del commit en el cual se había realizado el merge. Y mediante `git reset --hard` seguido del id del commit regresamos a la situación del merge llevando el working copy también a dicho estado. 

***
#### 12. ¿Qué comando o comandos usaste en el paso 32?
* **git reflog**
* **git checkout** ***id_commit***

Con `git reflog`accedemos al id del primer commit realizado y con git checkout nos desplazamos a ese estado descartando los cambios en el working copy.

***
#### 13. ¿Qué comando o comandos usaste en el punto 33?
* **git reflog**
* **git checkout** ***id_commit***

Con `git reflog`accedemos al id del primer commit realizado y con git checkout nos desplazamos a ese estado descartando los cambios en el working copy.

En este punto, si queremos conservar los últimos cambios realizados en este archivo (en este caso el título) tendremos que crear una rama temporal que posteriormente mergearemos en master.
