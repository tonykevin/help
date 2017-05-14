GIT
===

Requerimientos
--------------
1. Instalar git

    > pacman -S git

2. Instalar openssh para generar la clave ssh

    > pacman -S openssh

3. Instalar meld para resolver "merge"

    > pacman -S meld

Configuración global
--------------------

1. Define tu nombre

    > git config --global user.name "nombre"

2. Define tu correo electrónico.

    > git config --global user.email "correo"

3. Define gitignore global

    > git config --global core.excludesfile ~/.gitignore-global

4. Define la herramienta para el "merging"

    > git config --global merge.tool meld

Define el gitignore global
--------------------------

1. Crea el archivo

    > touch .gitignore-global

2. Edite el archivo

    > echo "*.log" > .gitignore-global

    * ___Nota___: [Gitignore.io](http://www.gitignore.io) puede ayudarte para selecionar los patrones según tus aplicaciones.


Generando clave ssh
-------------------

Ejecutar el comando, luego pulsa "enter" para confirmar donde se guarda la llave.

   > ssh-keygen

* ___Nota___: Para finalizar establece una contraseña y confirma.

Conectar vía ssh con repositorios remotos
-----------------------------------------

1. Previamente tienes que tener una cuenta en [github](https://github.com), [bitbucket](https://bitbucket.org) u otro con soporte para git

2. Agregar la llave pública ssh a tu servicio en la nube para sincronizar tu equipo:

  * Inicialmente se generó 2 llaves con ssh-keygen:

    | Llave   | Descripción                                                           |
    |---------|:----------------------------------------------------------------------|
    | rsa     | Llave de seguridad __privada__ nunca se debe compartir.               |
    | rsa.pub | Llave de seguridad __pública__ para agregar a los servicios externos. |

  * Estos archivos se encuentran ocultos en tu carpeta personal, para visualizar control+h y busca la carpeta `~/.ssh/`

  * Abre con tu editor favorito el archivo `rsa.pub`, copia y agrega estos carácteres a los servicios que desees.

  * Sigue los links de acuerdo al servicio externo que eligas

    *___Recuerda:___ son instrucciones referenciales, debido a que las plataformas web de los servicios está sujeto a cambios.

    __Github:__

    * Edit profile
    * SSH and GPG keys
    * New SSH key
    * En los formularios:
      * título: Ingresa un título referencial para la llave(sugerencia: usa el nombre de tu ordenador)
      * key   : Agrega el contenido de la llave `rsa.pub`
    * Add SSH key

    __Bitbucket:__

    * Click en tu perfil
    * Bitbucket settings
    * SSH keys
    * Add key
    * En los formularios:
      * label: Ingresa un título referencial para la llave(sugerencia: usa el nombre de tu ordenador)
      * key: Agrega el contenido de la llave `rsa.pub`
    * Add key

Verficar y testear la configuracion de git con los servicios en la nube
-----------------------------------------------------------------------

1. Comprobar la conexión con los servicios externos:

  * __Github__

      > ssh -T git@github.com

  * __Bitbucket__

      > ssh -T git@bitbucket.org

      * ___Opcional___: si deseas ver cada detalle que se realiza en la conexión puedes agregar "v".

          > ssh -vT git@github.com

2. Una vez comprobado la conexión; se consulta si desea agregar la dirección IP del servicio, confirme y listo.

  * Nota: Las direcciones conocidas que usted da de alta se almacenan en el archivo `~/.ssh/known_hosts`

3. Finalmente el resultado puede ser(depende del idioma de tu ordenador):

  * __Github:__    Hi "tu cuenta"! You've successfully authenticated, but github does not provide shell access.
  * __Bitbucket:__ logged in as "tu cuenta" You can use git or hg to connect to Bitbucket. Shell access is disabled.

Extras
------

1. Puedes instalar un entorno gráfico para git:

  > pacman -S gitg

2. Si deseas imprimir, busca en el proyecto la carpeta [textConfig](./recursos/git)
