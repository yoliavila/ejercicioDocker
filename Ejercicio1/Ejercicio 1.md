### Ejercicio 1 - Servidor de base de datos

> Realizado por Pablo Merino.

- Arrancar un contenedor que se llame web y que ejecute una instancia de una imagen con Apache y php.

  ```bash
  $ docker run -d --name web -p 8080:80 php:apache
  ```

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.42_e19b63c6](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.42_e19b63c6.jpg)

  - Captura de pantalla y documento que desde el navegador muestre el fichero`index.html.`

  ```bash
  $ docker exec -it web bash
  $ cd var/www/html
  $ echo "<h1>Fichero index.html de Yoli y Pablo</h1>" > index.html
  ```

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.43_3a40322b](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.43_3a40322b.jpg)

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.42_2aa7decc](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.42_2aa7decc.jpg)

  - Captura de pantalla y documento que desde un navegador muestre la salida del script `mes.php`.

  ```bash
  $ echo "<?php date_default_timezone_set('Europe/Madrid');" '$mes_actual = date("F");' 'echo "Estamos en el mes de $mes_actual"; ?>' > /var/www/html/mes.php
  
  ```

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.42_ed5b0da0](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.42_ed5b0da0.jpg)

  - Captura de pantalla y documento donde se vea el tamaño del contenedor `web` después de crear los ficheros.

  ```bash
  $ docker ps -s
  ```

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.35_12ed5d7f](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.35_12ed5d7f.jpg)

- Arrancar un contenedor que se llame `bbdd` y que ejecute una instancia de la imagen mariadb para que sea accesible desde el puerto 3306.

  ```bash
  $ docker run -d --name bbdd -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=prueba -e MYSQL_USER=invitado -e MYSQL_PASSWORD=invitado mariadb
  ```

![Imagen de WhatsApp 2024-03-03 a las 20.44.42_3f03c0fe](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.42_3f03c0fe.jpg)

- Captura de pantalla y documento donde desde un cliente de base de datos, se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba (`show_databases`). 

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.34_741829e6](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.34_741829e6.jpg)

![Imagen de WhatsApp 2024-03-03 a las 20.44.42_603a26b7](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.42_603a26b7.jpg)

![Imagen de WhatsApp 2024-03-03 a las 20.44.35_7c939f66](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.35_7c939f66.jpg)

- Captura de pantalla y documento donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado.

  ![Imagen de WhatsApp 2024-03-03 a las 20.44.35_e85d5890](./Ejercicio%201.assets/Imagen%20de%20WhatsApp%202024-03-03%20a%20las%2020.44.35_e85d5890.jpg)

  

​	
