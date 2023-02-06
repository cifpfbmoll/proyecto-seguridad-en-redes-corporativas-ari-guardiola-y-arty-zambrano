# proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano
proyecto-seguridad-en-redes-corporativas-ari-guardiola-y-arty-zambrano created by GitHub Classroom
SPRINT I: HARDENING DE UBUNTU

  1. Asegura las configuraciones globales.
  2. Configuración de usuarios y grupos.
  3. Actualizaciones de software.



SPRINT II: HARDENING DE WINDOWS

  1. Crear otro usuario administrador y otro de empleador.
  2. Desintalar programas que no estemos usando.
  3. Comprobar si esta habilitado el windows defender.
  4. Comprobar si esta habilitado la protección contra ransomware.
  5. Comprobación de posible reseteo.
  6. Aplicar medidas



SPRINT III: COPIAS DE SEGURIDAD

  1. se solicita realizar dos copias de seguridad diferente:
     a. La copia 1 llamada “copia documentos”, tendrá las siguientes características:
       copia cifrada con origen en la carpeta Documentos del servidor y destino tu cuenta de Google Drive. 
       Para esta carpeta solo podemos aceptar la pérdida de datos de máximo 1 hora de tiempo, y se genera información en esta carpeta de lunes a viernes. 
       Ten en cuenta que además de configurar la copia, es imprescindible comprobar la recuperación. Por ello se solicita una batería de pruebas con el fin de conocer        el programa y comprobar que funciona correctamente.

     b. La copia 2 llamada “copia imágenes”, tendrá las siguientes características: Copia sin cifrar con origen en la carpeta Imágenes del servidor y destino tu cuenta         de Google Drive. Para esta carpeta solo podemos aceptar la pérdida de datos de máximo 1 día de tiempo, y se genera información en esta carpeta de lunes a               domingo. Ten en cuenta que además de configurar la copia, es imprescindible comprobar la recuperación. Por ello se solicita una batería de pruebas con el fin           de conocer el programa y comprobar funciona correctamente.

  2. Recuperación de datos perdidos:
    a. Instala dos herramientas de recuperación estilo Recuva, y realiza una prueba para comprobar la recuperación de los datos con ambos. Para ello, utiliza una              unidad extraíble y comprueba los resultados. ¿Has podido recuperar los datos cuando estos aparentemente estaban eliminados? 		
    b. Si utilizamos una unidad extraíble y realizamos el "formateo rápido" ofrecido por Windows, ¿podemos recuperar la información con ambas herramientas? ¿Y si              hacemos un formateo completo?	
    c. Prueba la siguiente aplicación de sobrescritura, y comprueba si puedes 	recuperar la información del dispositivo con el software anterior.

 

SPRINT IV: HARDENING APACHE

  1. Instalación de Apache.
  2. Configuraciones globales.
  3. Ficheros de configuraciones
  4. Configuración de usuarios y grupos
  5. Ocultación de versiones. 
  6. Exposición mínima de módulos.
  7. Creación de virtualhost con tu nombre y apellido.
  8. Configuración múltiple y de contexto: directiva options
  9. Restricción de acceso al contenido: directiva Auth y Require. Aplica la configuración para autenticar el acceso mediante digest a uno de los directorios de tu         virtualHost.
  10. Ficheros .htaccess. ¿Para qué sirven?
  11. ¿Cómo podemos evitar el hotlinking? Compruébalo.
  12. Configuración HTTPS mediante OpenSSL. Crea los certificados para que tu virtualHost sea seguro, y obligatoriamente los accesos sean por HTTPS
  13. Módulo mod_security. ¿Qué es mod_security?
  14. Realiza un ataque DoS mediante Metasploit (Slowloris) y comprueba que efectivamente el servidor está inaccesible.
  15. Clona e instala las reglas recomendadas OWASP. Habilita mod_security
  16. Reglas para detectar SQLInjection
  17. Realiza de nuevo el ataque DoS y comprueba que el servidor está accesible.



SPRINT V: HARDENING SSH

  1. Instalación de SSH.
  2. Configuración de sesión.
  3. Configuración de cifrado.
  4. Doble factor de autenticación.



SPRINT VI: ESCANEO DE VULNERABILIDADES

  * Objetivo: Conocer las principales herramientas de reconocimiento de vulnerabilidades, las       cuales ayudan a prevenir futuros ataques al sistema.
  * Lo que hay que hacer:
    1. Descargar e instalar la MV Metasploit2. 
    2. Realizar un escaneo del servidor con cualquiera de estas herramientas:
       a. Herramienta GUI: Nessus u Openvas.
       b. Nmap: Tener en cuenta su CheatSheet.
       
       
       
SPRINT VII: PFSENSE

  * Objetivo: Poner en práctica los conocimientos adquiridos sobre seguridad perimetral, y aplicar una arquitectura adecuada que asegure perimetralmente el sistema                   empleando una arquitectura Screened Subnet (DMZ).
  * Lo que hay que hacer: 
    1. Instala Pfsense con tres tarjetas de red: Wan (adaptador puente, Lan DMZ (Red Nat 10.0.3.0/24) y Lan Empleados (Red Nat 10.0.2.0/24).
    2. Configura el servidor adjudicando a su tarjeta de red Lan DMZ.
    3. Configura el equipo del empleado adjudicando a su tarjeta de red Lan Empleados.
    4. Utiliza la herramienta de ping de Pfsense, y comprueba que efectivamente el servidor y el equipo del empleado es accesible desde pfsense.
       a. Realiza un ping desde tu equipo local a Pfsense. Se supone que estará inaccesible, ya que por defecto se bloquean estas acciones. Compruébalo.
    5. Aplica una regla para que se permitan pings a Pfsense.
       a. Con la situación actual, las peticiones desde la Wan al servidor web, no serán atendidas (normal, no hemos configurado nada para que se puedan llevar a cabo). Compruébalo.
    6. Incluye una regla Nat Pfsense, de manera que las peticiones que lleguen al puerto 80 o 443 sean redirigidas al servidor Web. Comprueba que funciona tu                  configuración tanto en el puerto 80 como el 443.
    7. Aplica una regla de manera que se bloquee todo el tráfico en el puerto 80. Compruébalo.
    8. Incluye una regla Nat Pfsense, de manera que las peticiones que lleguen al puerto del servidor SSH sean redirigidas al servidor SSH. Comprueba que funciona tu configuración.
  
SPRINT VIII: IDS Y VPN CON PFSENSE

  * Objetivo: Poner en práctica los conocimientos adquiridos sobre seguridad perimetral, y configurar el cortafuegos pfSense habilitando el servicio IDS/IPS y servidor VPN correctamente.
  * Lo que hay que hacer:
    1. Instala IDS/IPS Suricata siguiendo esta guía.
    2. Aplica las reglas de la comunidad Snort.
    3. Antes de habilitar Suricata, realiza un ataque DoS sobre el servidor Web. 
    4. Habilita el IDS, y vuelve a realizar el ataque, comprobando que aparece en el log el ataque que se está realizando, además de proteger del mismo.
    5. Habilita el servidor VPN en pfSense siguiendo la guía. Comprueba su funcionamiento.
