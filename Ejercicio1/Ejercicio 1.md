### Ejercicio 1 - Servidor de base de datos

> Realizado por Pablo Merino.

- Arrancar un contenedor que se llame `bbdd` y que ejecute una instancia de la imagen mariadb para que sea accesible desde el puerto 3306.

- Antes de arrancarlo visitar la página del contenedor en **Docker Hub** y establecer las variables de entorno necesarias para que:
  - La contraseña de root sea `root`.
  - Crear una base de datos automáticamente al arrancar que se llame `prueba`.
  - Crear el usuario `invitado` con la contraseña `invitado`.

El comando que he usado ha sido: 

```bash
docker run -d --name bbdd -p3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=prueba -e MYSQL_USER=invitado -e MYSQL_PASSWORD=invitado mariadb
```

<img src="/home/ubuntu/.config/Typora/typora-user-images/image-20240226192531432.png" alt="image-20240226192531432"  />

<img src="/home/ubuntu/.config/Typora/typora-user-images/image-20240226192550985.png" alt="image-20240226192550985"  />

- Captura del fichero `index.html.`

<img src="/home/ubuntu/.config/Typora/typora-user-images/image-20240226194847255.png" alt="image-20240226194847255" style="zoom:80%;" />



