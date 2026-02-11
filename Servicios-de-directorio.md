Resultados de aprendizaje
Al finalizar esta unidad, el alumno/a:

###RA3. Realiza tareas de gestión sobre dominios identificando necesidades y aplicando herramientas de administración de dominios.

Criterios de evaluación:

a) Se ha identificado la función del servicio de directorio, sus elementos y nomenclatura.
- __Identifica__ la función de servicio de directorio y dominio, estructura, sus elementos y nomenclatura.

b) Se ha reconocido el concepto de dominio y sus funciones.
- __Identifica__ y __aplica__ directrices en la gestión del dominio

c) Se han establecido relaciones de confianza entre dominios.
- __Realiza__ la instalación y configuración básica del servicio de directorio y establece relaciones de confianza.

d) Se ha realizado la instalación del servicio de directorio.
- __Utiliza__ herramientas gráficas de administración de dominio y consolas de administración.

e) Se ha realizado la configuración básica del servicio de directorio.
- __Crea, configura y gestiona__ cuentas de usuario, grupos, equipos y distintos tipos de perfiles.

f) Se han utilizado agrupaciones de elementos para la creación de modelos administrativos.
- __Usa__ agrupaciones de elementos para la creación de modelos administrativos.

g) Se ha analizado la estructura del servicio de directorio. 
- __Especifica__ el propósito de los grupos, sus tipos y ámbitos, y gestiona la pertenencia de usuarios a grupos.
- __Identifica__ las características de usuarios y grupos predeterminados y especiales.

h) Se han utilizado herramientas de administración de dominios.
- __Utiliza__ herramientas para la administración de usuarios y grupos, incluidas en el sistema operativo en red.
  
- __Verifica__ la corrección de las tareas realizadas y documenta adecuadamente las tareas de gestión y administración de dominios realizadas.



(1) Recordar, (2) Comprender, (3) Aplicar (4) Analizar, (5) Evaluar, (6) Crear

# Contenidos:
> - Protocolo de acceso a directorios: LDAP.
> - Introducción al concepto de directorio y dominio
> - Pasos creación de un dominio
> - Herramientas administrativas para dominios

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

_Autenticación simple_ , en la que el directorio mantiene almacenada la contraseña de cada _usuario. Cuando el usuario accede al directorio, realiza una comparación con el valor almacenado. Si lo comparamos con una carta, equivaldría al servicio que ofrece la firma a pie de página.
_Autenticación fuerte_ , en la que el directorio mantiene almacenadas claves de cifrado para autenticar al usuario. Siguiendo con la comparación, el cifrado de mensajes equivaldría a cerrar el sobre y añadir un lacre digital para impedir que terceras personas lo abrieran.


<img width="967" height="453" alt="image" src="https://github.com/user-attachments/assets/c5e6e4ee-8e8b-40f5-a6c7-d1244c97b367" />

