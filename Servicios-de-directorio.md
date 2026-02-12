
# 1. ¿Qué es un directorio?

> Un directorio es una base de datos especializada que almacena información sobre los recursos o entidades existentes en una red, como usuarios, ordenadores o impresoras, y la pone a disposición de los usuarios de la red.

# 2. ¿Para que sirve este directorio?
_Función principal:_ 

> La función principal de un directorio electrónico es tener la información organizada de forma estructurada, para que desde los diferentes sitios de la red que disponen de un servicio de directorio se pueda acceder a los datos que se almacenan y actualizarlos. 

# 3. ¿Qué es un servicio de directorio?

> Un servicio de directorio constituye un conjunto de elementos, formado por software y hardware, que trabajan juntos para almacenar, organizar y gestionar la información referente a los usuarios y los recursos de una red. Los servicios de directorio actúan como una capa de abstracción entre los usuarios y los recursos compartidos y permiten a los administradores gestionar el acceso de los usuarios a los recursos de la red.

# 4. ¿Explica la direfencia entre un directorio y el servicio de directorio?

> El directorio constituye la base de datos en la que se almacena la información, mientras que el servicio de directorio es la infraestructura física y lógica que permite gestionar los datos del directorio

# 5. ¿Nombra algunas de las principales utilidades de los servicios de directorios?

> _Utilidades de un servicio de directorio:_ Algunas de las principales utilidades de los servicios de directorio son la búsqueda y gestión de información dentro de una red y el hecho de garantizar la seguridad de acceso a la red mediante su uso para la autenticación de usuarios.
Es decir:
- Encontrar información
- Gestionar información
- Seguridad

# 6. ¿Nombra y describe los dos mecanismos que utilizan los servicios de directorio para realizar funcciones de autenticación?
   
> Los servicios de directorio pueden realizar funciones de autenticación de usuario mediante dos tipos de mecanismos:

- _Autenticación simple_ , en la que el directorio mantiene almacenada la contraseña de cada _usuario. Cuando el usuario accede al directorio, realiza una comparación con el valor almacenado. Si lo comparamos con una carta, equivaldría al servicio que ofrece la firma a pie de página.
- _Autenticación fuerte_ , en la que el directorio mantiene almacenadas claves de cifrado para autenticar al usuario. Siguiendo con la comparación, el cifrado de mensajes equivaldría a cerrar el sobre y añadir un lacre digital para impedir que terceras personas lo abrieran.

# 7. ¿Qué define una política de seguridad en el servicico de directorio?

> La política de seguridad define define el "qué" (usuarios) y el "porqué" (uso), y el "cómo" (listas de control de acceso) que para llevarla a cabo se necesita un método para autenticar al usuario. 

> Una vez verificada la identidad del cliente, se puede determinar si está autorizado a llevar a cabo la operación solicitada o no.

# 8. ¿Qué son las ACL?

> ACL (Acces Control List o Lista de control de acceso) es un concepto de seguridad utilizado para dar privilegios o no a un objeto determinado que está haciendo una petición. En general las ACL (Access Control Lists o Listas de Control de Acceso) son conjuntos de reglas secuenciales aplicadas a dispositivos de red (routers, firewalls) o sistemas de archivos para filtrar el tráfico y gestionar permisos. 

# 9 ¿Qué es LDAP?

> LDAP es un protocolo abierto a escala de aplicación, del tipo cliente-servidor, que se utiliza para acceder a un servicio de directorio.

# 10 ¿Cuál es el objetivo de LDAP?

> El objetivo principal es permitir la autenticación en red .


# 11 ¿Cuál es el funcionamiento de LDAP?

> El servicio de directorio LDAP, como casi todos los servicios de directorio, tiene una arquitectura cliente-servidor. En este modelo, uno o varios servidores LDAP contienen los datos que conforman el árbol de directorio LDAP o base de datos jerárquica. La aplicación que hace de cliente LDAP se conecta con el servidor LDAP y le hace una consulta . El servidor contesta con la respuesta correspondiente o indica el lugar donde el cliente puede encontrar más información. Normalmente, este sitio será otro servidor LDAP.



# ¿Qué es la autenticación en términos de seguridad de redes?

> La autenticación es el acto de establecimiento o confirmación de algo o persona como auténtica. La autenticación de un objeto puede significar la confirmación de su procedencia, mientras que la autenticación de una persona a menudo consiste en verificar su identidad.

# ¿Qué es la autenticación en términos de seguridad de redes?

Autorización , es el proceso por el que la red autoriza al usuario identificado a acceder a determinados recursos de esta red.

# ¿Qué es la auditoria en términos de seguridad de redes?

Auditoría , mediante la cual la red o sistemas asociados registran todos los accesos a los recursos que hacen los usuarios autorizados o no.


Para entender mejor el funcionamiento de la autenticación en los sistemas GNU/Linux, es necesario saber qué archivos y herramientas utilizan los sistemas para gestionar las cuentas de usuarios y grupos, y sus perfiles.
# ¿Qué archivos y herramientas utilizan los sistemas para gestionar las cuentas de usuarios y grupos, y sus perfiles.?

### Archivos
> - El archivo /etc/passwd es el que utilizan los sistemas GNU/Linux para almacenar la información de los usuarios del sistema. Todos los usuarios deben tener una entrada en este archivo para poder acceder al sistema.
> - El archivo /etc/group es el que utilizan los sistemas GNU/Linux para almacenar la información de los grupos existentes en el sistema. Todos los grupos deben tener una entrada en este archivo y todos los usuarios deben pertenecer a algún grupo.
> - El archivo /etc/shadow es el archivo en el que los sistemas GNU/Linux almacenan las contraseñas cifradas de los usuarios para garantizar el acceso al sistema. Por motivos de seguridad, este archivo sólo puede editarlo el superusuario y sólo lo pueden leer los usuarios que pertenecen al grupo del superusuario.

### Herramientas

Herramientas de gestión de usuarios
Entre las órdenes que proporciona el sistema, están las siguientes:
> - __useradd__, __adduser__, __groupadd__, __addgroup__: estos comandos permiten al superusuario crear nuevos usuarios y grupos en el sistema. Dependiendo de la distribución con la que trabajemos, estas órdenes funcionan igual o no. En Ubuntu existen diferencias entre estas órdenes. Los comandos adduser y addgroup son más completos, ya que realmente son scripts de Perl que utilizan los comandos useradd y groupadd para crear usuarios y grupos. De hecho, los mandatos adduser y addgroup le permiten crear todos los parámetros (la contraseña, el directorio del usuario…) de los usuarios y grupos a la vez.
> - __usermod__, __groupmod__: son órdenes que se utilizan para modificar la información sobre los usuarios y los grupos respectivamente. Sólo puede utilizarlas el usuario root.
> - __userdel__, __deluser__, __groupdel__, __delgroup__: permiten al superusuario borrar usuarios y grupos del sistema. El funcionamiento depende también de cada distribución, como en el caso de las órdenes de creación. El mandato userdel -r eliminará también la carpeta del usuario.
> - passwd: comando que se utiliza para establecer o actualizar la contraseña de los usuarios existentes en el sistema.

<img width="967" height="453" alt="image" src="https://github.com/user-attachments/assets/c5e6e4ee-8e8b-40f5-a6c7-d1244c97b367" />

