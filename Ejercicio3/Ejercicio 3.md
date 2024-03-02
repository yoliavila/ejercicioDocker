### Ejercicio 3 - Contenedores en red: Adminer y MariaDB

> Realizado por Pablo Merino.

- Crea una red bridge `redbd`.

  ```bash
  $ docker network create redbd
  ```

  ![image-20240302173359585](Ejercicio%203.assets/image-20240302173359585.png)

- Crea un contenedor con una imagen de `mariaDB` que estará en la red `redbd`. Este contenedor se ejecutará en segundo plano, y será accesible a través del puerto 3306. (Es necesario definir la contraseña del usuario `root` y un volumen de datos persistente).

  ```bash
  $ docker run -d --name contenedorMariadb --network redbd -p3306:3306 -eMYSQL_ROOT_PASSWORD=root -v mariadb_data:/var/lib/mysql mariadb
  ```

  ![image-20240302173803438](Ejercicio%203.assets/image-20240302173803438.png)

- Crea un contenedor `Adminer` que se pueda conectar al contenedor de la BD.

  ```bash
  $ docker run -d --name contenedorAdminer --network redbd -p 8008:8080 adminer
  ```

  ![image-20240302174053409](Ejercicio%203.assets/image-20240302174053409.png)

- Compruebar que el contenedor Adminer puede conectar con el contenedor mysql abriendo en un navegador web y accediendo a la URL: http://localhost:8008.

  Captura de pantalla y documento donde se vea el acceso a la BD  a través de la interfaz web de Adminer.

  ![image-20240302174235264](Ejercicio%203.assets/image-20240302174235264.png)

  ![image-20240302174339773](Ejercicio%203.assets/image-20240302174339773.png)

  

  Captura de pantalla y documento donde se vea la creacion de una BD con la interfaz web Adminer.

  ![image-20240302175820352](Ejercicio%203.assets/image-20240302175820352.png)

  ![image-20240302175757668](Ejercicio%203.assets/image-20240302175757668.png)

  

- Captura de pantalla y documento donde se vean los contenedores creados y en ejecución.

  ```bash
  $ docker ps
  ```

  ![image-20240302174512047](Ejercicio%203.assets/image-20240302174512047.png)

  

- Captura de pantalla y documento donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD.

  ```bash
  $ docker exec -it contenedorMariadb /bin/bash
  $ mysql -h localhost -u root -p
  $ SHOW DATABASES;
  ```

  ![image-20240302180031456](Ejercicio%203.assets/image-20240302180031456.png)

- Borra los contenedores la red y los volúmenes utilizados.

  ```bash
  $ docker stop contenedorMariadb contenedorAdminer
  $ docker rm contenedorMariadb contenedorAdminer
  $ docker network rm redbd
  ```

  ![image-20240302180437787](Ejercicio%203.assets/image-20240302180437787.png)

​	



