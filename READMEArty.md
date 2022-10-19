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
      5.1. Acceso controlado a carpetas: es sumamente importante mantenerlo              activo. Ya que esto permitirá que potenciales programas maliciosos            no pueda  tener control de tus archivos y carpetas. Además,                  tendrás opción de visualizar el historial de los bloqueos, agregar            o quitar carpetas protegidas y gestionar las aplicaciones que                tienen acceso controlado a tus archivos o carpetas. Comprueba que            tienes protegida la carpeta de Documentos del perfil de usuario,              ya que esta es la carpeta que utilizará el usuario para el trabajo            diario.  
      
      5.2. Recuperación de datos por ransomware: si utilizas OneDrive, podrás            configurar y gestionar la sincronización de tus archivos y                    carpetas (para nuestro caso, no es necesario, simplemente es que              informativo este paso para que sepáis que existe). Esto será de              gran utilidad, sobre todo, si es que llegas a ser víctima de                  este tipo de ataque, ya que todos los archivos estarán en tu                  espacio en la nube. Así también, ten presente que todos los                  cambios que hagas en los archivos sincronizados, los mismos se                verán reflejados en la sincronización con OneDrive en sí.
      
      
6. Comprueba que si hubiera un intento de intrusión en uno de los portátiles pordrían resetear la contraseña del administrador y acceder a la cuenta.

7. Ya has visto el peligro que supone el arranque de herramientas live. Aplica las medidas necesarias para contrarrestar este riesgo:

      7.1 Adecuada política de contraseñas: caducidad contraseñas, longitud,           símbolos, etc.
      7.2 Cifrado de disco.
      7.3 Comenta como evitas el arranque de herramientas live. 

 











