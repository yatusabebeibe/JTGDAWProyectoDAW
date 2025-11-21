[< Volver atrás](README.md)

- [Plesk](#plesk)
  - [Como acceder](#como-acceder)
  - [Subir los sitios](#subir-los-sitios)
  - [Sitios Virtuales](#sitios-virtuales)
  - [Creación de subdominios](#creación-de-subdominios)
  - [Creación de bases de datos](#creación-de-bases-de-datos)

---

> **Jesús Temprano Gallego**  
> Curso: 2025/2026  
> 2º Curso CFGS Desarrollo de Aplicaciones Web  
> Despliegue de aplicaciones web

# Plesk

Panel de control web para administrar servidores y sitios web fácilmente. \
Permite gestionar dominios, correos, bases de datos y archivos desde una interfaz gráfica. \
Incluye opciones para instalar aplicaciones, configurar seguridad y automatizar tareas del servidor.

## Como acceder

Para acceder a Plesk vamos a la url donde este el servidor web, pero por el puerto 8443.

En nuestro caso la url es: [`https://ieslossauces.es:8443`](https://ieslossauces.es:8443).

Ponemos nuestro usuario y contraseña y le damos a iniciar sesión y ya estaríamos dentro.

## Subir los sitios

En la pagina principal de administración, hacemos click en **FTP**.

Seleccionamos nuestra cuenta y nos aparecerá un apartado para configurar los datos de nuestra configuración ftp para subir archivos. \
Ponemos una contraseña que recordemos, y también recordamos la dirección ip con la que accederemos por ftp, y le damos a guardar.

Vamos la GitHub del repositorio que queramos subir, y en las releases descargamos el source code en Zip y lo extraemos en nuestro pc.

Luego, nos conectamos con un cliente S/FTP como FileZilla, MovaXterm o WinSCP; y metemos los archivos y carpetas extraídos del zip a la carpeta del servidor que queramos.

## Sitios Virtuales

En la pagina principal de administración, en nuestro dominio vamos al apartado de **"Hosting y DNS"**, y hacemos click en **DNS**.

Le damos a **"Añadir registro"**.

Creamos un tipo de registro **A**, ponemos el nombre de dominio que queramos para el subdominio, el TTL no lo tocamos y ponemos la dirección ip de nuestro servidor.

Una vez le demos a aceptar, nos dirá que hay que actualizar los registros DNS. \
Le damos click en actualizar y ya estaría.

Seguimos en [esta](ServidorDeDesarrollo.md#hosts-virtuales) parte.

## Creación de subdominios

En la pagina principal de administración, hacemos click en **"Añadir subdominio"**.

En esta pagina pondremos el nombre del subdominio; y luego en **"Raíz del documento"** ponemos la ruta a la carpeta que será la pagina principal de ese subdominio. \
Por ejemplo, si queremos poner la aplicación al tema 4 de DWES la ruta sería `/httpdocs/JTGDWESProyectoTema4`.

Una vez terminado, le damos a aceptar y ya estaría.

## Creación de bases de datos

En la pagina principal de administración, en nuestro dominio principal vamos a **"Bases de datos"**, y dentro le damos a **"Añadir base de datos"**.

En el menú que se nos abrirá le ponemos un nombre a la base de datos, en sitio relacionado seleccionamos el [Subdominio](#creación-de-subdominios) al que estará asociada la BD.

Abajo, creamos el usuario que se usara con esa base de datos. \
El nombre del usuario será el indicado según el estándar de desarrollo; y para la contraseña, dado que necesita tener un mínimo de seguridad tenemos que generar o crear una que cumpla con los requisitos de Plesk.

Y para importar el script SQL de borrado, creación y carga inicial de las tablas, en la pantalla para gestionar las bases de datos, tenemos que meter cada script en un `.zip` (*O crear un solo script y meterlo en un `.zip`*). \
Luego seleccionamos la DB en la que queramos importar los scripts y le damos a **"Importar volcado"**, le damos a **"Seleccionar archivo"** desde el ordenador local y seleccionamos el `.zip` con el/los script/s SQL.

Hecho esto, ya estaría la DB creada.