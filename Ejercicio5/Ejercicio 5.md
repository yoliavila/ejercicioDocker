### Ejercicio 5 - Imagen con Dockerfile - Aplicación web

> Realizado por Pablo Merino.

Arranca un contenedor que ejecute una instancia de la imagen `php:7.4-apache` , que se
llame `web` y que sea accesible desde un navegador en el `puerto 8000`.

```bash
$ docker run -d -p 8000:80 --name web php:7.4-apache
```

Coloca en el directorio raíz del servicio web `( /var/www/html )` un sitio web donde figure el
nombre de los componentes del grupo - el sitio deberá tener al menos un archivo
`index.html` y un `archivo .css`

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

![image-20240303130243269](./Ejercicio%205.assets/image-20240303130243269.png)

Borrar el contenedor

```bash
$ docker stop web

$ docker rm web
```

![image-20240303131317895](./Ejercicio%205.assets/image-20240303131317895.png)

Automatizar estas operaciones creando un fichero `Dockerfile`
Subir la imagen a la cuenta de Docker Hub
Deberás entregar los siguientes capturas de pantalla y los comandos empleados para resolver cada apartado:

1. Creación inicial del contenedor - documenta los pasos hasta el borrado del mismo
2. Bloque de código con el Dockerfile
3. Captura de pantalla y documento donde se vea el comando que crea la nueva imagen.
4. Captura de pantalla y documento donde se vea la imagen subida a tu cuenta de Docker Hub.
5. Captura de pantalla y documento donde se vea la bajada de la imagen - por parte de otra
persona del grupo - y la creación de un contenedor.
6. Captura de pantalla y documento donde se ve el acceso al navegador con el sitio servido