# 2048
A small clone of [1024](https://play.google.com/store/apps/details?id=com.veewo.a1024), based on [Saming's 2048](http://saming.fr/p/2048/) (also a clone).

Made just for fun. [Play it here!](http://gabrielecirulli.github.io/2048/)

The official app can also be found on the [Play Store](https://play.google.com/store/apps/details?id=com.gabrielecirulli.app2048) and [App Store!](https://itunes.apple.com/us/app/2048-by-gabriele-cirulli/id868076805)

### Contributions

[Anna Harren](https://github.com/iirelu/) and [sigod](https://github.com/sigod) are maintainers for this repository.

Other notable contributors:

 - [TimPetricola](https://github.com/TimPetricola) added best score storage
 - [chrisprice](https://github.com/chrisprice) added custom code for swipe handling on mobile
 - [marcingajda](https://github.com/marcingajda) made swipes work on Windows Phone
 - [mgarciaisaia](https://github.com/mgarciaisaia) added support for Android 2.3

Many thanks to [rayhaanj](https://github.com/rayhaanj), [Mechazawa](https://github.com/Mechazawa), [grant](https://github.com/grant), [remram44](https://github.com/remram44) and [ghoullier](https://github.com/ghoullier) for the many other good contributions.

### Screenshot

<p align="center">
  <img src="https://cloud.githubusercontent.com/assets/1175750/8614312/280e5dc2-26f1-11e5-9f1f-5891c3ca8b26.png" alt="Screenshot"/>
</p>

That screenshot is fake, by the way. I never reached 2048 :smile:

## Contributing
Changes and improvements are more than welcome! Feel free to fork and open a pull request. Please make your changes in a specific branch and request to pull into `master`! If you can, please make sure the game fully works before sending the PR, as that will help speed up the process.

You can find the same information in the [contributing guide.](https://github.com/gabrielecirulli/2048/blob/master/CONTRIBUTING.md)

## License
2048 is licensed under the [MIT license.](https://github.com/gabrielecirulli/2048/blob/master/LICENSE.txt)

## Donations
I made this in my spare time, and it's hosted on GitHub (which means I don't have any hosting costs), but if you enjoyed the game and feel like buying me coffee, you can donate at my BTC address: `1Ec6onfsQmoP9kkL3zkpB6c5sA4PVcXU2i`. Thank you very much!


# Ampliacion Rafael Pablo Garcia Sanchez
# # Despliegue de Juego 2048 con Docker y AWS

Este proyecto consiste en la "dockerización" de una aplicación web estática (el juego 2048) y su posterior despliegue en una instancia EC2 de Amazon Web Services (AWS) utilizando Docker Compose.

## 🚀 Pasos realizados

### 1. Creación del Dockerfile
Se ha creado un archivo `Dockerfile` basado en la imagen de `nginx` para servir el contenido estático. El proceso incluye:
* Instalación de `git`.
* Clonación del repositorio del juego.
* Copia de los archivos al directorio por defecto de Nginx (`/usr/share/nginx/html`).
![alt text](<2048-doc/1-creacion dockerfile.png>)

### 2. Construcción y Publicación
La imagen fue construida localmente y subida a **Docker Hub**:
1. `docker build -t nginx-2048 .`
2. `docker tag nginx-2048 tu_usuario/nginx-2048:latest`
3. `docker push tu_usuario/nginx-2048:latest`
![alt text](<2048-doc/2-levantando dockerfile.png>)
![alt text](<2048-doc/3-subir imagen a docker hub.png>)
![alt text](<2048-doc/4-imagen subida .png>)

### 3. Infraestructura en AWS
Se ha desplegado una instancia **EC2 (Ubuntu)** en AWS con la siguiente configuración de red (Security Group):
* **Puerto 22 (SSH):** Para administración remota.
* **Puerto 80 (HTTP):** Para permitir el acceso web público.

### 4. Despliegue con Docker Compose
Una vez dentro de la instancia de AWS, se utilizó un archivo `docker-compose.yml` para gestionar el contenedor:

![alt text](<2048-doc/5-creacion compose.png>)

### 5. Funcionamiento del juego 2048
![alt text](2048-doc/6-funcionando.png)
