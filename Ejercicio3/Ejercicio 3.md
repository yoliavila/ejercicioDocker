### Ejercicio 3 - Contenedores en red: Adminer y MariaDB

> Realizado por Pablo Merino.

- Crea una red bridge redbd.
- Crea un contenedor con una imagen de mariaDB que estará en la red redbd. Este contenedor se ejecutará en segundo plano, y será accesible a través del puerto 3306. (Es necesario definir la contraseña del usuario root y un volumen de datos persistente).
- Crea un contenedor Adminer que se pueda conectar al contenedoor de la BD.
- Compruebar que el contenedor Adminer puede conectar con el contenedor mysql abriendo en un navegador web y accediendo a la URL: http://localhost:8008.



- Captura de pantalla y documento donde se vean los contenedores creados y en ejecución.
- Captura de pantalla y documento donde se vea el acceso a la BD  a través de la interfaz web de Adminer.
- Captura de pantalla y documento donde se vea la creacion de una BD con la interfaz web Adminer.
- Captura de pantalla y documento donde se entre a la consola del servidor web en modo texto y se compruebe que se ha creado la BD.
- Borra los contenedores la red y los volúmenes utilizados.

