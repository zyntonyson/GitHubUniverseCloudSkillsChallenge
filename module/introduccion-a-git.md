
# Introducción a Git

Descubra en qué consiste el control de código fuente y obtenga una introducción a Git, el sistema de control de versiones más popular del mundo.

Objetivos de aprendizaje
Objetivos de este módulo:

* Más información sobre el control de versiones
* Descripción de los sistemas de control de versiones distribuidos, como Git
* Creación de un nuevo proyecto de Git y su configuración
* Realización y seguimiento de cambios en el código mediante Git
* Uso de Git para recuperarse de errores simples


# Introducción

**Completado:** 100 XP  
**Tiempo estimado:** 3 minutos

Imagine que es un nuevo desarrollador de software en una empresa que escribe software de aviónica para líneas aéreas comerciales. El control de calidad es crítico y los desarrolladores trabajan en equipos pequeños que usan Git para el control de versiones. Ha oído hablar del control de versiones, pero nunca ha usado Git, por lo que tiene muchas ganas de ponerse al día.

Decide compilar un sitio web que le permita compartir fotografías de sus gatos con sus amigos y, así, aprender a usar Git en un entorno divertido antes de aplicar esos conocimientos a su trabajo. Se propone compilar el sitio con Git para efectuar el seguimiento de los cambios y mantener copias de seguridad de todos los archivos de código fuente en caso de que el servidor deje de funcionar. Pero antes de entrar primero en Git, debe cubrir los conceptos básicos.

En este módulo, se ofrece una introducción al control de versiones y a Git. Git puede parecer un poco críptico al principio, incluso a veces frustrante, pero si lo conoce paso a paso, verá que hay una razón por la que se está convirtiendo rápidamente en el sistema de control de versiones más popular del mundo, no solo entre los desarrolladores de software, sino también entre los equipos que escriben documentación y colaboran en otras tareas.

## Objetivos de aprendizaje

Objetivos de este módulo:

- Más información sobre el control de versiones
- Descripción de los sistemas de control de versiones distribuidos, como Git
- Comprensión de las diferencias entre Git y GitHub y los roles que desempeñan en el ciclo de vida de desarrollo de software

## Prerrequisitos

Ninguno.


# ¿Qué es el control de versiones?

**Completado:** 100 XP  
**Tiempo estimado:** 5 minutos

Un sistema de control de versiones (VCS) es un programa o conjunto de programas que realiza un seguimiento de los cambios en una colección de archivos. Uno de los objetivos de un VCS es recuperar fácilmente versiones anteriores de archivos individuales o de todo el proyecto. Otro objetivo es permitir que varios miembros de un equipo trabajen en un proyecto, incluso en los mismos archivos, al mismo tiempo sin que eso afecte al trabajo de los demás.

Otro nombre para un VCS es un sistema de administración de configuración de software (SCM). Los dos términos suelen usarse indistintamente; de hecho, la documentación oficial de Git se encuentra en [git-scm.com](https://git-scm.com/). Técnicamente, el control de versiones es solo uno de los procedimientos que implica el SCM. Un VCS se puede usar para otros proyectos además de los de software, incluidos libros y tutoriales en línea.

Con un VCS, puede:

- Ver todos los cambios realizados en el proyecto, cuándo se hicieron los cambios y quién los efectuó.
- Incluir un mensaje con cada cambio para explicar los motivos.
- Recuperar versiones anteriores del proyecto completo o de archivos individuales.
- Crear ramas, donde los cambios se pueden hacer experimentalmente. Esta característica permite que se trabaje en varios conjuntos de cambios diferentes (por ejemplo, características o correcciones de errores) al mismo tiempo, posiblemente personas distintas, sin que ello afecte a la rama principal. Más adelante se pueden combinar los cambios que se quieren mantener en la rama principal.
- Adjuntar una etiqueta a una versión, por ejemplo, para marcar una nueva versión.

Git es un VCS de código abierto rápido, versátil, muy escalable y gratuito. Su autor principal es Linus Torvalds, creador de Linux.

## Control de versiones distribuido

Las instancias anteriores de los VCS, como CVS, Subversion (SVN) y Perforce, usaban un servidor centralizado para almacenar el historial de un proyecto. Esta centralización significaba que un solo servidor también era un único punto de error en potencia.

Git es un sistema distribuido, lo que significa que el historial completo de un proyecto se almacena en el cliente y en el servidor. Se pueden editar archivos sin conexión de red, protegerlos localmente y sincronizarlos con el servidor cuando una conexión esté disponible. Si un servidor deja de funcionar, todavía tendrá una copia local del proyecto. Técnicamente, ni siquiera es necesario tener un servidor. Los cambios pueden pasarse por correo electrónico o compartirse mediante medios extraíbles, pero, en la práctica, nadie usa Git así.

## Terminología de Git

Para entender Git, debe comprender la terminología. Esta es una breve lista de los términos que los usuarios de Git emplean con frecuencia. De momento no se preocupe por los detalles; todos estos términos le irán resultando familiares a medida que avanza por los ejercicios de este módulo.

- **Árbol de trabajo**: conjunto de directorios y archivos anidados que contienen el proyecto en el que se trabaja.
- **Repositorio (repo)**: directorio, situado en el nivel superior de un árbol de trabajo, donde Git mantiene todo el historial y los metadatos de un proyecto. A veces se hace referencia a los repositorios como repos. Un repositorio vacío es aquel que no forma parte de un árbol de trabajo; se usa para compartir o realizar copias de seguridad. Un repositorio vacío suele ser un directorio con un nombre que acaba en `.git`, por ejemplo, `project.git`.
- **Hash**: número generado por una función hash que representa el contenido de un archivo u otro objeto como un número de dígitos fijo. Git usa hashes de 160 bits de longitud. Una ventaja de usar códigos hash es que Git puede indicar si un archivo ha cambiado aplicando un algoritmo hash a su contenido y comparando el resultado con el hash anterior. Si se cambia la marca de fecha y hora del archivo, pero el hash del archivo no, Git sabe que el contenido del archivo no se ha modificado.
- **Objeto**: un repositorio de Git contiene cuatro tipos de objetos, cada uno identificado de forma única por un hash SHA-1. Un objeto `blob` contiene un archivo normal. Un objeto `árbol` representa un directorio, y contiene nombres, valores hash y permisos. Un objeto de `confirmación` representa una versión específica del árbol de trabajo. Una `etiqueta` es un nombre asociado a una confirmación.
- **Confirmación**: cuando se usa como verbo, confirmar significa crear un objeto de confirmación. Esta acción toma su nombre de las confirmaciones en una base de datos. Significa que los cambios se han probado y están listos para ser incluidos en el historial de un proyecto.
- **Rama**: versión del proyecto que diverge del tronco principal. Una rama es un apuntador a una confirmación específica. Las ramas permiten desarrollar características o arreglos de manera aislada, para después fusionarlos con la rama principal.
- **Clonar**: hacer una copia local de un repositorio.
- **Fusión**: combinar dos versiones de un proyecto.
- **Tirar (pull)**: recuperar cambios de un repositorio remoto.
- **Empujar (push)**: enviar cambios a un repositorio remoto.
- **Conflicto de fusión**: sucede cuando Git no puede fusionar automáticamente los cambios porque dos ramas han cambiado el mismo fragmento de código de diferentes maneras.

## Ejercicio: Hello World en Git

Durante el transcurso de este módulo, usted creará su propio repositorio Git, aprenderá a hacer cambios en él y a trabajar con repositorios en GitHub. ¡Vamos a empezar!

