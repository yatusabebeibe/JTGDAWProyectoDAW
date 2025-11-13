[< Volver atrás](README.md)

- [Plesk](#plesk)
  - [Como acceder](#como-acceder)
  - [Subir los sitios](#subir-los-sitios)

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

