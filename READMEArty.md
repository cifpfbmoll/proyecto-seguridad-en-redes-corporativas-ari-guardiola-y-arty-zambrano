# proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano


SPRINT 1 - HARDENING DE UBUNTU



ASEGURA LAS CONFIGURACIONES GLOBALES

1. Configurar arranque del GRUB. 

- Establecer una contraseña de arranque
- Establecer los permisos del fichero de configuración de arranque
- Obligar al uso de contraseña en el modo "Single User"



CONFIGURACIÓN DE USUARIOS Y GRUPOS. CREA UN USUARIO ADMINISTRADOR CON TU NOMBRE, Y AÑADE ESTE AL GRUPO DE SUDOERS. ADEMÁS, APLICA UNA POLÍTICA DE CONTRASEÑA ADECUADA.


1. COMPLEJIDAD
Para la complejidad de contraseñas debemos instalar el siguiente paquete libpam-pwquality, utilizaremos el comando apt install libpam-pwquality.

![recorte instalación libpam-pwquality](https://user-images.githubusercontent.com/92945214/195324656-904bd6bc-0a2a-475d-a430-d4fad8b4aa4b.png)

Seguidamente tenemos que editar el archivo pwquality.conf y se deben cambiar los siguientes valores.

![recorte editar pwquality.conf](https://user-images.githubusercontent.com/92945214/195329142-25fcaf55-bb12-4ec0-be36-778eba99a6e5.png)

![recorte archivo pwquality.cont ](https://user-images.githubusercontent.com/92945214/195329370-d346887e-e65e-4c39-9c14-415464cf2a6c.png)

Los valores que se deben cambiar en el archivo pwquality.conf son los siguientes:
minlen se debe cambiar minlen que por defecto tiene el número 8 y cambiaremos a
minlen = 14 
de esta manera la contraseña deberá tener un mínimo de 14 caracteres.

![recorte minlen](https://user-images.githubusercontent.com/92945214/195330981-3c7ece5a-5163-4efc-b85b-888d9ab0ec7c.png)

También cambiaremos minclass que por defecto tiene el número 0 y lo cambiaremos a
minclass = 4
de esta manera la contraseña debera tener al menos un caracter de los 4 grupos que son: números, mayúsculas, minúsculas y símbolos.
!!!ATENCIÓN¡¡¡ si al editar el fichero estas líneas están comentadas deberemos descomentarlas.


![recorte minclass](https://user-images.githubusercontent.com/92945214/195331069-9c733627-093b-4b8f-8c44-2305ea2aa6ca.png)

A continuación para poner el numero de intentos fallidos antes de que se muestre el mensaje de error, deberemos editar el siguiente fichero en la siguiente ruta /etc/pam.d/common-password

![recorte archivo common-password](https://user-images.githubusercontent.com/92945214/195332100-e20e2b02-081a-43e4-8e20-7195e6e38e3b.png)

![recorte editar archivo common-password](https://user-images.githubusercontent.com/92945214/195332297-7a8b1133-1f9b-472c-a25b-12fcbf5bff42.png)

Una vez dentro del archivo buscamos la línea que contenga retry deberíamos configurar este parámetro a 3 o menos. Lo configuraremos con 3 intentos antes de que salga el mensaje de error.

![recorte password retry](https://user-images.githubusercontent.com/92945214/195332897-29b363e2-9ce9-4a23-bdf0-28b28a4361e5.png)


2. REUTILIZACIÓN DE CONTRASEÑAS.

Para evitar la reutilización de contraseñas se debe configurar primero la cantidad de contraseñas que no se pueden utilizar. Se recomienda un valor de 5 contraseñas.
Para ello se tiene que editar el siguiente fichero /etc/pam.d/common-password y debemos añadir la siguiente línea:
password required pam_pwhistory.so remember=5

![recorte archivo reutilizar contraseñas](https://user-images.githubusercontent.com/92945214/195523229-482d8aa2-637a-4608-8f3e-db6aff9558b8.png)

![recorte añadir línea reutilizar contraseñas](https://user-images.githubusercontent.com/92945214/195523312-2e65c58d-4eea-4513-b3a9-ddcd99951de0.png)


3. ALMACENAMIENTO DE CONTRASEÑAS. COMPRUEBA COMO UN HASH PUEDE SER ROTO SI EL CIFRADO NO ES EL ADECUADO. 

El almacenamiento de contraseñas debe ser cifrado con un algoritmo robusto se recomienda el sha512.
Para configurarlo debemos editar el fichero /etc/pam.d/common-password y debemos comprobar la línea siguiente:
"password [success =11  default=ignore ] pam_unix.so  obscure  use_authtok  try_first_pass sha512"
Si no está establecido el algoritmo lo debemos establecer el algoritmo y forzar que todos los usuarios cambien su contraseña.

![recorte algoritmo sha512](https://user-images.githubusercontent.com/92945214/195525783-9b4a2288-4539-4719-832b-e81849ec5e95.png)


4. AHORA YA HAS EVIDENCIADO LA IMPORTANCIA DE REALIZAR ALMACENAMIENTO SEGURO DE CONTRASEÑAS COMO POR EJEMPLO SHA512. UNA VEZ ESTABLECIDO VUELVE A PROCEDER AL ATAQUE.

SE HA REALIZADO EL CAMBIO DEL ALGORITMO SHA512.
FALTA REALIZAR EL ATAQUE PARA ROMPER EL HASH....



5. CONFIGURACIÓN DEL ENTORNO (CADUCIDAD Y CAMBIO DE CONTRASEÑA, TIMEOUT DE INACTIVIDAD, BLOQUEO DE CUENTA TRAS VARIOS INTENTOS, ETC)


El período de caducidad de una contraseña se debe establecer como mínimo cada 90 días y en el caso de servidores muy críticos cada 45 días. Para editar la caducidad de la contraseña debemos ir al fichero siguiente:
/etc/login.defs
se deben establecer los siguientes valores: PASS_MAX_DAYS  que por defecto pone 99999 deberemos cambiarlo a 90 y el PASS_MIN_DAYS que por defecto marca 0 lo cambiaremos a 1. 
Querdaría de la siguiente manera: 
PASS_MAX_DAYS 90   
PASS_MIN_DAYS  1 
De esta manera la contraseña caducará cada 90 días. 

![recorte caducidad contraseña](https://user-images.githubusercontent.com/92945214/195585874-a760838d-6dab-4932-be5f-79b29c923f89.png)

![recorte caducidad contraseña 90 días](https://user-images.githubusercontent.com/92945214/195587136-eb97c04f-b3f2-4ec5-b145-76b71ac17899.png)

Otra cosa a tener en cuenta en la configuración del entorno es el BLOQUEO DE CUENTAS POR INACTIVIDAD ya que puede suponer una vulnerabilidad en el sistema. Se recomienda que este valor se fije en 30 días como máximo.
Para configurar este parámetro cuando creamos una nueva cuenta de usuario tenemos que utilizar el siguiente comando:
useradd -D -f 30

Para cambiar el parámetro si los ususarios ya existen se debe utilizar otro comando que es:
chage  -inactive 30 "nombre de usuario"

![recorte bloqueo cuenta por inactividad usuario existente](https://user-images.githubusercontent.com/92945214/195592945-61718c1b-289c-4aa7-8df7-01e4d5a25004.png)


Otro aspecto a tener en cuenta es el TIMEOUT DE INACTIVIDAD para la consola de comandos, es decir, cuánto tiempo podemos tener la consola abierta sin actividad por parte del usuario. 
No congigurar esta opción puede ocasionar que se produzcan accesos no autorizados si un usuario dejase su puesto desatendido, sin bloquear y con una conexión abierta. 
Esta característica, por defecto, no tiene ningún valor establecido. Si tenemos que cambiar este parámetro para editarlo necesitaremos acceder al siguiente fichero:
/etc/bash.bashrc
y tendremos que añadir las siguientes líneas:
readonly TMOUT=900
export TMOUT

De esta manera hemos configurado un timeout de 15 minutos.

![recorte inactividd consola](https://user-images.githubusercontent.com/92945214/195592442-e7ce58db-4a2d-4e82-863c-30fdf79aab55.png)

Bloqueo de cuenta tras fallos de autenticación.

Se pueden realizar ataques de fuerza bruta para adivinar la contraseña de un usuario, en estos casos, se debe proteger el sistema de forma que no le sea posible al atacante realizar esta acción, pero tampoco debemos perjudicar al usuario atacado.
Para evitar estos ataques se deberían configurar un número máximo de intentos de acceso fallidos tras los cuales se bloquea la cuenta temporalmente. Normalmente se suelen configurar el número de intentos en 5 y el tiempo que la cuenta está bloqueada de 15 minutos, ya que si se bloquease la cuenta indefinidamente se podría provocar una denegación de servicio.
Para configurar la opción de bloqueo de cuenta por fallos de autenticación debemos editar el fichero siquiente:
/etc/pam.d/common-auth
y añadimos la línea:
auth required pam-tally2.so onerr=fail audit silent deny=5 unlock_time =900
Donde deny indica el número de intentos tras los cuales se bloqueará la cuenta y unlock_time indica el tiempo en segundo que tardará la cuenta en desbloquearse.

![recorte comando configurar bloqueo](https://user-images.githubusercontent.com/92945214/195714810-91292ec9-0384-4c14-8c61-85199b28c263.png)

![recorte línea para bloqueo de cuenta](https://user-images.githubusercontent.com/92945214/195715561-dae33878-0ab2-4aca-9bce-7894a8889086.png)

Seguidamente accedemos al siguiente fichero:
/etc/pam.d/common-account
y añadimos, si no lo están ya, las siguientes líneas:
account requisite pam-deny.so
account required pam.tally.so


![recorte archivo common-account](https://user-images.githubusercontent.com/92945214/195716534-54d9ac98-a5c9-40c4-a215-0f7cfa24b09f.png)

![recorte líneas añadidas en common-account](https://user-images.githubusercontent.com/92945214/195717066-b30f8bbe-ecc8-46d4-9bd1-c3d557478403.png)

Las cuentas de servicio deben estar configuradas para no establecer consolas interactivas, es decir, que no puedan autenticarse en el sistema y ejecutar comandos.
Por eso  deben estar todas ellas configuradas al tipo de consola establecida nologin.
Debemos acceder al siguiente fichero para configurar esta opción:
/etc/passwd
Como se puede apreciar en la captura de pantalla esta configuración ya viene por defecto. Todas vienen con el tipo establecido nologin.

![recorte nologin](https://user-images.githubusercontent.com/92945214/195718242-b18129a8-1aa0-46a2-9c4d-764d1685ba77.png)

El parámetro de configuración umask establece los permisos por defecto que se le asignan a un fichero creados por un usuario. El valor ideal para este parámetro es 027 que quiere decir control total para el creador del fichero. Permisos de lectura y ejecución para los usuarios pertenecientes al grupo y acceso denegado para el resto de ususarios.
Para modificar estos valores es necedario añadir o modificar el comando umask 027 en los siguientes ficheros:
/etc/bash.bashrc
/etc/profile
y en todos los scripts del directorio:
/etc/profile.d/



Restringir el acceso al comando su
El comando su permite ejecutar comandos en nombre de otro usuario, es útil en según que situaciones que se deban elevar privilegios para ciertas tareas, el problema es que no permite el control de los comandos que se ejecutan no se pueden especificar los comandos permitidos. Para estas tareas se desarrolló la herramienta sudo, que permite un control de los comandos ejecutados. Al restrigir el uso de su y sudo en su lugar, porporciona a los administradores del sistema un mejor control de la ejecución de comandos con privilegios altos. Además sudo proporciona un mejor mecanismo de registro y auditoría ya que puede registra cada comando ejecutado mientra que con su solo queda registrada la ejecución de éste. 
Para restringir el uso de su y utilizar sudo, se debe crear un grupo vacío, en este caso lo vamos a llamar "sugroup" realizamos esto con el comando:
groupadd sugroup
y en el fichero siguiente:
/etc/pam.d/su  añadiremos la siguiente línea:
auth required pam_wheel.so use_uid group=sugroup
A partir de aquí solo podrán ejecutar el comando su los usuarios que pertenezcan al grupo "sugroup"


![recorte grupo sugroup](https://user-images.githubusercontent.com/92945214/195881023-98715605-2d9f-4e9a-ba1f-d0eca648cd08.png)

![recorte línea añadida sugroup](https://user-images.githubusercontent.com/92945214/195881418-e09d7cc0-c3dc-4192-9cf7-d4c79395809f.png)





ACTUALIZACIONES DE SOFTWARE
Las distribuciones Debian y en particular Ubuntu utilizan el sistema APT (Advanced Package Tool) para la actualización de paquetes de software.
Estas actualizaciones deben estar basadas en las políticas establecidas y se recomienda actualizar de manera períodica.
Estas actualizaciones se pueden configurar para instalar directamente o si antes se deben aplicar a un entorno de preproducción.

A continuación configuraremos el sistema de actualizaciones.
Configuramos Advanced Package Tool
Se deben configurar los repositorios con fuentes fiables y nos aseguramos de que estan configuradas las claves GPG para verificar la integridad de los paquetes durante la instalación.
Los repositorios los configuraremos desde el siguiente fichero:
/etc/apt/sources.list

![recorte archivo recursos apt](https://user-images.githubusercontent.com/92945214/195872329-146eadba-ffab-4126-af91-e38436e249fb.png)

Por defecto vienen incluidos los repositorios oficiales y podemos añadir repositorios adicionales que deben proceder de fuentes fiables y queda a criterio de las políticas establecidas.
De los repositorios oficiales existen de varios tipos:
MAIN RESTRICTED
UNIVERSE
MULTIVERSE
Se recomienda habilitar solamente los repositorios main restricted ya que son los únicos 100% probados y con soporte. El resto de repositorios continen software que no ha sido 100% probado y no tiene soporte.

![recorte tipos de repositorios](https://user-images.githubusercontent.com/92945214/195874976-5f76a7e5-bef5-477c-bb3f-4bdd85346c84.png)

Para deshabilitar estos repositorios lo único que se debe hacer es comentar las líneas de los repositorios UNIVERSE y MULTIVERSE.

![recorte deshabilitar repositorios](https://user-images.githubusercontent.com/92945214/195876230-00bfcf10-bd2d-4c79-91be-b0178e10855b.png)

Cada vez que hagamos un cambio en el fichero de los repositorios es necesario ejecutar un apt update para actualizar los paquetes disponibles.
Para instalar software de terceros es recomendable descargarlos siempre desde los repositorios oficiales del proveedor y mantenerlos actualizados.

![recorte apt upgrade](https://user-images.githubusercontent.com/92945214/195879109-9cd924c3-d3ae-4369-98f9-45fad451e00d.png)








