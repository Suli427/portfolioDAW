# Introducción
En este documento, se explica la instalación y configuración básica de SSH para realizar conexiones seguras entre equipos de forma remota.

# Actividades realizadas
## Instalación SSH
Iniciaremos instalando SSH utilizando el siguiente comando:
![UD4: Trabajo en remoto"/imagenes/cap1.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap1.png)

## Configuración SSH
Cuando se cambie la configuración de SSH, también se cambiará la configuración del servidor sshd. En Ubuntu, el archivo principal de configuración sshd lo podemos encontrar en *etc/ssh/sshd_config/*.

Antes de editar el archivo de configuración, comprobaremos que la instalación de SSH ha sido correcta ejecutando el primer comando de la siguiente imagen. Luego, realizaremos una copia de seguridad del archivo de configuración sshd (*sshd_config*) con el segundo comando de la imagen:  
![UD4: Trabajo en remoto"/imagenes/cap2.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap2.png)

A continuación, utilizaremos el editor nano para modificar el archivo de configuración:
![UD4: Trabajo en remoto"/imagenes/cap3.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap3.png)

En el archivo encontraremos información importante, como el puerto que utiliza SSH. En esta práctica, no realizaremos modificaciones en el archivo.

Después de salir de la edición del archivo, recargaremos el servidor sshd para aplicar los cambios con el siguiente comando:
![UD4: Trabajo en remoto"/imagenes/cap4.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap4.png)

## Cómo crear claves SSH
Las claves SSH se deben generar en el equipo desde el cual deseamos iniciar sesión. Si ejecutamos el comando de la siguiente imagen y presionamos Intro, las claves se crearán en *~/.ssh/id_rsa.pub* y *~/.ssh/id_rsa*:
![UD4: Trabajo en remoto"/imagenes/cap5.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap5.png)

## Cómo tranferir nuestra clave pública al servidor
En este momento, tenemos acceso con contraseña a un servidor. Al copiar nuestra clave pública, se abrirá una sesión SSH. Después de ingresar nuestra contraseña, nuestra clave pública se copiará en el archivo de claves autorizadas del servidor, permitiendo iniciar sesión sin contraseña en el futuro, ya que el servidor reconocerá la clave como una credencial autorizada.
![UD4: Trabajo en remoto"/imagenes/cap7.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap7.png)

Si no sabemos nuestra IP, podemos ejecutar el comando *ifconfig*. Este comando no se ejecutará si no tenemos instaladas las net-tools. Para ello, ejecutaremos lo siguiente:
![UD4: Trabajo en remoto"/imagenes/cap6.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap6.png)



# Resultado final
Para terminar, vamos a conectarnos al equipo de otro compañero.

Para ello, nuestro compañero tendrá que permitir la entrada por el puerto 22 con el siguiente comando:
![UD4: Trabajo en remoto"/imagenes/cap9.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap9.png)  

A continuación, ejecutaremos el siguiente comando con el nombre de usuario y la dirección IP del equipo al que deseamos conectarnos:
![UD4: Trabajo en remoto"/imagenes/cap10.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap10.png)

![UD4: Trabajo en remoto"/imagenes/cap11.png](https://raw.githubusercontent.com/Suli427/portfolioDAW/refs/heads/main/UD4%3A%20Trabajo%20en%20remoto/imagenes/cap11.png)
Como podemos ver, nos hemos conectado al equipo de nuestro compañero y hemos creado un directorio.

# Conclusión
En conclusión, con la instalación y configuración básica de SSH, hemos aprendido a conectarnos de forma segura a otro equipo. Esta práctica nos ha permitido configurar el archivo sshd, generar claves SSH, y transferir la clave pública al servidor, permitiendo conexiones sin contraseña.
