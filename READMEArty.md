# proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano
proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano created by GitHub Classroom

SPRINT 1 - HARDENING DE UBUNTU

Iniciamos el Sprint de hardening instalando en una máquina virtual Ubuntu Server 22.04  con interfaz gráfica.

Después visualizamos el video en Youtube del seminario de INCIBE para comenzar a realizar nuestro Hardening de Ubuntu.


A continuación empezamos con el apartado de asegurar las configuraciones globales. 
Este apartado tiene varios puntos.

ASEGURA LAS CONFIGURACIONES GLOBALES

1. Configurar arranque del GRUB. 

Es un aspecto importante en las tareas de Hardening ya que si la configuración no es segura un atacante con acceso al mismo podría vulnerar el servidor y podría ejecutar comandos como usuario root.
Para realizar una buena configuración del arranque debermos realizar lo siguiente:
- Establecer una contraseña de arranque
- Establecer los permisos del fichero de configuración de arranque
- Obligar al uso de contraseña en el modo "Single User"

2. Establecer una contraseña de arranque
Para establecer una contraseña de arranque del sistema se debe crear una contraseña cifrada, debe ser robusta y se recomienda que tenga al menos 14 caracteres, en los cuales se debe incluir letras, números, mayúsculas, minúsculas y signos.
Con el siguiente comando grub-mkpasswd-pbkdf2 creamos la contraseña para fortalecer la seguridad. Al introducir el comando nos pedirá introducir la contraseña. Nos devolverá un Hash con la contraseña cifrada.
Una vez creada la contraseña creamos un fichero con el nombre init-pwd para guardar el usuario y la contraseña cifrada.
![recorte contraseña](https://user-images.githubusercontent.com/92945214/195299601-07664b72-9334-45f4-b544-83b5bab94c33.png)

![recorte archivo init](https://user-images.githubusercontent.com/92945214/195300559-2dda5c2f-318c-4093-b9b6-7a11aff90da3.png)

3. Establecer permisos fichero de configuración de arranque.

Una vez creado el fichero init-pwd le damos permisos de ejecución con el siguiente comando chmod +x init-pwd. A continuación se actualiza el grub.
![recorte permisos ejecución](https://user-images.githubusercontent.com/92945214/195300789-631e5db3-a93b-44b5-8979-79c0cb3d301f.png)

![recorte update grub](https://user-images.githubusercontent.com/92945214/195306465-cc6a5474-9856-49bb-8596-5a93be60cd73.png)

Para comprobar que todo se ha realizado correctamente volvemos a reiniciar y comprobamos que en el gestor de arranque deberemos introducir la contraseña.
!!!Atención¡¡¡ El gestor de arranque está oculto deberemos realizar una serie de acciones antes para poder comprobar que lo que hemos hecho hasta ahora es correcto.
Desde consola entramos en el archivo Grub que se encuentra en /etc/default/grub y modificamos los parámetros:
GRUB_TIMEOUT_STYLE=hidden    CAMBIAMOS hidden por menu
GRUB_TIMEOUT=0   CAMBIAMOS EL 0 POR EL TIEMPO QUE QUERAMOS QUE APAREZCA EL MENU SE MIDE EN SEGUNDOS, EJEMPLO: 10
Una vez hecho esto hacemos un update al GRUB


![recorte configurar archivo grub](https://user-images.githubusercontent.com/92945214/195308872-79175afd-9c93-4bf9-8dca-1b351005da52.png)


![recorte parámetros archivo grub](https://user-images.githubusercontent.com/92945214/195309222-be7004f2-7b68-4ada-8236-ac7e019b997d.png)


![recorte parámetros cambiados archivo grub](https://user-images.githubusercontent.com/92945214/195310832-7f5d3deb-3095-4ada-ab4b-788812a53b80.png)


![recorte update grub](https://user-images.githubusercontent.com/92945214/195311661-b1505205-bf08-4d07-9d2a-f2dc2cbbc0bc.png)


Una vez realizado todo lo anterior reiniciamos el sistema y comprobamos que nos aparece el menú del gestor de arranque, entramos en el modo recovery entramos en actualizar gestor de arranque y comprobamos que nos pide la contraseña que hemos configurado en pasos anteriores.

![recorte entrar en revovery mode](https://user-images.githubusercontent.com/92945214/195312621-fc6b9ce7-e21b-4a22-af2a-4d8cea2f90b9.png)


![recorte menu gestor de arranque](https://user-images.githubusercontent.com/92945214/195312986-7c1bea16-cccf-490e-8db3-47f65f0c8d95.png)


![recorte solicitud de contraseña root para mantenimiento](https://user-images.githubusercontent.com/92945214/195313535-cfe2bf05-81b6-4fcd-8605-93d0659bebee.png)

4. Obligar al uso de contraseña en el modo "Single User"
El modo Single User se emplea para recuperar el sistema en caso de fallo, es decir, si no establecemos una contraseña al usuario root un atacante con acceso al servidor podría tener acceso privilegiado al mismo.
Para asignar una contraseña modo Single User se debe asignar una contraseña al usuario root y lo haremos ejecutando el comando passwd e introduciremos la contraseña deseada.

![recorte password Single User](https://user-images.githubusercontent.com/92945214/195315599-68231141-cc12-416c-beb9-f9a05632edcf.png)

![recorte password Single User introducida](https://user-images.githubusercontent.com/92945214/195316169-00bc21f8-6e5b-4b5e-be89-6cb8dbf7ded6.png)

Una vez asignada la contraseña al usuario root debemos configurar los permisos para que solamente el usuario root pueda tener acceso a dicho fichero. Para ello debemos ejecutar el siguiente comando chmod 400 /boot/grub/grub.cfg de esta manera el usuario root será el´único que tenga acceso y solo tendrá acceso de lectura. 
Podemos comprobar con el comando stat /boot/grub/grub.cfg el estado del archivo grub.cfg 

![recorte permisos Single User y comprobación del archivo con stat](https://user-images.githubusercontent.com/92945214/195317823-5bdb2496-4a2c-415b-a7d1-41000d34b213.png)

Aquí concluyen las tareas incluidas en Asegurar las configuraciones globales.


CONFIGURACIÓN DE USUARIOS Y GRUPOS. CREA UN USUARIO ADMINISTRADOR CON TU NOMBRE, Y AÑADE ESTE AL GRUPO DE SUDOERS. ADEMÁS, APLICA UNA POLÍTICA DE CONTRASEÑA ADECUADA.

1. COMPLEJIDAD
2. REUTILIZACIÓN DE CONTRASEÑAS
3. ALMACENAMIENTO DE CONTRASEÑAS. COMPRUEBA COMO UN HASH PUEDE SER ROTO SI EL CIFRADO NO ES EL ADECUADO. SIGUE ESTE TUTORIAL
4. AHORA YA HAS EVIDENCIADO LA IMPORTANCIA DE REALIZAR ALMACENAMIENTO SEGURO DE CONTRASEÑAS COMO POR EJEMPLO SHA512. UNA VEZ ESTABLECIDO VUELVE A PROCEDER AL ATAQUE.
5. CONFIGURACIÓN DEL ENTORNO (CADUCIDAD Y CAMBIO DE CONTRASEÑA, TIMEOUT DE INACTIVIDAD, BLOQUEO DE CUENTA TRAS VARIOS INTENTOS, ETC)



ACTUALIZACIONES DE SOFTWARE








Para comprobar que ha tenido éxito nuestra configuración del GRUB debemos configurar el acceso al gestor de arranque ya que cuando iniciamos el ordenador éste permanece oculto y no nos lo muestra. Una vez realizada esta operación (ver capturas de pantalla) podemos comprobar que todas las operaciones de hardening que hemos realizado funcionan correctamente.   
