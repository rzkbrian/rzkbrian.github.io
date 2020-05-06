---
title: Usando GIT
image: /assets/images/git.png
layout: post
---

# Sistema de control de versiones GIT

>Git es un sistema de control de versiones. Un sistema de control de versiones nos va a servir para trabajar en equipo de una manera mucho más simple y óptima cuando estamos desarrollando software.

# Instalación
<br>
Para empezar a trabajar con <mark>git</mark> puedes darcargarlo [aquí](https://git-scm.com/). Con <mark>GIT</mark> puedes conectarte al servidor remoto de 2 formas:

+ Por conexión HTTP: Requiere de un usuario y contraseña para conectarse al repositorio.
+ Por conexión SSH: Requiere obtener la llave pública del equipo de trabajo. Se requiere usar el comando `ssh-keygen`, puedes obtener mayor información [aquí](https://www.ssh.com/ssh/keygen/).
<br><br>

# Preparación el entorno
Git necesita los datos del usuario con el cual trabajará y por lo general hace uso de los datos del equipo donde estamos trabajando, pero esto puede cambiarse de la siguiente manera:<br><br>

## <strong>Cambiar nombre de usuario</strong>
Ejecutamos `git config --global user.name "Brian Rodriguez"` para añadir un nombre de usuario.

Luego `git config --global user.name` para visualizar el nombre de usuario.
<br><br>

## <strong>Cambiar email de usuario</strong>
Ejecutamos `git config --global user.email "rzknairb@gmail.com"` para añadir un nombre de usuario.

Luego `git config --global user.email` para visualizar el nombre de usuario.
<br><br>

## <strong>Configuración global y local</strong>
El comando `git config --global` es para manejar las configuraciones a nivel global, es decir tendrá efecto en todos los repositorios que se gestione dentro del equipo donde se está trabajando. 

Existe también `git config --local` para manejar las configuraciones para un repositorio en específico.
<br><br>

## <strong>Cambiar de editor predeterminado</strong>
Por defecto <mark>GIT</mark> trabaja con un editor predeterminado que es <mark>VIM</mark> con el cual pocos están acostumbrados a usar por su complejidad, sin embargo es importante manejar adecuadamente los mensajes de <mark>GIT</mark> a través del editor, ya sea por un <mark> merge </mark> o por conflictos entre las ramas.

Podemos cambiar el editor de forma sencilla:

+ Cambiar a nano `git config --global core.editor "nano"`
+ Cambiar a Visual Studio Code `git config --global core.editor "code --wait"`
+ Cambiar a Atom `git config --global core.editor "atom --wait"`
<br><br>

# Inicializar proyecto GIT (`git init`)
Éste método solo se usa cuando tenemos un proyecto local y queremos migrar o empezar a utilizar <mark> GIT</mark>. Para ello usaremos el comando `git init`, ésto generará la configuración inicial de git con lo cual ya podremos hacer uso de otros comandos como `git status`, `git commit` y `git push` entre los más básicos.
<br><br>

# Clonar Repositorio (`git clone`)
Con git existen 2 maneras de descargar un repositorio:

+ Por HTTP: `git clone https://github.com/rzkbrian/rzkbrian.github.io.git`.
+ Por SSH: `git clone git@github.com:rzkbrian/rzkbrian.github.io.git`.

Todo dependerá del modo en que puedas acceder al servidor.
<br><br>

# Agregar cambios (`git add`)
Para poder guardar los cambios del repositorio, primero se tiene que agregar los cambios al <mark>stage</mark>. <mark>Stage area</mark> es el área donde se almacenan los cambios agregados para luego empaquetarlo en un `commit`.

+ Agregar archivo modificado, agregado o eliminado: `git add src/main/java/repository/Version.java`.
+ Agregar todos los cambios: `git add .`

Se tiene que tener cuidado al momento de agregar cambios, hay ciertos archivos que no se deben subir al servidor dependiendo la tecnología que se use, para evitar que GIT rastree estos archivos más adelante usaremos <mark>.gitignore</mark>
<br><br>

# Guardar cambios (`git commit -m`)
Una vez que se agregan los cambios en el <mark>stage area</mark> el paso siguiente es guardarlos e identificarlo mediante un mensaje que represente los cambios realizados.

Usamos `git commit -m "mensaje descriptivo"`, de ésta manera guardaremos los cambios modificados en el proyecto.
<br><br>

# Enviar cambios al servidor (`git push`)
Existen varios modos de enviar cambios al repositorio remoto, sin embargo la sentencia tiene un cuerpo que se detalla a continuación:
- `git push` - Comando necesario para subir los commits al servidor.
- `origin` - Es parte de la sentencia que hace referencia al nombre del repositorio remoto. Se detallará mas adelante.
- `develop` - Se indica el nombre de la rama a la cual se enviarán los commits realizados.

Sentencia completa:
+ `git push origin develop` - Envía los cambios a la rama <mark> develop </mark> del repositorio remoto.
+ `git push --all` - Este comando envía o sube al servidor todas las ramas locales que existan.
<br><br>

# Actualizar o bajar cambios del servidor (`git pull`)
Al igual que `git push`, éste comando tambien tiene el mismo cuerpo con la diferencia que en lugar de subir cambios (push), actualizaremos el repositorio local con los cambios que existen en el servidor con el fin de estar actualizados siempre con la última versión del código.
+ `git pull origin develop` - De ésta manera actualizaremos la rama <mark>develop</mark> de nuestro repositorio local.
<br><br>

# Actualizar las ramas remotas (`git fetch`)
Este comando nos permite actualizar las ramas dependiendo el origen de los datos y tiene el siguiente cuerpo:
- `git fetch origin` - De ésta manera actualizaremos todas las copias locales de las ramas remotas del repositorio `origin`.
- `git fetch --all` - Actualiza todas las copias locales de las ramas remotas de todos los repositorios.
<br><br>

# Repositorios de origen (`git remote`)
Este comando nos brinda el nombre del repositorio de la fuente de datos.

+ `git remote` - Informa el nombre del asignado a la fuente de datos.
+ `git remote --v` - Informa sobre la url de conexion ala fuente de datos, puede ser una conexión HTTP o SSH.
+ `git remote add <nombre_de_origen> <url_fuente_datos>` - Podemos añadir una nueva fuente de datos. <mark> nombre_de_origen </mark> debe ser reemplazado por el nombre correspondiente, generalmente y por defecto es `origin`, <mark>url_fuente_datos</mark> siempre será la url del repositorio remoto. Al final deberá quedar de la siguiente forma:
    - `git remote add origin_two https://gitlab.com/rzkbrian.git`.
+ `git remote remove <origin> <url_source>` Elimina la fuente de datos del repositorio local.

# Crear ramas locales y remotas (`git branch`)
Con git podemos crear ramas o una versión del código que actualmente estamos trabajando para después integrarlo con los cambios del resto del equipo.

+ `git branch nueva_rama` - Crea un nueva rama a partir de la rma actual donde de está trabajando. Luego para ir a la rama creada tendremos que usar `git checkout nueva_rama`.
+ `git checkout -b nueva_rama` - Es un atajo, el cual crea una nueva rama y te lleva directamente a ella.

Para que la rama local se convierta en remota solo bastaría con hacer `git push origin nueva_rama` y automaticamente la nueva rama se creará en el repositorio remoto. Ésto esat sujeto a los permisos y niveles de seguridad del servidor remoto.

