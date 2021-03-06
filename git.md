Git
===

Requerimientos
--------------
Instalar git

```bash
pacman -S git
```



Instalar openssh para generar la clave ssh

```bash
pacman -S openssh
```



Instalar meld para resolver "merge"

```bash
pacman -S meld
```

Configuración global
--------------------

### Requerido

Define tu nombre

```bash
git config --global user.name "nombre"
```



Define tu correo electrónico.

```bash
git config --global user.email "correo"
```



Define gitignore global

```bash
git config --global core.excludesfile ~/.gitignore-global
```



Define la herramienta para el "merging"

```bash
git config --global merge.tool meld
```



### Opcional

Deshabilitar copias de respaldo(__.orig__)

```bash
git config --global mergetool.keepBackup false
```




Define el gitignore global
--------------------------

Crea el archivo

```bash
touch .gitignore-global
```

Edite el archivo

```bash
echo "*.log" > .gitignore-global
```



* ___Nota___: [Gitignore.io](http://www.gitignore.io) puede ayudarte para selecionar los patrones según tus aplicaciones.


Generando clave ssh
-------------------

Ejecutar el comando:

```bash
ssh-keygen -t rsa -b 4096 -C "tu correo electrónico"
```

   > -t: tipo
   >
   > -b: número de bits
   >
   > -C: agrega un comentario

___Nota___: 

* Para finalizar establece una contraseña y confirma.

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

      ```bash
      ssh -T git@github.com
      ```

  * __Bitbucket__

      ```bash
ssh -T git@bitbucket.org
      ```

      * ___Opcional___: si deseas ver cada detalle que se realiza en la conexión puedes agregar "v".
      
          > ssh -vT `git@github.com`

2. Una vez comprobado la conexión; se consulta si desea agregar la dirección IP del servicio, confirme y listo.

  * Nota: Las direcciones conocidas que usted da de alta se almacenan en el archivo `~/.ssh/known_hosts`

3. Finalmente el resultado puede ser(depende del idioma de tu ordenador):

  * __Github:__    Hi "tu cuenta"! You've successfully authenticated, but github does not provide shell access.
  * __Bitbucket:__ logged in as "tu cuenta" You can use git or hg to connect to Bitbucket. Shell access is disabled.

Extras
------

1. Puedes instalar un entorno gráfico para git:

   ```bash
   pacman -S gitg
   ```

   

2. Si deseas imprimir, busca en el proyecto la carpeta [recursos](./recursos/git)
