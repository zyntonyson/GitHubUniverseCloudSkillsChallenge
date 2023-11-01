
# Introducción a Git  [img](https://learn.microsoft.com/es-mx/training/modules/intro-to-git/)

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

# Ejercicio: Prueba de Git

Este módulo requiere un espacio aislado para completarse.

> **Nota:** Un espacio aislado le da acceso a recursos gratuitos. No se le cobrará en su suscripción personal. El espacio aislado solo podrá usarse para completar el aprendizaje en Microsoft Learn. El uso para cualquier otro motivo está prohibido y podría generar la pérdida permanente del acceso al espacio aislado.
> 
> Microsoft ofrece esta experiencia de laboratorio y el contenido relacionado con fines educativos. Toda la información presentada es propiedad de Microsoft y está destinada únicamente a brindar información sobre los productos y servicios abordados en este módulo de Microsoft Learn.

Para poder crear el primer repositorio, debe asegurarse de que Git está instalado y configurado. Git está preinstalado en Azure Cloud Shell, por lo que podemos usar Git en Cloud Shell, a la derecha.

## Configuración de Git

En Cloud Shell, para comprobar que Git está instalado, escriba `git --version`:

``` 
git --version
``` 

**Sugerencia:** Puede usar el botón `clipboard;` para copiar los comandos en el Portapapeles. Para pegarlos, haga clic con el botón derecho en una nueva línea en el terminal de Cloud Shell y seleccione Pegar, o bien use el método abreviado de teclado Mayús+Insert (`Cmd;+V en macOS).

Debería ver una salida similar a la de este ejemplo:

``` 
git version 2.7.4
``` 

Para configurar Git, debe definir algunas variables globales: `user.name` y `user.email`. Ambas son necesarias para realizar confirmaciones.

Establezca su nombre en Cloud Shell con el siguiente comando. Reemplace <USER_NAME> por el nombre de usuario que quiere usar.

``` 
git config --global user.name "<USER_NAME>"
``` 

Ahora, use este comando para crear una variable de configuración `user.email` para ello, reemplace <USER_EMAIL> por su dirección de correo electrónico:

``` 
git config --global user.email "<USER_EMAIL>"
``` 

Ejecute el siguiente comando para comprobar que los cambios han funcionado:

``` 
git config --list
``` 

Confirme que la salida incluye dos líneas similares al siguiente ejemplo. El nombre y la dirección de correo electrónico serán distintos a los que se muestran en el ejemplo.

``` 
user.name=User Name
user.email=user-name@contoso.com
``` 

## Configuración del repositorio de Git

Git funciona buscando cambios en los archivos dentro de una determinada carpeta. Vamos a crear una carpeta que actúe como árbol de trabajo (directorio del proyecto) y a permitir que Git sepa sobre ella para que pueda comenzar a seguir los cambios. Se indica a Git que empiece a realizar el seguimiento de los cambios mediante la inicialización de un repositorio de Git en esa carpeta.

Empiece por crear una carpeta con el nombre Cats. Esta carpeta va a ser el directorio del proyecto, también denominado árbol de trabajo. El directorio del proyecto es donde se almacenan todos los archivos relacionados con el proyecto. En este ejercicio, es donde se almacenan el sitio web y los archivos que crean el sitio web y su contenido.

``` 
mkdir Cats
``` 

Vaya al directorio del proyecto mediante el comando cd:

``` 
cd Cats
``` 

Ahora, inicialice el nuevo repositorio y establezca el nombre de la rama predeterminada en main:

Si está ejecutando la versión 2.28.0 o una posterior de Git, use el comando siguiente:

``` 
git init --initial-branch=main
``` 

O bien, use el siguiente comando:

``` 
git init -b main
``` 

En versiones anteriores de Git, use estos comandos:

``` 
git init
git checkout -b main
``` 

Después de ejecutar el comando de inicialización, debería ver una salida similar a la de este ejemplo:

``` 
Initialized empty Git repository in /home/<user>/Cats/.git/
Switched to a new branch 'main'
``` 

Ahora, use un comando `git status` para mostrar el estado del árbol de trabajo:

``` 
git status
``` 

Git responde con esta salida, que indica que master es la rama actual. (De hecho, también es la única rama). Por ahora todo está claro.

``` 
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
``` 

Use un comando `ls` para mostrar el estado del árbol de trabajo:

``` 
ls -a
``` 

Confirme que el directorio contiene un subdirectorio denominado .git. (El uso de la opción -a con `ls` es importante, ya que Linux normalmente oculta los nombres de archivos y directorios que comienzan con un punto). Esta carpeta es el repositorio de Git: el directorio en el que Git almacena los metadatos y el historial del árbol de trabajo.

Normalmente no se hace nada directamente con el directorio .git. Git actualiza los metadatos a medida que el estado del árbol de trabajo cambia para mantener un seguimiento de lo que ha cambiado en sus archivos. Este directorio es práctico para usted, pero es increíblemente importante para Git.

### Ayuda desde Git

Git, al igual que la mayoría de las herramientas de línea de comandos, tiene una función de ayuda integrada que se puede usar para buscar comandos y palabras clave.

Escriba el comando siguiente para obtener ayuda sobre lo que puede hacer con Git:

``` 
git --help
``` 

El comando muestra la salida siguiente:

``` 
usage: git [--version] [--help] [-C <path>] [-c name=value]
[--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
[-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
[--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
<command> [<args>]
...
``` 

Lea las distintas opciones disponibles con Git y observe que cada comando incluye su propia página de ayuda, para cuando empiece a profundizar más. No todos estos comandos tendrán sentido todavía, pero es posible que algunos le resulten familiares si tiene experiencia con un VCS.

En la lección siguiente, empezará a realizar cambios y a ver cómo Git los rastrea.

# Comandos básicos de Git

Git recuerda los cambios efectuados en los archivos como si tomara instantáneas del sistema de archivos.

## Introducción

Vamos a hablar de algunos comandos básicos para iniciar el seguimiento de los archivos del repositorio. Luego va a guardar la primera "instantánea" con la que Git va a comparar.

### git status

El primer comando de Git, y el que se usa con más frecuencia, es `git status`. Ya lo ha usado una vez en el ejercicio anterior para ver que había inicializado correctamente el repositorio de Git.

`git status` muestra el estado del árbol de trabajo (y del área de almacenamiento provisional, de la que pronto hablaremos más). Permite ver los cambios que Git está siguiendo en ese momento para poder decidir si quiere pedir a Git que tome otra instantánea.

### git add

`git add` es el comando que se usa para indicar a Git que empiece a realizar un seguimiento de los cambios en determinados archivos.

El término técnico es almacenamiento provisional de estos cambios. Va a usar `git add` para almacenar provisionalmente los cambios a fin de prepararse para una confirmación. Todos los cambios en los archivos que se han agregado pero que aún no se han confirmado se almacenan en el área de almacenamiento provisional.

### git commit

Después de haber almacenado provisionalmente algunos cambios para su confirmación, puede guardar el trabajo en una instantánea si invoca al comando `git commit`.

Confirmar (o "commit") es un verbo y un sustantivo. Básicamente tiene el mismo significado que cuando se confirma en un plan o se confirma un cambio en una base de datos. Como verbo, la confirmación de cambios significa que se coloca una copia (del archivo, el directorio u otra "cosa") en el repositorio como una nueva versión. Como sustantivo, una confirmación es el pequeño fragmento de datos que asigna una identidad única a los cambios que se confirman. Los datos que se guardan en una confirmación incluyen el nombre del autor y la dirección de correo electrónico, la fecha, los comentarios sobre lo que se ha hecho (y por qué), una firma digital opcional y el identificador único de la confirmación anterior.

### git log

El comando `git log` permite ver información sobre las confirmaciones anteriores. Cada confirmación tiene un mensaje adjunto (un mensaje de confirmación), y el comando `git log` permite imprimir información sobre las confirmaciones más recientes, como su marca de tiempo, el autor y un mensaje de confirmación. Este comando ayuda a realizar un seguimiento de lo que ha estado haciendo y de los cambios que se han guardado.

### git help

Ya ha probado el comando `git help`, pero vale la pena recordar ciertas cosas. Use este comando para obtener información fácilmente sobre todos los comandos que conoce hasta ahora y más.

Recuerde que cada comando incluye también su propia página de ayuda. Para encontrar estas páginas de ayuda, escriba `git <command> --help`. Por ejemplo, `git commit --help` muestra una página que proporciona más información sobre el comando `git commit` y cómo usarlo.


# Cuestionario sobre Control de Versiones

1. ¿Cuál de los siguientes escenarios es un caso de uso habitual de un sistema de control de versiones?

   - [ ] Eliminación de versiones anteriores de un proyecto o archivo para saber que se está trabajando solo con el archivo o los datos más recientes.
   - [x] Realización de cambios experimentales en el proyecto en una rama aislada.
   - [ ] Recopilación de requisitos de características de un proyecto grande y su comunicación a las partes interesadas.

2. ¿Cuál es otro nombre para un sistema de control de versiones?

   - [ ] Software de administración de versiones (VMS)
   - [x] Sistema de administración de control de software (SCM)
   - [ ] Sistema de administración de configuración de software (SCM)

3. ¿Cuál es la diferencia entre Git y GitHub?

   - [ ] Git permite trabajar con una o más ramas locales y enviar los cambios a un repositorio remoto. GitHub actúa como el repositorio remoto al que se accede por medio de un sitio web o herramientas de línea de comandos.
   - [ ] Git es un sistema de control de versiones distribuido (DVCS) que se ejecuta en la nube. GitHub es una capa de interfaz que proporciona acceso a la tecnología de Git.
   - [x] Git se usa por parte de un colaborador individual. GitHub se usa por parte de varios colaboradores para simplificar el trabajo de desarrollo en grupo.

4. ¿Qué comando de Git ofrece información sobre cómo usar Git?

   - [ ] git init
   - [ ] git status
   - [x] git help








