[< Volver atrás](README.md)

- [Git](#git)
  - [Instalación](#instalación)
  - [Configuración](#configuración)
  - [Buenas prácticas](#buenas-prácticas)
  - [**Gestión de un repositorio (Terminal)**](#gestión-de-un-repositorio-terminal)
    - [1. Iniciar / Clonar repo](#1-iniciar--clonar-repo)
    - [2. Estado e historial](#2-estado-e-historial)
    - [3. Añadir y confirmar cambios (commit)](#3-añadir-y-confirmar-cambios-commit)
    - [4. Crear y cambiar de ramas](#4-crear-y-cambiar-de-ramas)
    - [5. Fusionar ramas (merge) y conflictos](#5-fusionar-ramas-merge-y-conflictos)
    - [6. Conectar con remoto](#6-conectar-con-remoto)
    - [7. Subir y descargar cambios](#7-subir-y-descargar-cambios)
    - [8. Deshacer cambios](#8-deshacer-cambios)
    - [9. Etiquetas](#9-etiquetas)
  - [**Gestión de un repositorio (VSCode)**](#gestión-de-un-repositorio-vscode)
    - [1. Iniciar / Clonar repo](#1-iniciar--clonar-repo-1)
    - [2. Estado e historial](#2-estado-e-historial-1)
    - [3. Añadir y confirmar cambios (commit)](#3-añadir-y-confirmar-cambios-commit-1)
    - [4. Crear y cambiar de ramas](#4-crear-y-cambiar-de-ramas-1)
    - [5. Fusionar ramas (merge) y conflictos](#5-fusionar-ramas-merge-y-conflictos-1)
    - [6. Conectar con remoto](#6-conectar-con-remoto-1)
    - [7. Subir y descargar cambios](#7-subir-y-descargar-cambios-1)
    - [8. Deshacer cambios](#8-deshacer-cambios-1)
    - [9. Etiquetas](#9-etiquetas-1)
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
6. Si tienes que añadir alguna explicación necesaria se pondrá en el cuerpo del commit. En el se el puede explicar el qué y el por qué, no el cómo. Porque el mensaje puede mentir, pero el código no. Se debe dejar una línea en blanco entre el titulo y el cuerpo.
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

### 1. Iniciar / Clonar repo

Para iniciar un nuevo repositorio, por la terminal vamos a la carpeta donde lo queramos iniciar y ponemos `git init`.

Para clonar uno ya creado en GitHub, copiamos la url del repo y hacemos `git clone <url> <(opcional) directorio donde se guardara>`. Si no se pone directorio, se crea uno con el nombre que tiene el repo en GitHub. Si se pone uno, este tiene que estar vacío.

### 2. Estado e historial

Para ver el estado actual del repo usamos `git status`, que nos indica qué archivos están modificados, cuáles no se han añadido al área de staging y cuáles están listos para hacer commit.

Para ver el historial de commits usamos `git log`. Esto nos muestra los commits hechos en el repo, con su hash, autor, fecha y mensaje. Se pueden añadir opciones como `--oneline` para ver solo una línea por commit o `--graph` para ver un esquema más gráfico de las ramas. Recomiendo usar ambos para una mejor legibilidad.

Para ver los cambios en los archivos usamos `git diff`. Esto muestra línea por línea qué se ha añadido o eliminado desde el último commit pero que no han sido añadido al área de staging. Para ver los cambios del área de staging usamos la opción `--staged`.

### 3. Añadir y confirmar cambios (commit)

Para añadir los cambios al área de staging usamos `git add <archivo>` para un archivo concreto, o `git add .` para todos los cambios del directorio actual.

Para quitar los cambios del área de staging pero mantenerlos modificados usamos `git reset <archivo o '.'>`, y para deshacer los cambios hechos y volver al archivo como estaba en el ultimo commit usamos `git restore <archivo o '.'>`.

Para hacer un commit, usamos `git commit -m "mensaje"` (*el mensaje siguiendo las [buenas practicas](#buenas-prácticas)*). \
Si quisiéramos añadir un cuerpo al mensaje, haríamos `git commit` sin escribir un mensaje y nos aparecería un editor de texto para escribir el mensaje. Para poder escribir le tenemos que pulsar `i`. La primera línea, seria el titulo, las demás serian el cuerpo. Una vez escrito el mensaje y cuerpo, le pulsamos la tecla `Esc` después escribimos `:wq` y le damos a `intro` para confirmar el mensaje y terminar el commit.

### 4. Crear y cambiar de ramas

Para crear una nueva rama usamos `git branch <nombre_rama>`. Esto solo crea la rama, no cambia a ella automáticamente.

Para cambiar a otra rama usamos `git checkout <nombre_rama>`. También se puede crear y cambiar a la rama en un solo paso con `git checkout -b <nombre_rama>`.

Para ver todas las ramas del repositorio usamos `git branch`, la rama actual aparecerá con un *.

Para eliminar una rama usamos `git branch -d <nombre_rama>` (*solo se borrará si todos sus cambios ya están incluidos en otra rama*) o `git branch -D <nombre_rama>` (*se borra aunque tenga cambios no integrados*).

### 5. Fusionar ramas (merge) y conflictos

Para fusionar otra rama en la rama actual usamos `git merge <rama_a_fusionar>`. La rama en la que estamos **recibe** los cambios de la rama que indicamos.

Si Git puede combinar los cambios automáticamente, el merge se hace solo y solo mueve el puntero de la rama. \
Si queremos asegurar que cree un commit de merge en todo caso, tenemos que usar `git merge --no-ff <rama_a_fusionar> -m "mensaje"`. Para añadir un cuerpo al mensaje lo haríamos sin el `-m "mensaje"` y seria lo mismo que con los commit.

Si hay cambios que no se pueden combinar, se genera un conflicto. Los archivos en conflicto aparecen modificados y marcados para resolver.

Para resolver los conflictos:
1. Vemos qué archivos están en conflicto usando `git status`.
2. Abrimos los archivos y buscamos las marcas `<<<<<<<`, `=======` y `>>>>>>>`.
3. Elegimos qué cambios conservar editando el archivo a como lo queramos dejar y eliminamos las marcas.
4. Guardamos los archivos y añadimos los cambios con `git add <archivo o '.'>`.
5. Terminamos el merge con `git commit -m "mensaje"` o `git commit` si Git no lo hace automáticamente.

### 6. Conectar con remoto

Para enlazar el repositorio local con uno remoto usamos `git remote add <nombre_remoto> <url_del_repo>` (*nombre_remoto el 99% de las veces es "**origin**". Es un **casi** un estándar*). 
Esto crea la conexión entre tu repo local y el repo de GitHub (o cualquier otro servicio).

Para eliminar un remoto usamos `git remote remove <nombre_remoto>`, que borra la conexión con ese repositorio remoto.

Para comprobar qué remotos están configurados usamos `git remote -v`, que muestra las URLs asociadas al remoto.

### 7. Subir y descargar cambios

Para subir los cambios al remoto usamos `git push <rama>`.

Para descargar los cambios del remoto usamos `git pull`, que trae los cambios de la rama remota correspondiente y los fusiona con la rama en la que estamos.

Si solo queremos descargar los cambios sin fusionarlos todavía, usamos `git fetch`, que trae los commits nuevos del remoto y actualiza su información si no hay conflictos, sin modificar nuestros archivos ni nuestra rama actual.

Podemos usar la opción `--force`. Al usarla en el `push` sobrescribimos el remoto con nuestra versión local; en `pull` forzamos que lo local se reemplace por lo del remoto; y en `fetch` forzamos que Git actualice lo que sabe del remoto aunque sobrescriba la información que había anteriormente.

### 8. Deshacer cambios

Si queremos deshacer un commit ya hecho pero aún no se ha subido al remoto, usamos `git reset --soft <commit>` para mantener los cambios en los archivos, o `git reset --hard <commit>` para borrar también los cambios en los archivos y volver al estado del commit indicado.

Si el commit ya se ha subido al remoto, podemos hacer los mismos pasos que si no se hubiera subido y luego forzar el push con `git push --force` para sobrescribir el remoto con nuestra versión corregida. Esto puede afectar a otros que ya hayan descargado esos commits, por lo que se debe usar con cuidado.

### 9. Etiquetas

Para crear una etiqueta usamos `git tag <nombre_etiqueta>`. Esto marca un commit concreto sin añadir información extra.

Para crear una etiqueta con mensaje usamos `git tag -a <nombre_etiqueta> -m "mensaje"`. Esto marca un commit y guarda información adicional.

Para ver todas las etiquetas del repositorio usamos `git tag`.

Para subir una etiqueta al remoto usamos `git push origin <nombre_etiqueta>`. Para subir todas las etiquetas existentes usamos `git push origin --tags`.

Para borrar una etiqueta local usamos `git tag -d <nombre_etiqueta>`. Para borrarla del remoto usamos `git push origin --delete <nombre_etiqueta>`.


## **Gestión de un repositorio (VSCode)**

### 1. Iniciar / Clonar repo

Para iniciar un repositorio, abrimos la carpeta donde lo queramos iniciar y abrimos el menú de control de versiones con `Ctrl + G` y le damos a "**Inicializar Repositorio**".

Para clonar uno ya creado en GitHub, iniciamos uno y en el menú de control de versiones en el apartado **CAMBIOS** le damos a los 3 puntos y a clonar y ponemos la url del repositorio en GitHub.

### 2. Estado e historial

En el menú de control de versiones, en el apartado de **CAMBIOS** podemos ver los archivos que se han modificado, y de esos, cuales están en el área de staging y listos para hacer commit. \
Para ver los cambios a un archivo podemos simplemente hacer click en los archivos del apartado de **CAMBIOS** y nos mostrara que se ha añadido o eliminado desde el ultimo commit.

En el menú de control de versiones, en el apartado de **GRAPH** podemos ver el historial de commits con el titulo del commit y su autor, y si pasamos el cursor por encima de uno, podemos ver mas información, como la fecha y hora, hash del commit, líneas añadidas y eliminadas y cuerpo del mensaje del commit.

### 3. Añadir y confirmar cambios (commit)

En el menú de control de versiones, en el apartado de **CAMBIOS**, en los archivos que están en la sección de **Cambios**, podemos darle al símbolo de '+' y añadirá todos sus cambios a la sección de staged; o podemos hacer click en el archivo y seleccionar bloque por bloque que queremos añadir.

Para deshacer cambios, seria lo mimo que lo anterior pero en vez de darle al '+' se le daría a la flecha hacia atrás.

Para hacer un commit, el el apartado de **CAMBIOS**, ponemos el mensaje (*siguiendo las [buenas practicas](#buenas-prácticas)*) y le damos a ***Confirmación***. \
Si quisiéramos añadir un cuerpo al mensaje, simplemente pondríamos `Crtl + Intro` para escribir mas líneas y le damos a ***Confirmación***.

### 4. Crear y cambiar de ramas

Para crear una rama, abajo a la izquierda en la barra de estado, le clicamos el nombre de nuestra rama actual. Seleccionamos **Crear nueva rama...** y le ponemos el nombre que queramos.

Para cambiar entre ramas, en el mismo sitio vamos y seleccionamos la rama que queramos usar.

Para eliminar una rama, en el menú de control de versiones, en el apartado de **CAMBIOS** le damos a los tres puntos, seleccionamos `Rama > Borrar rama...` y borramos la que queramos (si queremos borrar en la que estamos actualmente, primero tenemos que cambiar a otra rama).

### 5. Fusionar ramas (merge) y conflictos

Para fusionar otra rama en la rama actual, en el menú de control de versiones, en el apartado de **CAMBIOS** le damos a los tres puntos, seleccionamos `Rama > Combinar`. La rama en la que estamos **recibe** los cambios de la rama que indicamos.

Si Git puede combinar los cambios automáticamente, el merge se hace solo y simplemente mueve el puntero de la rama. \
Si queremos asegurar que cree un commit de merge en todo caso, *vscode no tiene una forma propia de hacer esto*. Pero podríamos hacerlo con la extension [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph).

En el apartado de **CAMBIOS** al lado de los tres puntos seleccionamos el icono del grafo (el de las líneas y puntos) y se abrirá una pestaña con el historial de commits. \
Hacemos doble click en la rama en la que queramos recibir los cambios y después click derecho la rama de la cual traemos los cambios y seleccionamos `Merge into current branch...`.\
Marcamos "*Create a new commit even if fast-forward is possible*" para hacer que cree un nuevo commit, y "*No Commit*" para hacer que no envíe el commit directamente para poder cambiar el mensaje en el menú de la barra lateral.

Si hay cambios que no se pueden combinar, se genera un conflicto. Los archivos en conflicto aparecen modificados, marcados para resolver y en una sección nueva en el menú en el apartado de **CAMBIOS** llamada "*Fusionar cambios mediante combinación*".

Para solucionarlo, clicamos en el archivo en esa nueva sección y nos llevara a donde esta el conflicto. \
Nos aparecerán varias opciones. Podemos elegir entre conservar el actual, el entrante o ambos. Seleccionamos el que nos convenga y una vez seleccionado, si aceptamos ambos, podemos editar el archivo manualmente para poder solucionar cualquier error que git no pueda detectar.

Una vez terminado y que no haya mas conflictos, añadimos el archivo al stage, escribimos el commit de merge y le damos a ***Confirmación***.

### 6. Conectar con remoto

Para conectar con remoto, en el menú de control de versiones, en el apartado de **CAMBIOS** le damos a los tres puntos, seleccionamos `Remoto > Agregar remoto...`, ponemos la url del remoto y de nombre le damos `origin`.

Para eliminar el remoto, en el mismo sitio pero dándole a `Quitar remoto`.

Puedes ver los remotos que hay, en el apartado de **CAMBIOS** le damos a los tres puntos, seleccionamos `Pull, Push > Insertar en...` y nos mostrara una lista con los que tenemos.

### 7. Subir y descargar cambios

Para subir los cambios al remoto, en el menú de control de versiones le damos a los tres puntos y seleccionamos `Pull, Push > Insertar`. Esto enviará los commits de la rama actual al remoto correspondiente.

Para descargar los cambios del remoto, usamos `Pull, Push > Incorporar cambios`, que trae los cambios de la rama remota correspondiente y los combina automáticamente con la rama actual.

Podemos hacer un pull y push a la vez con `Pull, Push > Sincronizar`.

Si solo queremos traer los cambios sin fusionarlos todavía, usamos `Pull, Push > Fetch`, que actualiza la información del remoto y descarga los commits nuevos, pero no modifica nuestros archivos hasta que hagamos un merge manual.

### 8. Deshacer cambios

Si has hecho un commit en local o si además también lo has subido a remoto y lo quieres deshacer, desde la interfaz de vscode no es posible.

Si necesitas hacerlo solo se podría [hacer por terminal](#8-deshacer-cambios).

### 9. Etiquetas

Para crear una etiqueta, en el menú de control de versiones, en el apartado de **CAMBIOS** le damos a los tres puntos, seleccionamos `Etiquetas > Crear etiqueta...`, le ponemos un nombre y nos aparecerá para poner un mensaje. Si no queremos poner mensaje, pulsamos intro sin poner nada.

Para subir todas las etiquetas al remoto pulsamos `F1` y escribimos `push etiquetas` y le damos al intro.

Para borrar una etiqueta local vamos a `Etiquetas > Eliminar etiqueta...`. Y para borrarlas del remoto `Etiquetas > Eliminar etiqueta remota...`.

Para ver todas las etiquetas del repositorio, en el menú de control de versiones, en el apartado de **GRAPH** podemos ver el historial de commits donde también aparecen los tags que hay.

---

# GitHub

Plataforma online para almacenar y gestionar repositorios Git en la nube. \
Permite colaborar, revisar código, crear issues y pull requests entre varios desarrolladores. \
Incluye herramientas extra como automatización, documentación y gestión de tareas para mejorar el trabajo en equipo.
