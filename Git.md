[< Volver atrás](README.md)

- [Git](#git)
  - [Instalación](#instalación)
  - [Configuración](#configuración)
  - [Buenas prácticas](#buenas-prácticas)
  - [**Gestión de un repositorio (Terminal)**](#gestión-de-un-repositorio-terminal)
    - [Iniciar / Clonar repo](#iniciar--clonar-repo)
    - [Estado e historial](#estado-e-historial)
    - [Añadir y confirmar cambios (commit)](#añadir-y-confirmar-cambios-commit)
    - [Crear y cambiar de ramas](#crear-y-cambiar-de-ramas)
    - [Fusionar ramas (merge) y conflictos](#fusionar-ramas-merge-y-conflictos)
    - [Conectar con remoto](#conectar-con-remoto)
    - [Subir y descargar cambios](#subir-y-descargar-cambios)
    - [Deshacer cambios](#deshacer-cambios)
    - [Etiquetas](#etiquetas)
  - [**Gestión de un repositorio (VSCode)**](#gestión-de-un-repositorio-vscode)
    - [Iniciar / Clonar repo](#iniciar--clonar-repo-1)
    - [Estado e historial](#estado-e-historial-1)
    - [Añadir y confirmar cambios (commit)](#añadir-y-confirmar-cambios-commit-1)
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

Nosotros usaremos el estándar de [Commits Convencionales](https://www.conventionalcommits.org/es/v1.0.0/), que sigue todas estas reglas.

## **Gestión de un repositorio (Terminal)**

### Iniciar / Clonar repo

Para iniciar un nuevo repositorio, por la terminal vamos a la carpeta donde lo queramos iniciar y ponemos `git init`.

Para clonar uno ya creado en GitHub, copiamos la url del repo y hacemos `git clone <url> <(opcional) directorio donde se guardara>`. Si no se pone directorio, se crea uno con el nombre que tiene el repo en GitHub. Si se pone uno, este tiene que estar vacío.

### Estado e historial

Para ver el estado actual del repo usamos `git status`, que nos indica qué archivos están modificados, cuáles no se han añadido al área de staging y cuáles están listos para hacer commit.

Para ver el historial de commits usamos `git log`. Esto nos muestra los commits hechos en el repo, con su hash, autor, fecha y mensaje. Se pueden añadir opciones como `--oneline` para ver solo una línea por commit o `--graph` para ver un esquema más gráfico de las ramas. Recomiendo usar ambos para una mejor legibilidad.

Para ver los cambios en los archivos usamos `git diff`. Esto muestra línea por línea qué se ha añadido o eliminado desde el último commit pero que no han sido añadido al área de staging. Para ver los cambios del área de staging usamos la opción `--staged`.

### Añadir y confirmar cambios (commit)

Para añadir los cambios al área de staging usamos `git add <archivo>` para un archivo concreto, o `git add .` para todos los cambios del directorio actual.

Para quitar los cambios del área de staging pero mantenerlos modificados usamos `git reset <archivo o '.'>`, y para deshacer los cambios hechos y volver al archivo como estaba en el ultimo commit usamos `git restore <archivo o '.'>`.

Para hacer un commit, usamos `git commit -m "mensaje"` (*el mensaje siguiendo las [buenas practicas](#buenas-prácticas)*). \
Si quisiéramos añadir un cuerpo al mensaje, haríamos `git commit` sin escribir un mensaje y nos aparecería un editor de texto para escribir el mensaje. Para poder escribir le tenemos que pulsar `i`. La primera línea, seria el titulo, las demás serian el cuerpo. Una vez escrito el mensaje y cuerpo, le pulsamos la tecla `Esc` después escribimos `:wq` y le damos a `intro` para confirmar el mensaje y terminar el commit.

### Crear y cambiar de ramas

### Fusionar ramas (merge) y conflictos

### Conectar con remoto

### Subir y descargar cambios

### Deshacer cambios

### Etiquetas


## **Gestión de un repositorio (VSCode)**

### Iniciar / Clonar repo

Para iniciar un repositorio, abrimos la carpeta donde lo queramos iniciar y abrimos el menú de control de versiones con `Ctrl + G` y le damos a "**Inicializar Repositorio**".

Para clonar uno ya creado en GitHub, iniciamos uno y en el menú de control de versiones en el apartado **CAMBIOS** le damos a los 3 puntos y a clonar y ponemos la url del repositorio en GitHub.

### Estado e historial

En el menú de control de versiones, en el apartado de **CAMBIOS** podemos ver los archivos que se han modificado, y de esos, cuales están en el área de staging y listos para hacer commit. \
Para ver los cambios a un archivo podemos simplemente hacer click en los archivos del apartado de **CAMBIOS** y nos mostrara que se ha añadido o eliminado desde el ultimo commit.

En el menú de control de versiones, en el apartado de **GRAPH** podemos ver el historial de commits con el titulo del commit y su autor, y si pasamos el cursor por encima de uno, podemos ver mas información, como la fecha y hora, hash del commit, líneas añadidas y eliminadas y cuerpo del mensaje del commit.

### Añadir y confirmar cambios (commit)

En el menú de control de versiones, en el apartado de **CAMBIOS**, en los archivos que están en la sección de **Cambios**, podemos darle al símbolo de '+' y añadirá todos sus cambios a la sección de staged; o podemos hacer click en el archivo y seleccionar bloque por bloque que queremos añadir.

Para deshacer cambios, seria lo mimo que lo anterior pero en vez de darle al '+' se le daría a la flecha hacia atrás.

Para hacer un commit, el el apartado de **CAMBIOS**, ponemos el mensaje (*siguiendo las [buenas practicas](#buenas-prácticas)*) y le damos a ***Confirmación***. \
Si quisiéramos añadir un cuerpo al mensaje, le damos a ***Confirmación*** sin escribir un mensaje y nos aparecería un editor de texto para escribir el mensaje. La primera línea, seria el titulo, las demás serian el cuerpo. Una vez escrito el mensaje y cuerpo, en la barra superior (donde aparecen los archivos) a la derecha le damos a el tic de verificación para confirmar el mensaje y terminar el commit.

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
