# proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano
proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano created by GitHub Classroom

# SPRINT 1: HARDENING DE UBUNTU
0. Instalar ubuntu server 20.04 i instalar la grafica (gnome)
1. Asegura las configuraciones globales.

        1.1. Configuración del arranque GRUB.

        1.2. Establecer una contraseña de arranque.

        1.3. Establecer permisos fichero de configuración de arranque

        1.4. Obligar al uso de contraseña en el modo “single user”

2. Configuración de usuarios y grupos. Crea un usuario administrador con tu nombre, y añade este al grupo sudoers. Además, aplica  una política de contraseñas adecuada. 

        2.1. Complejidad

        2.2. Reutilización de contraseñas.

        2.3. Almacenamiento de contraseñas. Comprueba como un hash puede ser roto si el cifrado no es el adecuado. Sigue este tutorial.

        2.4. Ahora ya has evidenciado la importancia de realizar almacenamiento seguro de contraseñas como por ejemplo sha512. Una vez establecido vuelve a proceder el ataque.

        2.5. Configuración del entorno (Caducidad y cambio de contraseña, Timeout de inactividad, Bloqueo de cuenta tras varios intentos, etc)
  
3. Actualizacion de software

# SPRINT 2: HARDENING WINDOWS
0. Instalar S.O Windows 10
1. Crear otro usuario administrador y otro de empleador.
2. Desintalar programas que no estemos usando
3. Comprobar si esta habilitado el windows defender
4. Comprobar si esta habilitado la protección contra ransomware

        4.1.Acceso controlado a carpetas y comprobar la protección de la carpeta de Documento del perfil del usuario.
        
        4.2. Recuperación de datos por ransomware
        
5. Comprueba que si hubiera un intento de intrusión en uno de los portátiles si podrían resetear la contraseña del administrador y acceder a la cuenta.
6. Aplicar las medidas:

        6.1. Politica de contraseñas (caducidad, longitud,simbolos...)
        
        6.2. Cifrado de disco
     
        6.3. Comentar como evitar el arranque de herramientas live

# SPRINT 3 : COPIAS DE SEGURIDAD
Antes de nada, hay que instalar el duplicati en Ubuntu Server

0. Copia 1 llamada “copia documentos”, tendrá las siguientes características:

        0.1. copia cifrada con origen en la carpeta Documentos del servidor y destino tu cuenta de Google Drive. 
  
        0.2.Para esta carpeta solo podemos aceptar la pérdida de datos de máximo 1 hora de tiempo, y se genera información en esta carpeta de lunes a viernes. 
        
        0.3.Ten en cuenta que además de configurar la copia, es imprescindible comprobar la recuperación. Por ello se solicita una batería de pruebas con el fin de conocer el programa y comprobar que funciona correctamente.

1. La copia 2 llamada “copia imágenes”, tendrá las siguientes características:

        1.1.Copia sin cifrar con origen en la carpeta Imágenes del servidor y destino tu cuenta de Google Drive. 

        1.2.Para esta carpeta solo podemos aceptar la pérdida de datos de máximo 1 día de tiempo, y se genera información en esta carpeta de lunes a domingo.
 
        1.3.Ten en cuenta que además de configurar la copia, es imprescindible comprobar la recuperación. Por ello se solicita una batería de pruebas con el fin de conocer el programa y comprobar funciona correctamente.

2. Recuperación de datos perdidos

        2.1. Leer el enlace: https://www.lavanguardia.com/tecnologia/20160806/403712293181/metodo-gutmann-barcenas-disco-duro-pp-formatear-dos-pasadas.html 

        2.2. Instalar dos herramientas de recuperación estilo Recuva, y realizar una prueba para comprobar la recuperación de datos con ambos. Usar una unidad extraible (USB)i comprobar los resultados

        2.3. ¿Se ha recuperado nos datos que estaban eliminados?

        2.4. Al USB hay que realizar un "formateo rapido" ofrecido por Windows. ¿Se ouede recuperar la información con ambas herramientas?

        2.5. ¿Formateo completo, que pasa?
        
        2.6. usar la aplicación de sobreescritura del siguiente enlace: https://www.google.com/url?q=https://eraser.heidi.ie/download/&sa=D&source=docs&ust=1667577894709242&usg=AOvVaw14FjCC0DtC9Eth2JxBSUw5 
        Comprobar si se puede recuperar la información del dispositivo con el software anterior.
        
# SPRINT 4 : HARDENING APACHE

0. Instalación de Apache.

1. Configuraciones globales.

2. Ficheros de configuraciones

3. Configuración de usuarios y grupos

4. Ocultación de versiones. 

5. Exposición mínima de módulos.

6. Creación de virtualhost con tu nombre y apellido.

7. Configuración múltiple y de contexto: directiva options

8. Restricción de acceso al contenido: directiva Auth y Require. Aplica la configuración para autenticar el acceso mediante digest a uno de los directorios de tu virtualHost.

9. Ficheros .htaccess. ¿Para qué sirven?

10. ¿Cómo podemos evitar el hotlinking? Compruébalo.

11. Configuración HTTPS mediante let’s encrypt o OpenSSL. Crea los certificados para que tu virtualHost sea seguro, y obligatoriamente los accesos sean por HTTPS

12. Módulo mod_security. ¿Qué es mod_security?

13. Realiza un ataque DoS mediante Metasploit (Slowloris) y comprueba que efectivamente el servidor está inaccesible.

14. Clona e instala las reglas recomendadas OWASP. Habilita mod_security

15. Reglas para detectar SQLInjection
Realiza de nuevo el ataque DoS y comprueba que el servidor está accesible.

# SPRINT 5 : HARDENING SSH-APACHE

0. Configuración de acceso

        0.1. Instalación SSh
        
        0.2. Configuración de sesión
        
        0.3. Configuración de cifrado

1. Doble factor de autennticación en SSH

        1.1. Instalar i configurar paquetes requeridos


        1.2. Configurar la autenticación

        1.3. Añadir el secreto a “Google Authenticator”

# SPRINT 6 : ESCANEO DE VULNERABILIDADES

0. Descargar herramienta NESSUS

        0.1. Escanenrar vulnerabilidades que hay entre en una maquina servidor que yo configuré y otra maquina especifica que es un metasploitable.

1. Nmap --> investigar y realizar un escaneo de vulnerabilidades sobre equipos
