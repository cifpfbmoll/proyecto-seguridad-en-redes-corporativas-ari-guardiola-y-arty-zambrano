# proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano
proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano created by GitHub Classroom

# SPRINT 1
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

#SPRINT 2
0. Instalar S.O Windows 10
1. Crear otro usuario administrador y otro de empleador.
2. Desintalar programas que no estemos usando
3. Comprobar si esta habilitado el windows defender
4. Comprobar si esta habilitado la protección contra ransomware

        4.1.Acceso controlado a carpetas y comprobar la protección de la carpeta de Documento del perfil del usuario.
        
        6.2. Recuperación de datos por ransomware
        
5. Comprueba que si hubiera un intento de intrusión en uno de los portátiles si podrían resetear la contraseña del administrador y acceder a la cuenta.
6. Aplicar las medidas:

        6.1. Politica de contraseñas (caducidad, longitud,simbolos...)
        
        8.2. Cifrado de disco
     
        10.3. Comentar como evitar el arranque de herramientas live
