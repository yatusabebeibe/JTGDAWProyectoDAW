[< Volver atrás](README.md)

- [Git](#git)
  - [Instalación](#instalación)
  - [Configuración](#configuración)
  - [Buenas prácticas](#buenas-prácticas)
  - [**Gestión de un repositorio (Terminal)**](#gestión-de-un-repositorio-terminal)
    - [Iniciar / Clonar repo](#iniciar--clonar-repo)
    - [Clonar repo](#clonar-repo)
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
    - [Clonar repo](#clonar-repo-1)
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

## **Gestión de un repositorio (Terminal)**

### Iniciar / Clonar repo

### Clonar repo

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

### Clonar repo

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
