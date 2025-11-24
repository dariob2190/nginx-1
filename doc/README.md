# Práctica 2.1: Instalación y configuración de servidor web Nginx

## Sumario:

1.  Instalación servidor web Nginx
2.  Creación de las carpetas del sitio web
3.  Configuración de servidor web NGINX
4.  Comprobaciones

## 1. Instalación servidor web Nginx

Vamos a empezar instalando el servidor en nuestra máquina Debian. Primero actualizamos los repositorios y después instalamos el paquete correspondiente:

```
sudo apt update
sudo apt install nginx
```

Hecho esto, vamos a comprobar que Nginx se ha instalado y que está funcionando correctamente con `systemctl status nginx`. Nos tendría que salir algo así:

![Captura de la comprobación del estado de nginx](./capturas/captura1.png)

## 2. Creación de las carpetas del sitio web

Igual que ocurre en Apache, todos los archivos que formarán parte de un sitio web se organizarán en carpetas dentro de `/var/www`. Vamos a crear la carpeta de nuestro dominio:

```
sudo mkdir -p /var/www/luisdario.test/html
```

Ahora vamos a entrar en esa carpeta y clonar el repositorio que usaremos de ejemplo.

```
cd /var/www/luisdario.test/html
git clone https://github.com/cloudacademy/static-website-example
```

Además, tenemos que hacer que el propietario de esta carpeta y todo lo que haya dentro sea del usuario `www-data`, que es el usuario del servicio web, y le daremos los permisos adecuados para no tener errores de acceso:

```
sudo chown -R www-data:www-data /var/www/luisdario.test/html
sudo chmod -R 755 /var/www/luisdario.test
```

Podemos comprobar con un `ls -l` que los permisos y el propietario se han aplicado correctamente:

![Captura de la comprobación de los permisos de nginx](./capturas/captura2.png)
