---
title: Usando GIT
image: /assets/images/git.png
layout: post
---

# Sistema de control de versiones GIT

>Git es un sistema de control de versiones. Un sistema de control de versiones nos va a servir para trabajar en equipo de una manera mucho más simple y optima cuando estamos desarrollando software.

# Instalación
<br>
Para empezar a trabajar con <mark>git</mark> puedes darcargarlo [aquí](https://git-scm.com/). Con <mark>GIT</mark> puedes conectarte al servidor remoto de 2 formas:

+ Por conexión HTTP: Requiere de un usuario y contraseña para conectarte al repositorio.
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

## <strong>Configuracion global y local</strong>
El comando `git config --global` es para manejar las configuraciones a nivel global, es decir tendra efecto en todos los repositorios que se gestione dentro del equipo donde se está trabajando. 

Existe también `git config --local` para manejar las configuraciones para un reposiorio en específico.
<br><br>

## <strong>Cambiar de editor predeterminado</strong>
Por defecto <mark>GIT</mark> trabaja con un editor predeterminado que es <mark>VIM</mark> con el cual pocos estan acostumbrados a usar por su complejidad, sin embargo es importante manejar adecuadamente los mensajes de <mark>GIT</mark> a través del editor, ya sea por un <mark> merge </mark> o por conflictos entre las ramas.

Podemos cambiar el editor de forma sencilla:

+ Cambiar a nano `git config --global core.editor "nano"`
+ Cambiar a Visual Studio Code `git config --global core.editor "code --wait"`
+ Cambiar a Atom `git config --global core.editor "atom --wait"`