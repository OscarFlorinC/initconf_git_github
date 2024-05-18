# Configuración de Git

## 1. Configuración inicial git:
### Configuración de usuario y correo, estos datos son globales

#### Comandos:
	git config --global user.name  "JuanLópez"
	git config --global user.email  "jb@mail.com"


## 2. Iniciar el Sistema de control de Versiones (SCDV):

#### Comando:
	git init

###### Salida CLI
<img src="../imagenes/1.-Salida_init.png" width="500" height="200">

## 3. Cambio de nombre de la rama "master" a "main"
### Por buena practica se recomienda cambiar el nombre de la rama

#### Comando:
	git branch -m main

###### Salida CLI
<img src="../imagenes/2.-Cambio_nombre(branch).png" width="400" height="50">


|  | Descripción |
|-----:|---------------|
| [![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](../ejemPython/ejemgit.md) | ***Ejemplo*** |



## 4. Creación de etiquetas para las app's:
### Se sugiere crear etiquetas con cada version de la app, solo se aplica cuando ya se realizó un commit (archivo, aplicación, etc.).

#### Comandos:
	git tag v0.1
	git tag
	git checkout v0.1


## 5. Creación de ramas:
### Las ramas nos permiten desarrollar características, corregir errores, o experimentar con seguridad las ideas nuevas en un área contenida de nuestro repositorio.

#### Comandos:
	git branch developers
	git switch developers

## 6. Git Merge
### Combinar cambios entre las distintas ramas, por ejemplo combinar los cambios de la rama developer a main

#### Comando:
	git merge main


## 7. Eliminar ramas:
### Se elimina una rama, cuando la nueva funcionalidad, error o el desarrollo de una nueva característica ya esta en producción.

#### Comando:
	git branch -d developers


# Configuración de GitHub
## GitHub son repositorios en la nube, un repositorio en la nube nos ayuda, por si un dia nuestro servidor o maquina local falla y la tenemos que reemplazar estos dispositivos, github nos ayuda a recuperar nuestros proyectos.
## También nos ayuda a trabajar con desarrolladores que tienen cuenta en github o con nuestros compañeros de trabajo, independientemente de su ubicación.


## 1. Autenticación SSH:
### SSH (o Secure SHell) es el nombre de un protocolo y del programa que lo implementa cuya principal función es el acceso remoto a un servidor por medio de un canal seguro en el que toda la información está cifrada. Además de la conexión a otros dispositivos, SSH permite copiar datos de forma segura (tanto archivos sueltos como simular sesiones FTP cifradas), gestionar claves RSA para no escribir contraseñas al conectar a los dispositivos y pasar los datos de cualquier otra aplicación por un canal seguro tunelizado mediante SSH y también puede redirigir el tráfico del (Sistema de Ventanas X) para poder ejecutar programas gráficos remotamente.

#### Comandos:
	ls -la ~/.ssh								> Nos muestra las claves SSH que se han creado anteriormente

###### Salida CLI
<img src="../imagenes/3.-Com_SSH.png" width="400" height="100">

## b. Generando key pair:
#### Comando:
	ssh-keygen -t ed25519 -C "jb@mail.com"		> Este comando genera el keypair
												> asignar nombre al keypair (Se sugieren los siguientes id_rsa    o      id_ecdsa     o      id_ed25519)
												> passphrase (si lo deseas lo puedes habilitar)

###### Salida CLI
<img src="../imagenes/4.-Gen_Keypair.png" width="500" height="150">


## 2. Comprobar el SSH:
#### Comandos:
	eval "$(ssh-agent -s)"			> Muestra un ID

###### Salida CLI
<img src="../imagenes/5.-Com_SSH_agent.png" width="300" height="70">


## 3. Creación del fichero de configuración:
	touch ~/.ssh/config			> dentro del fichero copiar el siguiente scrip:
									Host github.com
        								AddKeysToAgent yes
        								UseKeychain yes
        								IdentityFile ~/.ssh/"id_ed25519"		> Cambiar el "id_ed25519" por el asignado en el paso 1

###### Salida CLI
<img src="../imagenes/6.-Conf_file.png" width="500" height="150">


## 4. Añadir la clave al sistema de gestión:
#### Comando:
	ssh-add --apple-use-keychain ~/.ssh/"id_ed25519"			> Cambiar el "id_ed25519" por el asignado en el paso 1


## 5. Configuración en GitHub:
    - entrar a settings

###### Imagen
<img src="../imagenes/7.-Conf_Github.png" width="250" height="400">

    - entrar a SSH and GPG keys (hay dos formas de gestionar claves)
###### Imagen
<img src="../imagenes/7a.-Conf_Github.png" width="250" height="300">

    - SSH Keys
        - Crear nueva clave ssh, de tipo authentication key
###### Imagen
<img src="../imagenes/7b.-Conf_Github.png" width="550" height="100">


        - Dar nombre
        - ir a nuestro file de keypair (rsa, id_ecdsa, id_ed25519), abrir y copiar el contenido del archivo .pub
        - Pegar la key.pub en el segundo recuadro
            - Key
                ssh-ed25519 LASJKDFHKJH27YEBKDSF783287YKAJDFH7TDSAFKJBJL jb@mail.com
        - después dar click al botón
            - Add ssh key
###### Imagen
<img src="../imagenes/7c.-Conf_Github.png" width="500" height="400">


## 6. Comparar la configuración:
    - ssh -T git@github.com
    - Repetir la instrucción  ssh -T git@github.com
        - Saldrá un mensaje de que sea autenticado correctamente, pero tienes acceso por shell. ("Es normal este mensaje")
            - Hi User! You've successfully authenticated, but GitHub does not provide shell access.

###### Imagen
<img src="../imagenes/8.-Conf_Github.png" width="550" height="60">

#
# Puedes seguir y apoyar mi trabajo haciendo click en "☆ Star" y en el botón de Follow.
# ¡Muchas gracias, bienvenido!!!

# Contacto y apoyo:

<br>[![LinkedIn](https://img.shields.io/badge/Oscar_Florin-0077B5?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=101010)](https://www.linkedin.com/in/oscarflorincontreras)
[![X](https://img.shields.io/badge/DevozzCloud-%23000000.svg?style=for-the-badge&logo=X&logoColor=white)](https://twitter.com/DevozzCloud)</br>
[![Just_Eat](https://img.shields.io/badge/🌮_Donaciones_para_tacos-7A1FA2?style=for-the-badge&logo=)](https://paypal.me/OscarFlorin?country.x=MX&locale.x=es_XC)
[![Eats](https://img.shields.io/badge/🐈_Donaciones_para_gatos-black?style=for-the-badge&logo=)](https://paypal.me/OscarFlorin?country.x=MX&locale.x=es_XC)