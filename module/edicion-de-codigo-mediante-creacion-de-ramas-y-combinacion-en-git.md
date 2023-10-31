# Introducción

**100 XP**
**5 minutos**

Imagine que es un nuevo desarrollador de software en una empresa que escribe software de aviónica para líneas aéreas comerciales. El control de calidad es crítico y los desarrolladores trabajan en equipos pequeños que usan Git para el control de versiones. Ya sabe algo sobre Git. Lo ha usado para realizar un seguimiento de los cambios, corregir errores y colaborar con otros desarrolladores a través de un repositorio compartido y solicitudes de incorporación de cambios. Sin embargo, sabe que Git todavía tiene mucho más que ofrecer, y eso le entusiasma.

Ya ha creado un pequeño sitio web que usted y sus amigos pueden usar para practicar con Git compartiendo fotografías de sus gatos. Ha reclutado a un par de amigos que son desarrolladores de software para que le ayuden.

A medida que progresa el proyecto, desea facilitar la colaboración con sus amigos, para poder trabajar en las características del sitio web sin conflictos ni esfuerzos en vano.

En este módulo, aprenderá qué ramas hay en Git, cómo usarlas para el desarrollo y cómo combinarlas, incluida la resolución de los conflictos de las combinaciones.

## Objetivos de aprendizaje
En este módulo, aprenderá a realizar las tareas siguientes:

* Trabajar con las ramas en Git
* Crear ramas y cambiar de una a otra
* Combinar ramas
* Más información sobre técnicas básicas para resolver conflictos de combinación

## Requisitos previos
Para trabajar en este módulo, debe tener conocimientos básicos de cómo trabajar con Git, entre los que se incluyen:

* Términos como repositorio, árbol de trabajo e índice
* Creación de repositorios
* Almacenamiento provisional y confirmación de cambios
* Restablecimiento y reversión de errores simples
* Clonación de repositorios
* Solicitudes de incorporación de cambios
* Guardado provisional de cambios
* Inserción de cambios y actualización del repositorio mediante extracción



# Ramas en Git
Es un desarrollador web que intenta aprender más cosas sobre Git por motivos laborales. Ha creado un sitio web HTML y CSS sencillo que presenta fotos de gatos para poner en práctica sus aptitudes de Git y ha trabajado en él con sus amigos, Alice y Bob.

A medida que el proyecto avanza, se da cuenta de que quiere que todos puedan trabajar en más de una tarea a la vez sin interponerse en la forma de trabajar de otra persona. Necesita mantener por separado el trabajo de todos para que el nuevo desarrollo no interfiera con las correcciones de errores existentes. En Git, las ramas facilitan este tipo de colaboración.

El trabajo que se hace en una rama no se tiene que compartir, y tampoco interfiere con el trabajo realizado en otras ramas. Las ramas le permiten mantener las confirmaciones relacionadas con cada tema juntas y aisladas de otro trabajo, por lo que los cambios realizados en un tema son fáciles de revisar y supervisar.

El desarrollo de software moderno se realiza casi por completo en ramas. El objetivo es mantener limpia la rama principal hasta que el trabajo esté listo para su inserción en el repositorio. Después, inserte los cambios en la rama principal, o mejor aún, envíe una solicitud de incorporación de cambios para fusionar los cambios.

Una ventaja de Git con respecto a los sistemas de control de versiones (VCS) anteriores es que, con Git, la creación de una rama es muy rápida; equivale a escribir un hash de 40 caracteres en un archivo en `.git/heads.` La conmutación de ramas también es rápida, ya que Git almacena archivos completos y los descomprime en lugar de intentar reconstruirlos a partir de listas de cambios. La combinación en Git no es tan simple, pero es sencilla y a menudo totalmente automática.

Veamos qué son las ramas, cómo se usan y cómo funcionan.

## Estructura y nomenclatura de las ramas
Una rama es simplemente una cadena de confirmaciones que se ramifica a partir de la línea principal de desarrollo, como una rama de un árbol.

Si va a cambiar a Git desde otro VCS, es posible que esté acostumbrado a una terminología algo distinta. La subversión del VCS nombra su rama predeterminada como trunk, mientras que Git la denomina master. Puede cambiar el nombre de la rama predeterminada de la misma forma que puede hacerlo con cualquier otra rama. En este módulo, la rama predeterminada se denomina main.

Normalmente, una rama comienza con una confirmación en la rama predeterminada; en este caso, en main. A medida que se agregan confirmaciones, la rama desarrolla una cadena de historial independiente. Finalmente, los cambios de la rama se vuelven a combinar en main. En este módulo, aprenderá a realizar confirmaciones en una rama y a combinarlas en la rama main.

Supongamos que crea una rama a partir de la rama `main`. Aquí se muestra cómo visualizar lo que sucede:


![Diagrama que muestra la relación de la rama principal con las ramas locales.
](https://learn.microsoft.com/es-mx/training/modules/branch-merge-git/media/branch-tree.png)



Cada letra mayúscula del diagrama representa una confirmación. Las ramas reciben nombres tales como `add-authentication` y `fix-css-bug`  , y pueden tener sus propias ramas. El objetivo final es dejar que los desarrolladores hagan lo que tienen que hacer sin interferir unos con otros y terminar con una rama principal que represente los mejores esfuerzos de todos los implicados.

## Creación y modificación de ramas (rama de Git y desprotección de Git)

Una razón común para crear una rama es realizar cambios en una característica existente. Una rama con este fin se denominaría habitualmente rama puntual o rama de características.

Puede crear una rama con el comando `git branch`. Cambie entre las ramas con el comando `git checkout`.

Ha identificado `checkout` como una forma de reemplazar archivos en el árbol de trabajo obteniéndolos del índice. Sin rutas de acceso en la lista de argumentos, checkout actualiza todo lo que hay en el árbol de trabajo y el índice para que coincida con la confirmación especificada (en este caso, el encabezado de la rama).

## Combinación de ramas (combinación de Git)
Una vez que haya finalizado algún trabajo en una rama, quizá una característica o una corrección de errores, querrá combinar la rama de nuevo con la rama principal. Puede usar el comando git merge para combinar una rama específica con la rama actual.

Por ejemplo, si estuviera trabajando en una rama llamada my-feature, el flujo de trabajo sería similar al del siguiente ejemplo:


```
# Switch back to the main branch
git checkout main

# Merge my-feature branch into main
git merge my-feature

```
Después de usar estos comandos y resolver los conflictos de combinación (los describiremos más adelante en este módulo), todos los cambios de la rama my-feature se encontrarían en main.


# Ejercicio: Creación de una rama como Alice

**Este módulo requiere un espacio aislado para completarse. Usó 3 de 10 espacios aislados por hoy. Mañana habrá disponibles más espacios aislados.**


Su amiga desarrolladora Alice desea agregar algunos estilos CSS para dar estilo a las fotos de gatos del sitio web. Alice desea realizar este trabajo en su propia rama.

## Configurar
Para que podamos asumir el rol de Alice, debe hacer algo de trabajo para configurar un repositorio vacío que todos compartan y, después, agregar algunos archivos.

Git ya se ha instalado automáticamente en Azure Cloud Shell, por lo que podemos usar Git en Cloud Shell, a la derecha.

### Creación de un repositorio vacío compartido
Cree un directorio denominado Shared.git para que contenga el repositorio vacío:

```
mkdir Shared.git
cd Shared.git
```

Ahora, ejecute el comando siguiente para crear un repositorio vacío en el directorio compartido:

```
git init --bare

```
Establezca el nombre de la rama predeterminada del nuevo repositorio. Para realizar este paso, puede cambiar la rama HEAD para que apunte a otra rama; en este caso, la rama main:


```
git symbolic-ref HEAD refs/heads/main

```

### Clonación del repositorio compartido para Bob
Suba un nivel a partir de este directorio y cree un directorio para que Bob almacene su repositorio:

```
cd ..
mkdir Bob
```
Clone y configure el repositorio de Bob:

```
cd Bob
git clone ../Shared.git .
git config user.name Bob
git config user.email bob@contoso.com
git symbolic-ref HEAD refs/heads/main
```
 
> Nota
>
> Como quiere empezar con la rama predeterminada de main, debe cambiar HEAD para que apunte a refs/heads/main en lugar de refs/heads/master, que es el nombre de la rama predeterminada.

## Incorporación de archivos base
Como paso final de configuración, se agregarán los archivos de sitio web base y se insertarán en el repositorio compartido. En el caso de estos comandos, todavía estamos trabajando en el directorio Bob.

Cree algunos archivos mediante el comando touch de Linux, agréguelos al "stage" y confírmelos mediante Git:


```
touch index.html
mkdir Assets
touch Assets/site.css
git add .
git commit -m "Create empty index.html and site.css files"
```
Ahora agregue HTML al archivo con el editor de código de Cloud Shell. Puede abrir el editor mediante la ejecución del comando code. Abra index.html en el editor en línea; para ello, introduzca code index.html en el símbolo del sistema del terminal:

```
code index.html

```
Pegue este código HTML:

```
HTML

Copiar
<!DOCTYPE html>
<html>
  <head>
    <meta charset='UTF-8'>
    <title>Our Feline Friends</title>
    <link rel="stylesheet" href="CSS/site.css">
  </head>
  <body>
    <nav><a href="./index.html">home</a></nav>
    <h1>Our Feline Friends</h1>
    <p>Eventually we will put cat pictures here.</p>
    <footer><hr>Copyright (c) 2021 Contoso Cats</footer>
  </body>
</html>
```
Guarde el archivo y cierre el editor. Puede seleccionar los puntos suspensivos "…" de la esquina derecha del editor o usar el método abreviado de teclado (CTRL+S en Windows y Linux, o bien Cmd+S en macOS).

Cambie al directorio Assets (Recursos) y abra site.css en el editor:

```
cd Assets
code site.css
```
Agregue el siguiente CSS al archivo:

```
Copiar
h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
body { font-family: serif; background-color: #F0FFF8; }
nav, footer { background-color: #C0D8DF; }

```
Guarde el archivo y cierre el editor.

Vuelva al directorio Bob y confirme de nuevo:

```
cd ..
git add .
git commit -m "Add simple HTML and stylesheet"
git push --set-upstream origin main
```

 >Nota
>
>Como se va a usar otro nombre de rama predeterminado, debe indicarle a Git que asocie la rama principal a la rama principal del repositorio de origen.

Compruebe los resultados. Si ve una advertencia similar a la de este ejemplo, no se preocupe. Esta advertencia simplemente informa a los usuarios de un cambio en los comportamientos predeterminados de Git.


```
warning: push.default is unset; its implicit value has changed in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the traditional behavior, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, run:

  git config --global push.default simple

When push.default is set to 'matching', git will push local branches
to the remote branches that already exist with the same name.

Since Git 2.0, Git defaults to the more conservative 'simple'
behavior, which only pushes the current branch to the corresponding
remote branch that 'git pull' uses to update the current branch.

See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)
```

Si quiere asegurarse de que no vuelve a ver esta advertencia, puede ejecutar este comando:

```

git config --global push.default simple

```
Compruebe la salida de este indicador de éxito:


```

Counting objects: 9, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (9/9), 953 bytes | 953.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0)
To ../Shared.git
 * [new branch]      main -> main
```

## Creación de una rama para Alice
Alice quiere crear una rama puntual denominada add-style para realizar su trabajo. Vamos a asumir el rol de Alice y, después, crearemos la rama y agregaremos código a esta rama.

Suba un nivel a partir de este directorio y cree un directorio para la copia del repositorio de Alice:

```
cd ..
mkdir Alice
```

Clone el repositorio de Alice y, a continuación, configúrelo:


```
cd Alice
git clone ../Shared.git .
git config user.name Alice
git config user.email alice@contoso.com
```

Ahora tiene una copia actual del repositorio. Puede enumerar el contenido del archivo y ejecutar git status para confirmar el estado del repositorio.

```
ls
git status
```

Ejecute el comando  `git branch` para crear una rama denominada add-style. Luego, ejecute el comando git checkout para cambiar a esa rama (de este modo, la convierte en la rama actual).

```
git branch add-style
git checkout add-style
```

En el directorio `Alice/Assets` (Alice/Recursos), abra site.css. Agregue la siguiente definición de clase CSS al final del archivo:

```
.cat { max-width: 40%; padding: 5 }
Guarde los cambios en el archivo y cierre el editor.
```

Confirme el cambio:

```
git commit -a -m "Add style for cat pictures"
```

En este momento, Alice quiere poner su estilo a disposición de todos los demás, para que cambien a main de nuevo y realicen una incorporación de cambios por si alguna otra persona ha realizado cambios:

```
git checkout main
git pull
```

La salida indica que la rama main está actualizada (es decir, main del equipo de Alice coincide con main en el repositorio compartido). Por tanto, Alice combina la rama `add-style`  con la rama main mediante la ejecución del comando `git merge --ff-only`  para realizar una combinación de avance rápido. Luego, Alice inserta la main de su repositorio en el compartido.

```
git merge --ff-only add-style
git push
```

En este caso, la combinación de avance rápido no era estrictamente necesaria porque la rama main no tenía ningún cambio y Git habría combinado los cambios de todos modos. Sin embargo, usar la marca  `--ff only`  es una buena práctica porque se produce un error en una combinación de  `--ff-onlysi` main ha cambiado.






