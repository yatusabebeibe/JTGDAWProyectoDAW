[< Volver atrás](README.md)

- [Git](#git)
  - [Instalación](#instalación)
  - [Configuración](#configuración)
  - [Buenas prácticas](#buenas-prácticas)
  - [**Gestión de un repositorio (Terminal)**](#gestión-de-un-repositorio-terminal)
    - [Iniciar / Clonar repo](#iniciar--clonar-repo)
    - [Estado e historial](#estado-e-historial)
    - [Añadir y confirmar cambios](#añadir-y-confirmar-cambios)
    - [Crear y cambiar de ramas](#crear-y-cambiar-de-ramas)
    - [Fusionar ramas (merge) y conflictos](#fusionar-ramas-merge-y-conflictos)
    - [Conectar con remoto](#conectar-con-remoto)
    - [Subir y descargar cambios](#subir-y-descargar-cambios)
    - [Deshacer cambios](#deshacer-cambios)
    - [Etiquetas](#etiquetas)
  - [**Gestión de un repositorio (VSCode)**](#gestión-de-un-repositorio-vscode)
    - [Iniciar / Clonar repo](#iniciar--clonar-repo-1)
    - [Estado e historial](#estado-e-historial-1)
    - [Añadir y confirmar cambios](#añadir-y-confirmar-cambios-1)
    - [Crear y cambiar de ramas](#crear-y-cambiar-de-ramas-1)
    - [Fusionar ramas (merge) y conflictos](#fusionar-ramas-merge-y-conflictos-1)
    - [Conectar con remoto](#conectar-con-remoto-1)
    - [Subir y descargar cambios](#subir-y-descargar-cambios-1)
    - [Deshacer cambios](#deshacer-cambios-1)
    - [Etiquetas](#etiquetas-1)
- [GitHub](#github)

---

> **Jesús Temprano Gallego**  
> Curso: 2025/2026  
> 2º Curso CFGS Desarrollo de Aplicaciones Web  
> Despliegue de aplicaciones web

# Git

Sistema de control de versiones que permite guardar cambios y trabajar en proyectos de forma organizada. \
Facilita colaborar, crear ramas y volver a versiones anteriores sin perder historial. \
Se usa tanto en local como con plataformas como GitHub o GitLab para gestionar repositorios.

## Instalación

Lo descargamos de https://git-scm.com/install/

Al ejecutarlo, le damos a aceptar y siguiente hasta la parte de elegir el editor por defecto. Elegimos VSCode y le damos a siguiente.

Después nos preguntara si queremos cambiar el nombre de la rama principal por defecto. Marcamos la opción de si y pondremos `master` (porque es como tenemos que llamar las ramas de nuestros repositorios).

En la opción del PATH elegimos la de terminal y aplicaciones de terceros. \
En el SSH, SSL y finales de línea los dejamos por defecto. \
En la terminal le decimos que use la propia de Windows. \
Y el resto de opciones le damos a siguiente dejándolas como están hasta instalar.

Una vez instalado podemos abrir una terminal nueva y comprobar que esta instalado con `git --version`.

## Configuración

Para poder usarlo primero hay que configurar la cuenta poniendo estos comandos en la terminal:
```bash
git config --global user.name "nombre"
git config --global user.email "email@ejemplo.com"
```

## Buenas prácticas

1. Añadir un archivo `.gitignore` en la raíz del proyecto para no subir archivos y/o carpetas innecesarios o que no queremos.
2. Usar lenguaje imperativo en los commits. Los commits deben verse como "*instrucciones*" que cambian el proyecto mas que como cosas que se han hecho.
3. NO usar punto final. El mensaje corto del commit (la primera línea) es el encabezado/titulo del commit, y al igual que en el periódico o las noticias, los títulos no llevan punto final.
4. NI puntos suspensivos. Si vemos los commits como instrucciones, las instrucciones deben de ser claras y estar completas. No deben crear duda a quien lo lea después.
5. Usar como máximo unos 50 caracteres. Si tienes que explicar demasiado, tu commit probablemente hace demasiadas cosas. Si es posible dividirlo en varios commits; **hazlo**.
6. Si tienes que añadir alguna explicación necesaria se pondrá en el cuerpo del commit. En el se el puede explicar el qué y el por qué, no el cómo. Porque el mensaje puede mentir, pero el código no.
7. Usar prefijos para mejor legibilidad. Para eso, se usa esta estructura: `<tipo>(<scope>): <descripcion>`.
   - Es scope es opcional y sirve para indicar la parte del proyecto afectada (*por ejemplo un módulo, componente o funcionalidad específica*), pudiendo entender rápidamente dónde se aplicó el cambio.
   - Para el tipo de commit, los más comunes y usados son ***feat***, ***fix***, ***refactor*** y ***docs***, pera hay mas. Aquí unos ejemplos y usos:
     - **feat**: Añade una nueva característica.
     - **fix**: Arregla errores en el código.
     - **refactor**: Refactorización del código como cambios de nombre de variables o funciones.
     - **docs**: Cambios en la documentación.
     - **style**: Cambios de formato, tabulaciones, espacios, etc en el código; no afectan al funcionamiento.
     - **perf**: Cambios que mejoran el rendimiento del sitio.
     - **build**: Cambios en el sistema de construcción, tareas de despliegue o instalación.
     - **test**: Añade tests o refactoriza uno existente.
     - **ci**: Cambios en la integración continua.
   - Si el commit contiene **breaking changes** (*cambios que rompen la compatibilidad con las versiones anteriores. Ej: eliminar o renombrar funciones o clases, cambiar parámetros obligatorios, etc*), se pondrá un signo de exclamación `!` antes de los dos puntos. \
   Y en el cuerpo de commit se podría poner `BREAKING CHANGE:` y explicar exactamente que se ha eliminado o cambiado que rompe la compatibilidad.


## **Gestión de un repositorio (Terminal)**

### Iniciar / Clonar repo

Para iniciar un nuevo repositorio, por la terminal vamos a la carpeta donde lo queramos iniciar y ponemos `git init`.

Para clonar uno ya creado en GitHub, copiamos la url del repo y hacemos `git clone <url> <(opcional) directorio donde se guardara>`. Si no se pone directorio, se crea uno con el nombre que tiene el repo en GitHub. Si se pone uno, este tiene que estar vacío.

### Estado e historial

### Añadir y confirmar cambios

### Crear y cambiar de ramas

### Fusionar ramas (merge) y conflictos

### Conectar con remoto

### Subir y descargar cambios

### Deshacer cambios

### Etiquetas


## **Gestión de un repositorio (VSCode)**

### Iniciar / Clonar repo

Para iniciar un repositorio, abrimos la carpeta donde lo queramos iniciar y abrimos el menú de control de versiones con `Ctrl + G` y le damos a "**Inicializar Repositorio**".

Para clonar uno ya creado en GitHub, iniciamos uno y en el menú de control de versiones en el apartado "CHANGES" le damos a los 3 puntos y a clonar y ponemos la url del repositorio en GitHub.

### Estado e historial

### Añadir y confirmar cambios

### Crear y cambiar de ramas

### Fusionar ramas (merge) y conflictos

### Conectar con remoto

### Subir y descargar cambios

### Deshacer cambios

### Etiquetas


# GitHub

Plataforma online para almacenar y gestionar repositorios Git en la nube. \
Permite colaborar, revisar código, crear issues y pull requests entre varios desarrolladores. \
Incluye herramientas extra como automatización, documentación y gestión de tareas para mejorar el trabajo en equipo.
