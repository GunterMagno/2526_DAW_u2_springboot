# Despligue Aplicación de Docker

Para poder hacer el despliegue continuo de la aplicación en SpringBoot con Docker he creado un workflow de Github Actions llamado `ci.yaml` el cual realiza los siguientes pasos:

- Hace un checkout del repositorio
- Login en DockerHub
- Genera la imagen de la aplicación
- Sube la imagen a DockerHub


## Login en DockerHub

Para hacer login en DockerHub e usado este paso:

[Codigo del paso](https://github.com/GunterMagno/2526_DAW_u2_springboot/blob/59d857cd2841f5fd0a1ea13379ea1a22fac457e4/.github/workflows/ci.yaml#L19-L23)

El cual utiliza la acción `docker/login-action@f4ef78c080cd8ba55a85445d5b36e214a81df20a` para poder hacer el loggin en DockerHub, este paso utiliza el usuario y contraseña a tráves de un secreto configurado en el repositorio de GitHub para poder utilizar tanto usuario como contraseña sin tener que exponerlas en ningun archivo ni comando, como se ve en la imagen de abajo.

![Captura de Login sin exponer credenciales](/evidencias/Captura1.png)

Aqui dejo una imagen de donde se configura las credenciales secretas del repositorio
![Captura de la configuracion en GitHub](/evidencias/Captura3.png)

## Generación de la imagen

Para generar la imagen utilizo un actions de docker que crea la imagen y despues la sube a DockerHub
Como parametro le paso que archivo tiene que utilizar, que pushee la imagen y los tags de como se llame la imagen y el tag de versión.

[Enlace a codigo del paso](https://github.com/GunterMagno/2526_DAW_u2_springboot/blob/59d857cd2841f5fd0a1ea13379ea1a22fac457e4/.github/workflows/ci.yaml#L25-L31)

Aqui abajo dejo una imagen de como se ven los logs del workflow al hacer el build de la imagen.
![Captura de los logs](/evidencias/Captura2.png)

[Enlace a la Imagen en DockerHub](https://hub.docker.com/repository/docker/gunterelmagno/springboot_app/general)

## Subir imagen a DockerHub

Este paso utiliza el mismo actions que el paso anterior, dejo una imagen de los logs de como se hace el push de la imagen en el workflow.

![Captura de los logs en el workflow](/evidencias/Captura4.png)

# Otros Cambios

Tambien para la practica e cambiado el header de la página para que se vea reflejado mi nombre cuando entres en la pagina, lo e cambiado en el html como se ve en el codigo de abajo.

[Enlace al codigo html](https://github.com/GunterMagno/2526_DAW_u2_springboot/blob/59d857cd2841f5fd0a1ea13379ea1a22fac457e4/src/main/resources/templates/index.html#L12)