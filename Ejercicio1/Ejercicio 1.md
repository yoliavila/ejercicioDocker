### Ejercicio 1 - Servidor de base de datos

> Realizado por Pablo Merino.

- Arrancar un contenedor que se llame web y que ejecute una instancia de una imagen con Apache y php.

  ```bash
  $ docker run -d --name web -p 8080:80 php:apache
  ```

  ![image-20240301094622891](/home/ubuntu/.config/Typora/typora-user-images/image-20240301094622891.png)

  - Captura de pantalla y documento que desde el navegador muestre el fichero`index.html.`

  ```bash
  $ docker exec -it web bash
  $ cd var/www/html
  $ echo "<h1>Fichero index.html de Yoli y Pablo</h1>" > index.html
  ```

  ![image-20240301094959194](/home/ubuntu/.config/Typora/typora-user-images/image-20240301094959194.png)

  ![image-20240301095218188](/home/ubuntu/.config/Typora/typora-user-images/image-20240301095218188.png)

  - Captura de pantalla y documento que desde un navegador muestre la salida del script `mes.php`.

  ```bash
  $ echo "<?php date_default_timezone_set('Europe/Madrid');" '$mes_actual = date("F");' 'echo "Estamos en el mes de $mes_actual"; ?>' > /var/www/html/mes.php
  
  ```

  ![image-20240301103605252](/home/ubuntu/.config/Typora/typora-user-images/image-20240301103605252.png)

  - Captura de pantalla y documento donde se vea el tamaño del contenedor `web` después de crear los ficheros.

  ```bash
  $ docker ps -s
  ```

  ![image-20240301103843390](/home/ubuntu/.config/Typora/typora-user-images/image-20240301103843390.png)

- Arrancar un contenedor que se llame `bbdd` y que ejecute una instancia de la imagen mariadb para que sea accesible desde el puerto 3306.

  ```bash
  $ docker run -d --name bbdd -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=prueba -e MYSQL_USER=invitado -e MYSQL_PASSWORD=invitado mariadb
  ```

![image-20240301141900643](/home/ubuntu/.config/Typora/typora-user-images/image-20240301141900643.png)

- Captura de pantalla y documento donde desde un cliente de base de datos, se pueda observar que hemos podido conectarnos al servidor de base de datos con el usuario creado y que se ha creado la base de datos prueba (`show_databases`). 

  ![Captura desde 2024-03-02 12-42-48](/home/ubuntu/Imágenes/Capturas de pantalla/Captura desde 2024-03-02 12-42-48.png)

​	![image-20240302124357311](/home/ubuntu/.config/Typora/typora-user-images/image-20240302124357311.png)

![image-20240302125540730](/home/ubuntu/.config/Typora/typora-user-images/image-20240302125540730.png)

- Captura de pantalla y documento donde se comprueba que no se puede borrar la imagen `mariadb` mientras el contenedor `bbdd` está creado.

  ![image-20240302125739743](/home/ubuntu/.config/Typora/typora-user-images/image-20240302125739743.png)

  

​	
