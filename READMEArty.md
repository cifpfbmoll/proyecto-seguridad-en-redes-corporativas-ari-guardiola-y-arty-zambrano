# proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano


SPRINT 1 - HARDENING DE UBUNTU

1. INSTALA UBUNTU Y APLICA LAS CONFIGURACIONES QUE SE COMENTAN EN EL SEMINARO DE INCIBE.

2. ASEGURA LAS CONFIGURACIONES GLOBALES.

   2.1 Configurar arranque del GRUB.
   
   2.2 Establecer una contraseña de arranque.
   
   2.3 Establecer los permisos del fichero de configuración de arranque.
   
   2.4 Obligar al uso de contraseña en el modo "Single User".

3. CONFIGURACIÓN DE USUARIOS Y GRUPOS. CREA UN USUARIO ADMINISTRADOR CON TU NOMBRE, Y AÑADE ESTE AL GRUPO DE SUDOERS. ADEMÁS, APLICA UNA POLÍTICA DE CONTRASEÑA        ADECUADA.

   3.1 Complejidad.
   
   3.2 Reutilización de contraseñas.
   
   3.3 Almacenamiento de contraseñas. 
       Comprueba comu un hash puede ser roto si el cifrado no es el adecuado.
       
   3.4 Ahora ya has evidenciado la importancia de realizar almacenamiento seguro de contraseñas como por ejemplo SHA512. Una vez establecido vuelve a proceder al          ataque.
   
   3.5 Configuración del entorno. 
      (Caducidad y cambio de contraseña, Timeout de inactividad, Bloqueo de cuenta tras varios intentos, Etc.)
            
4. ACTUALIZACIONES DE SOFTWARE.





SPRINT 2 - HARDENING DE WINDOWS

US3 Los equipos de los empleados de son ordenadores portátiles, ya que necesitan en ocasiones teletrabajar.

1. Instala un S.O. Windows 11 o 10. Para simular en mejores condiciones la red local de los empleados del entorno empresarial, este equipo Windows 10 tendrá un usuario local (tu nombre y apellidos, sin active directory)

2. Este equipo será utilizado por un empleado que tendrá mínimos privilegios (no podrá instalar nada), por tanto, debe existir otro usuario administrador. Crea los dos ususarios con los privilegios adecuados, y comprueba su configuración.

3. Desinstalar programas que no estemos usando. Es peligroso que haya software que como administradores no tengamos controlada sus versiones. Como en el punto anterior hemos limitado la instalación a nuestro empleado en cuestión, podríamos decir que no deber haber programas no autorizados.

4. Utilizar Seguridad de Windows. Comprueba que efectivamente tienes habilitado Windows Defender.

5. Comprueba que tienes habilitado la protección contra ransomware. 

      5.1. Acceso controlado a carpetas: es sumamente importante mantenerlo activo. Ya que esto permitirá que potenciales programas maliciosos no pueda  tener control de tus archivos y carpetas. Además, tendrás opción de visualizar el historial de los bloqueos, agregar o quitar carpetas protegidas y gestionar las aplicaciones que    tienen acceso controlado a tus archivos o carpetas. Comprueba que tienes protegida la carpeta de Documentos del perfil de usuario, ya que esta es la carpeta que utilizará el usuario para el trabajo diario.  
      
      5.2. Recuperación de datos por ransomware: si utilizas OneDrive, podrás configurar y gestionar la sincronización de tus archivos y carpetas (para nuestro caso, no es necesario, simplemente es que informativo este paso para que sepáis que existe). Esto será de gran utilidad, sobre todo, si es que llegas a ser víctima de        este tipo de ataque, ya que todos los archivos estarán en tu espacio en la nube. Así también, ten presente que todos los cambios que hagas en los archivos sincronizados, los mismos se verán reflejados en la sincronización con OneDrive en sí.
      
      
6. Comprueba que si hubiera un intento de intrusión en uno de los portátiles pordrían resetear la contraseña del administrador y acceder a la cuenta.

7. Ya has visto el peligro que supone el arranque de herramientas live. Aplica las medidas necesarias para contrarrestar este riesgo:

      7.1 Adecuada política de contraseñas: caducidad contraseñas, longitud, símbolos, etc.
      
      7.2 Cifrado de disco.
      
      7.3 Comenta como evitas el arranque de herramientas live. 

 


SPRINT 3 - COPIAS DE SEGURIDAD

US4 COPIAS DE SEGURIDAD. ACTUALMENTE GRAN VARIEDAD DE SOLUCIONES BACKUP EN EL MERCADO. IMPORTANTE ELEGIR EL SOFTWARE QUE NOS APORTE TRANQUILIDAD Y SE AJUESTE A LAS NECESIDADES. LO PRINCIPAL ES ASEGURARNOS QUE EL PROGRAMA QUE SELECCIONAMOS NOS OFRECE LA FIABILIDAD Y CUBRE NECESIDADES. iMPRESCINDIBLE PROBARLO BIEN Y COMPROBAR RESTAURACIÓN DE LAS COPIAS CORRECTAS.
SOFTWARE EN LA MAYORÍA DE EMPRESAS VEAM BACKUP COMMUNITY EDITION.
TRABAJAREMOS CON DUPLICATI.

   CARACTERÍSTICAS PRINCIPALES DUPLICATI: 
   
   1. FUNCIONA CON PROTOCOLOS ESTÁNDAR FTP, SSH, WEBDAV TAMBIÉN CON BACKBLAZE B2, TARDIGRADE, MICROSOFT ONDRIVE, AMAZON S3, GOOGLE DRIVE, BOX.COM, MEGA, HUBIC Y           MÁS.
      
   2. COPIA SEGURIDAD DE ARCHIVOS Y CARPERTAS CON FUERTE ENCRIPTACIÓN AES-256. AHORRA ESPACIO CON COPIAS DE SEGURIDAD INCREMENTALES Y DEDUPLICACIÓN DE DATOS.             DUPLICATI TIENE UN PROGRAMADOR INCORPORADO Y UN ACTUALIZADOR AUTOMÁTICO.
      
   3. ES SOFTWARE LIBRE Y DE CÓDIGO ABIERTO. SE PUEDE UTILIZAR DUPLICATI DE FORMA GRATUITA INCLUSO CON FINES COMERCIALES. SE EJECUTA TANTO EN WINDOWS, LINUX Y MACOS
      
   4. FUE DISEÑADO PARA REALIZAR COPIAS DE SEGURIDAD EN LÍNEA DESDE CERO. NO SOLO ES EFICIENTE CON LOS DATOS, SINO QUE TAMBIÉN MANEJA LOS PROBLEMAS DE LA RED MUY         BIEN.


SE SOLICITA EN ESTA PRÁCTICA:

   1. COPIA 1 LLAMADA COPIA DOCUMENTOS CON LAS SIGUIENTES CARACTERÍSTICAS:
   
      1.1 COPIA CIFRADA CON ORIGEN EN LA CARPETA DOCUMENTOS DEL SERVIDOR Y DESTINO TU CUENTA DE GOOGLE DRIVE
      
      1.2 PARA ESTA CARPETA SOLO PODEMOS ACEPTAR LA PÉRDIDA DE DATOS DE MÁXIMO 1 HORA DE TIEMPO, Y SE GENERA INFORMACIÓN EN ESTA CARPETA DE LUNES A VIERNES.
      
      1.3 ADEMÁS DE CONFIGURAR LA COPIA, ES IMPRESCINDIBLE COMPROBAR LA RECUPERACIÓN. POR ELLO SE SOLICITA UNA BATERÍA DE PRUEBAS CON EL FIN DE CONOCER EL PROGRAMA           Y COMPROBAR QUE FUNCIONA CORRECTAMENTE.
   
   2. COPIA 2 LLAMADA COPIA IMÁGENES TENDRÁ LAS SIGUIENTES CARACTERÍSTICAS:
   
      2.1 COPIA SIN CIFRAR CON ORIGEN EN LA CARPETA IMÁGENES DEL SERVIDOR Y DESTINO TU CUENTA DE GOOGLE DRIVE.
      
      2.2 PARA ESTA CARPETA SOLO PODEMOS ACEPT LA PÉRDIDA DE DATOS DE MÁXIMO 1 DÍA DE TIEMPO, Y SE GENERA INFORMACIÓN EN ESTA CARPETA DE LUNES A DOMINGO
      
      2.3 ES IMPRESCINDIBLE COMPROBAR LA RECUPERACIÓN. SE SOLICITA UNA BATERÍA DE PRUEBAS CON EL FIN DE CONOCER EL PROGRAMA Y COMPROBAR QUE FUNCIONA CORRECTAMENTE.

US5 RECUPERACIÓN DE DATOS PERDIDOS.

   1. INSTALA DOS HERRAMIENTAS DE RECUPERACIÓN ESTILO RECUVA Y REALIZA UNA PRUEBA PARA COMPROBAR LA RECUPERACIÓN DE LOS DATOS DE AMBOS. UTILIZA UNA UNIDAD EXTRAIBLE       Y COMPRUEBA LOS RESULTADOS.
   
   3. ¿HAS PODIDO RECUPERAR LOS DATOS CUANDO ESTOS APARENTEMENTE ESTABAN ELIMINADOS?
   
   5. SI UTILIZAMOS UNA UNIDAD EXTRAIBLE Y REALIZAMOS EL "FORMATEO RÁPIDO" OFRECIDO POR WINDOWS, ¿PODEMOS RECUPERAR LA INFORMACIÓN CON AMBAS                               HERRAMIENTAS?
   
   6. ¿Y SI HACEMOS UN FORMATEO COPLETO?
   
   7. PROBAMOS LA APLICACION ERASER DE SOBREESCRITURA, Y COMPRUEBA SI PUEDES RECUPERAR LA INFORMACIÓN DEL DISPOSITIVO CON EL SOFTWARE ANTERIOR.












