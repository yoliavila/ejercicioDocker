### Ejercicio 5 - Imagen con Dockerfile - Aplicación web

> Realizado por Pablo Merino y Yolanda Frexes.

Arranca un contenedor que ejecute una instancia de la imagen `php:7.4-apache` , que se
llame `web` y que sea accesible desde un navegador en el `puerto 8000`.

```bash
$ docker run -d -p 8000:80 --name web php:7.4-apache
```

Coloca en el directorio raíz del servicio web `( /var/www/html )` un sitio web donde figure el
nombre de los componentes del grupo - el sitio deberá tener al menos un archivo
`index.html` y un `archivo .css`

![Imagen de WhatsApp 2024-03-03 a las 19.27.55_fd049c56](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.27.55_fd049c56.jpg)

![Imagen de WhatsApp 2024-03-03 a las 19.28.10_08677cf9](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.28.10_08677cf9.jpg)

```bash
$ echo '<! DOCTYPE html><html lang=en><head><meta charset=UTF-8><meta name=viewport content=width=device-width, initial-scale=1.0><title>YoliYPablo</title><link rel=stylesheet href=styles.css></head><body><h1>GRupo formado por Yolanda Frexes y Pablo Merino</h1></body></html>' > index.html

$ echo "body { background-color: #fofofo; font-family: Arial, sans-serif; } h1 { color: blue; }"" > styles.css
```

![image-20240303131021585](./Ejercicio%205.assets/image-20240303131021585.png)

Coloca en ese mismo directorio raíz un archivo llamado `mes.php` que muestre el nombre del
mes actual. Ver la salida del script en el navegador.

```bash
$ echo "<? php echo 'Estamos en el mes de ' . date('F'); ?>" > mes.php
```

![Imagen de WhatsApp 2024-03-03 a las 19.30.15_53bcae89](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.30.15_53bcae89.jpg)

![Imagen de WhatsApp 2024-03-03 a las 19.33.35_1a74d509](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.33.35_1a74d509.jpg)

Borrar el contenedor:

```bash
$ docker stop web

$ docker rm web
```

![Imagen de WhatsApp 2024-03-03 a las 19.35.32_14304707](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.35.32_14304707.jpg)

Automatizar estas operaciones creando un fichero `Dockerfile`
Subir la imagen a la cuenta de Docker Hub
Deberás entregar los siguientes capturas de pantalla y los comandos empleados para resolver cada apartado:

1. Creación inicial del contenedor - documenta los pasos hasta el borrado del mismo

     

2. Bloque de código con el Dockerfile

   ```bash
   FROM php:7.4-apache
   RUN mkdir /var/www/html/ejerciciodocker
   
   COPY index.html /var/www/html/ejerciciodocker
   COPY index.css /var/www/html/ejerciciodocker
   COPY mes.php /var/www/html/ejerciciodocker
   
   EXPOSE 8000
   ```

   ![Imagen de WhatsApp 2024-03-03 a las 19.39.13_7aaf34e1](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.39.13_7aaf34e1.jpg)

3. Captura de pantalla y documento donde se vea el comando que crea la nueva imagen.

   ![Imagen de WhatsApp 2024-03-03 a las 19.51.10_be2a510d](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.51.10_be2a510d.jpg)

   ![Imagen de WhatsApp 2024-03-03 a las 19.56.17_a51e313c](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.56.17_a51e313c.jpg)

4. Captura de pantalla y documento donde se vea la imagen subida a tu cuenta de Docker Hub.

   ![Imagen de WhatsApp 2024-03-03 a las 19.59.40_258a11f5](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2019.59.40_258a11f5.jpg)

   ![Imagen de WhatsApp 2024-03-03 a las 20.03.43_fe54ce10](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.03.43_fe54ce10.jpg)

   ![Imagen de WhatsApp 2024-03-03 a las 20.04.07_d269f2f1](./Ejercicio%205.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.04.07_d269f2f1.jpg)

5. Captura de pantalla y documento donde se vea la bajada de la imagen - por parte de otra
     persona del grupo - y la creación de un contenedor.

  ![image-20240303202503204](./Ejercicio%205.assets/image-20240303202503204.png)

6. Captura de pantalla y documento donde se ve el acceso al navegador con el sitio servido

   ![image-20240303203102354](./Ejercicio%205.assets/image-20240303203102354.png)

Adjunto captura del comando que debería utilizarse para crear el contenedor pero debido a que no tengo espacio en la máquina virtual no he podido hacer la comprobación.