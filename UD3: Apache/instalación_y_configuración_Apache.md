# Introducción
En este documento, se explica cómo instalar y configurar Apache de forma básica para crear un sitio web funcional. Apache es una excelente opción para este propósito, ya que actúa como un servidor web, lo que significa que su función principal es entregar contenido web (como páginas HTML, imágenes y archivos) a los usuarios que lo soliciten a través de un navegador.

# Palabras clave
* Apache2
* Firewall
* VirtualHost
* ServerAdmin
* DocumentRoot
* ServerName
* IP

# Actividades realizadas
## Instalación de apache
Para empezar, actualizaremos el índice de paquetes locales para que se reflejen los últimos cambios realizados:
!["UD3: Apache"/imagenes/cap1.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap1.png)

A continuación, procedemos a instalar el paquete apache2 con el siguiente comando:
!["UD3: Apache"/imagenes/cap2.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap2.png)

## Ajustar el firewall
Antes de ir a probar Apache, se debe modificar los ajustes del firewall para permitir el acceso externo a los puertos web predeterminados.

Durante la instalación, Apache se integra con UFW y crea varios perfiles de aplicación que permiten activar o desactivar el acceso a Apache a través del firewall.

Para enumerar dichos perfiles en una lista, escribiremos lo siguiente:   
!["UD3: Apache"/imagenes/cap4.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap4.png)

Por recomendación, habilitaremos el perfil más restrictivo solamente, que, de igual forma, permitirá el tráfico por el puerto 80 que es el que nos interesa. Antes de realizar esto, activaremos el cortafuegos, seguidamente habilitaremos el perfil y finalmente veremos su estado:  
!["UD3: Apache"/imagenes/cap6.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap6.png)

## Comprobar el servidor web
Ahora verificaremos si se encuentra en ejecución el servicio escribiendo el siguiente comando:
!["UD3: Apache"/imagenes/cap7.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap7.png)

El resultado nos confirma que el servicio se ha iniciado correctamente. Para comprobarlo de una mejor forma, solicitaremos una página de Apache. Para confirmar que el software funciona correctamente, utilizaremos nuestra dirección IP. La IP la podemos obtener de varias formas desde la línea de comandos.

Si escribimos lo siguiente en la línea de comandos, obtendremos la dirección IP del hostname:
!["UD3: Apache"/imagenes/cap8.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap8.png)

Otra alternativa es usar la herramienta Icanhazip, la cual nos mostrará nuestra dirección IP pública tal como se ve desde otra ubicación en Internet:  
!["UD3: Apache"/imagenes/cap9.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap9.png)

Cuando tengamos la dirección ip de nuestro servidor, la introduciremos en la barra de direcciones de nuestro navegador:
!["UD3: Apache"/imagenes/cap10.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap10.png)

## Administrar el proceso de Apache
Ahora, nuestro servidor web está listo y en funcionamiento. En este apartado del documento, se mostrarán algunos comandos de administración básicos.

* Para detener, iniciar y reiniciar nuestro servidor web, utilizaremos los siguientes comandos:
!["UD3: Apache"/imagenes/cap11.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap11.png)

* Si solo hemos hecho cambios de configuración, Apache da la opción de recargarse sin cerrar conexiones. Para ello, utilizaremos el siguiente comando:  
!["UD3: Apache"/imagenes/cap12.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap12.png)

* Por defecto, Apache tiene una configuración que hace que se inicie automáticamente cuando el servidor lo hace. Si quisiéramos deshabilitar esto, utilizaremos el primer comando de la siguiente imagen y si después de ejecutarlo quisiéramos volver a habilitarlo utilizaríamos el segundo:
!["UD3: Apache"/imagenes/cap13.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap13.png)

## Creación de nuestro propio sitio web
Visto todo esto, vamos a crear nuestro propio sitio web. Por defecto, Apache viene con un sitio web básico habilitado. Podemos modificar su contenido en /var/www/html o ajustar la configuración editando el archivo de Virtual Host ubicado en /etc/apache2/sites-enabled/000-default.conf.

El primer paso para crear nuestro sitio web será crear una carpeta para él:
!["UD3: Apache"/imagenes/cap15.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap15.png)

Seguidamente crearemos el archivo html que va a tener nuestro sitio web. A este archivo lo llamaremos index.html y utilizaremos el comando nano para crearlo. Su contenido será el siguiente:
!["UD3: Apache"/imagenes/cap16.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap16.png)

## Configuración del archivo de configuración VirtualHost
Comenzaremos este paso dirigiéndonos al directorio de archivos de configuración y copiaremos el archivo VirtualHost predeterminado que viene con Apache:
!["UD3: Apache"/imagenes/cap17.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap17.png)

A continuación, editaremos el archivo de configuración utilizando el comando nano. En este archivo, deberíamos tener nuestro correo electrónico en ServerAdmin para que así los usuarios puedan contactar con nosotros en caso de que   Apache experimente algún error. También queremos el DocumentRoot para apuntar al directorio de nuestros archivos alojados en /var/www/gci. Por último, este archivo no viene con un ServerName, por lo que tendremos que añadirlo y definir el nombre del servidor.

El resultado será el siguiente:
!["UD3: Apache"/imagenes/cap18.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap18.png)

## Activar archivo VirtualHost
Una vez ya configurado nuestro sitio web, activaremos el archivo de configuración de hosts virtuales para habilitarlo. Para ello, ejecutaremos el comando que se muestra a continuación y deberíamos ver la siguiente salida:
!["UD3: Apache"/imagenes/cap19.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap19.png)

Para cargar el nuevo sitio web, reiniciaremos Apache ejecutando el siguiente comando:
!["UD3: Apache"/imagenes/cap20.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap20.png)

Finalmente, modificaremos el archivo /etc/hosts:
!["UD3: Apache"/imagenes/cap21.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap21.png)

Y realizaremos los siguientes cambios:  
!["UD3: Apache"/imagenes/cap22.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap22.png)

# Resultado final
El resultado final ha sido el siguiente:
!["UD3: Apache"/imagenes/cap23.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD3%3A%20Apache/imagenes/cap23.png)

Como podemos observar, muestra el contenido del documento html de nuestro sitio web.

# Conclusión
En conclusión, al seguir los pasos detallados en este documento, hemos logrado instalar y configurar Apache de manera efectiva, creando un sitio web funcional con una configuración básica. Hemos aprendido a gestionar el servidor web, incluyendo cómo iniciar, detener y reiniciar el servicio, así como a configurar el firewall para permitir el acceso adecuado. También hemos explorado la creación y modificación de nuestro propio sitio web, ajustando los archivos de configuración de VirtualHost para adaptarlo a nuestras necesidades.

Este proceso no solo proporciona una comprensión fundamental de cómo funciona Apache, sino que también sienta las bases para futuras configuraciones más avanzadas, como la optimización del rendimiento y la implementación de medidas de seguridad.
