#Emacs Discreto

Una introducción discreta al editor de texto GNU Emacs 24.

<br>
###Introducción

<br>
Emacs es un poderoso editor de texto extensible liberado bajo la licencia GNU/GPL. Al ser un proyecto de código abierto se encuentra disponible para varias plataformas incluyendo GNU/Linux, Mac y Windows. Esta guía pretende introducir al lector en el uso de (GNU) Emacs, partiendo desde simples movimientos de teclado hasta autocompletado y autocorrección. Emacs es una herramienta muy compleja que requiere mucho tiempo de aprendizaje. El lector puede encontrar útil clonar este repositorio y así conservarlo para futura referencia.

<br>
###Notación

<br>
En Emacs, las funcionalidades se realizan a través de comandos. Para ingresar comandos debemos primero aprender a leer la notación.

<br>
 * `M-` Indica que debe mantenerse apretada la tecla *Meta*. Esta tecla corresponde a la tecla `[Alt]` en sistemas GNU/Linux y `[Command]` en sistemas Mac.
 * `C-` Indica que debe mantenerse apretada la tecla `[Control]`.

<br>
Por ejemplo, `M-x` consiste en presionar y mantener la tecla *Meta* y luego escribir *x*. Al hacer esto, veremos el texto *M-x* en el mini buffer (ese rectángulo ubicado al fondo). Añadiendo *load-theme* y luego `[Enter]` se ejecutará el comando para modificar el tema visual. Ingresando *wombat* y luego `[Enter]` Emacs modificará el tema visual por defecto. A partir de ahora, haremos referencia a esa secuencia de comandos con la combinación:

<br>
`M-x load-theme` `[Enter]` *wombat* `[Enter]`

<br>
La combinación utilizada es la forma estándar para la ejecución de comandos por nombre. Emacs asocia por defecto varios atajos de teclado a comandos utilizados regularmente.
Esta guía introducirá la mayoría de los comandos a través de gráficos para hacer más ameno el aprendizaje, pero hará uso de la notación recién vista cuando haga falta. Si cometemos un error (o creemos haberlo cometido) debemos tener en cuenta estos 2 atajos:

 * `C-g`: Ejecuta *keyboard-quit*, lo que cancela el comando que estamos por introducir.
 * `C-_`: Ejecuta *undo*, es decir, deshacer. Notar que debemos mantener presionado tanto `[Control]` como `[Shift]`.

<br>
###Archivos

<br>
Para abrir un archivo ejecutamos la combinación `C-x C-f`. El comando *find-file* nos pregunta la ruta del archivo a cargar. En caso de no existir se creará uno nuevo. El buffer activo mostrará los contenidos del archivo cargado. La siguiente imagen muestra otras combinaciones relacionadas a archivos.

<br>
![Archivos](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQSENHTkEwSWF3Z1k)

<br>
El grafo de nodos muestra un nodo grande de color verde que denominaremos *origen*. Cada camino desde el origen a cualquiera de los otros nodos conectados con flechas representa una combinación de teclas (es decir, un comando reconocible por Emacs). Cuando hayamos terminado de editar un archivo podemos cerrar la aplicación haciendo `C-x C-c`. En el caso de que haya cambios sin guardar Emacs nos consultará si deseamos guardarlos.

<br>
###Cursor: Parte 1

<br>
Saber moverse en un archivo resulta esencial. Emacs nos ofrece varios atajos que iremos viendo por partes.

<br>
![Cursor](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQRzE0WGJxUWZ2TE0)

<br>
###Edición: Parte 1

<br>
Los atajos para editar archivos no son los que comúnmente se usan en otras aplicaciones similares (de todas maneras, Emacs presenta un método de activar atajos tradicionales). Emacs ofrece varios atajos que introduciremos en 2 partes. El primer comando importante a recordar es *set-mark-command*. Este comando se ejecuta haciendo `C-[Espacio]`. Esta combinación inicializa la selección de texto. Para seleccionar un área de texto basta con ejecutar este comando y luego moverse con los atajos de cursor vistos previamente. Una vez tengamos el texto deseado dentro de la selección podemos utilizar alguna combinación como `C-w` o `M-w` para cortar/copiar.

<br>
![Edición](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQZ1BUV0JqMFlOalk)

<br>
Para conocer el alcance de una selección podemos utilizar `C-x C-x`. Este atajos sirve para intercambiar la posición del cursor con la del origen de la selección.

<br>
###Ventanas

<br>
Las ventanas ejecutando instancias de Emacs se denominan *frames*. Cuando abrimos Emacs veremos un *frame* conteniendo una *barra de menú*, una *barra de herramientas* y un *buffer* mostrando un mensaje de bienvenida. Bajo el *buffer* también tenemos una *linea de modo* (o *mode line*) y el *mini buffer*. Los *frames* a su vez contienen ventanas (o *windows*). Las ventanas contienen la combinación *buffer*, *linea de modo* y *mini buffer*. Saber utilizar más de una ventana resulta muy útil a la hora de editar más de un archivo.

<br>
![Ventanas](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQQUlpMThBY0RIZ1E)

<br>
Es normal terminar teniendo varias ventanas y buffers abiertos. El siguiente grupo de atajos resultan efectivos para manejar estas circunstancias:

<br>
![Ventanas](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQbUp2MVZaOGRsWGc)

<br>
Otros atajos útiles:

<br>
 * `M-x kill-some-buffers`: Permite eliminar varios buffers.
 * `C-x [Flecha Izq]` o `C-x [Flecha Der]` permite moverse entre buffers. `[Control]` + clic izquierdo provee otro atajo similar.
 * `M-x delete-windows-on` `[Enter]` *buffer* `[Enter]`: Cierra ventanas mostrando un determinado buffer.
 * `C-x 4 r`: Abre un archivo en otra ventana en modo *Solo Lectura*.

<br>
###Ayuda y documentación

<br>
Emacs incluye distintos mecanismos de ayuda a través de los siguientes atajos:

<br>
![Ayuda](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQenh4cmcwMi1QOGs)

<br>
###Mode line

<br>
La *mode line* muestra información relevante al buffer que estamos editando, como la línea donde nos encontramos o si hay cambios no guardados. También muestra el *modo principal* utilizado. La misma puede verse de la siguiente manera:

<br>
`U:**-  pruebas.txt      35% L70    (Fundamental)`

<br>
La letra `U` ubicada al principio identifica el contenido del buffer con el set de caracteres `Unix UTF-8`. El carácter `:` actúa simplemente como separador. Los 2 caracteres siguientes identifican el contenido del buffer con respecto al archivo. Estos son los valores posibles:

<br>
 * `--`: No hay cambios entre lo mostrado por el buffer y los contenidos del archivo.
 * `**`: Existen cambios que no han sido guardados todavía.

<br>
En caso de que el buffer sea de solo lectura, el primer carácter será `%` y el siguiente será el correspondiente al estado (`-` o `*`).
El carácter `-` que sigue se usa como separador. A continuación debería de mostrarse el nombre del *frame*, pero este no se mostrará si estamos en modo gráfico (lo que será más probable).
El valor siguiente muestra el nombre del buffer, por lo general será el nombre del archivo abierto a menos que se trate de un buffer especial.
Los 2 valores siguientes muestran la ubicación con respecto al archivo: Si estamos al principio del buffer mostrará *Top*, si estamos al final *Bot* (por *Bottom*). Puede también que se muestre un porcentaje indicando la cantidad de texto por arriba del cursor, o también, que diga *All* si el contenido del buffer entra en una sola pantalla. El valor siguiente simplemente muestra la línea en la que estamos ubicados.
Por último, se muestra el modo principal (o *major mode*) utilizado en este buffer. Este modo puede ser activado a mano o puede activarse automáticamente si Emacs asocia la extensión de un archivo a un determinado modo.

<br>
###Configuración

<br>
Emacs al ser una pieza de software extremadamente configurable posee una rica variedad de opciones. Existen 2 mecanismos para almacenar configuraciones:

<br>
 * Un archivo `~/emacs` con la configuración personal de Emacs
 * Una carpeta `~/emacs.d` que almacena las extensiones

<br>
Cuando ejecutamos Emacs por primera vez no tendremos opciones almacenadas. Para crear el archivo de configuración es necesario realizar un cambio en las opciones de programa y luego elegir la opción *Save Options* del menú *Options*. Por ejemplo, podríamos ocultar la *Toolbar* por defecto para ganar más espacio en pantalla. Para eso basta hacer *Options* -> *Show/Hide* -> *Toolbar* -> *None* y luego *Options* -> *Save Options*. Si todo salió bien se debería mostrar un mensaje en el mini buffer confirmando que el archivo de configuración fue actualizado. Haciendo `M-x customize` accederemos a las opciones de customización de Emacs. Desde ahí podemos modificar gran parte de las características de Emacs sin acudir al archivo de configuración.

<br>
###Cursor: Parte 2

<br>
![Cursor](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQZjQzRVZueTdsRnM)

<br>
###Edición: Parte 2

<br>
![Edición](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQbVdIZUpLOGphTlk)

<br>
###Frames

<br>
Los *frames* corresponden a las ventanas corriendo instancias de Emacs. También existen atajos dirigidos a su uso.

<br>
![Frames](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQZWtHSExOZW1TSEk)

<br>
###Búsqueda

<br>
Emacs permite varios métodos de búsqueda. La búsqueda de cadenas se realiza desde la posición actual del cursor hacia adelante, por lo que será recomendable utilizar el atajo para enviar el cursor al principio del buffer en el caso de que fuera necesario (`M-<`). El método más sencillo de búsqueda se realiza haciendo:

<br>
`C-s` `[Enter]` *cadena* `[Enter]`

<br>
Esto realizará la búsqueda de *cadena* en el buffer actual. El método alternativo es llamado búsqueda incremental, donde ingresamos `C-s` y comenzamos a escribir la cadena inmediatamente después. El siguiente gráfico extiende este metodología en detalle:

<br>
![Búsqueda](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQeWJYS1FKdmt5ZEU)

<br>
El *kill ring* representa al portapapeles de Emacs. El mismo se comporta como un buffer circular que puede albergar varias cadenas al mismo tiempo.

<br>
#####Reemplazar cadenas

<br>
El comando *replace-string* realiza un reemplazo de cadena sencillo. El listado de comandos es:

<br>
`M-x replace-string` `[Enter]` *cadena* `[Enter]` *reemplazo* `[Enter]`

<br>
Esto reemplaza ocurrencias de *cadena* por *reemplazo* en el buffer seleccionado. Un método más interesante es el *query-replace*, donde el editor nos consulta antes de realizar cada reemplazo. La serie de comandos es la siguiente:

<br>
`M-%` *cadena* `[Enter]` *reemplazo* `[Enter]`

<br>
Este comando recorrerá el buffer en busca de *cadena*. Por cada ocurrencia hallada nos permitirá decidir si reemplazar la cadena o realizar otra acción. El siguiente gráfico muestra las opciones disponibles:

<br>
![Replace](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQa19GWnkzYThndnM)

<br>
En algunas situaciones es deseable editar algo mientras se realiza un *query-replace*. Si al estar en este modo hacemos `C-r` podemos realizar una edición recursiva. En este sub-modo podemos editar nuevamente el texto, y al terminar podemos volver al modo anterior haciendo `C-M-c`. Para cancelar la búsqueda estando en modo edición recursiva haremos `C-]`.

<br>
#####Expresiones regulares

<br>
Emacs también soporta la búsqueda por expresiones regulares. Las expresiones soportadas son:

<br>
 * `^`: Comienzo de línea.
 * `$`: Final de línea.
 * `.`: Cualquier carácter.
 * `*`: Controla que el carácter previo este presente 0 o más veces.
 * `\<`: Comienzo de palabra.
 * `\>`: Final de palabra.
 * `\s`: Coincide con cualquier carácter de espacio.
 * `\S`: Coincide con cualquier carácter que no sea espacio.
 * `\d`: Coincide con dígitos (0-9).
 * `\D`: Coincide con cualquier carácter que no sea un dígito.
 * `\w`: Coincide con letras y dígitos.
 * `\W`: Coincide con caracteres distintos de letras y dígitos.
 * `[]`: Permite ingresar varios caracteres entre llaves para coincidir con distintos caracteres.

<br>
Al utilizar expresiones regulares contamos con las mismas características que la búsqueda tradicional, un atajo para realizar la búsqueda incremental (`C-M-s`) y otro para realizar reemplazo de cadenas (`C-M-%`). El comportamiento de estos modos es esencialmente el mismo a los vistos para la búsqueda normal.

<br>
###Corrector ortográfico

<br>
Emacs incorpora un corrector ortográfico que puede ser aplicado a un buffer, un área seleccionada o a una palabra. Para aplicar el corrector al contenido de un buffer haremos:

<br>
`M-x ispell`

<br>
Este comando activa el modo *ispell*, el cual nos permite controlar que palabras no son reconocidas por el corrector y aplicar una corrección donde fuera necesario. En este modo, por cada palabra incorrecta se mostrará una ventana superior con posibles correcciones. Bajo este modo tenemos el siguiente comportamiento:

<br>
![Corrector](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQWUctblZYOHg0ams)

<br>
Al hacer `C-r` podemos editar el documento. Luego haciendo `C-u M-$` podemos recuperar la sesión de corrección previa. Haciendo `R` ingresamos al modo de reemplazo, este modo permite reemplazar una coincidencia en todo el documento. Estando en este modo podemos hacer `q` para volver al modo previo. Para aplicar el corrector ortográfico a una palabra situar el cursor sobre la misma y hacer `M-$`. Este atajo también se puede aplicar a una región seleccionada.

<br>
###Bookmarks

<br>
Los *boorkmarks* ofrecen la posibilidad de crear atajos en un documento para poder acceder a distintas partes del mismo más eficientemente. Emacs almacena los *bookmarks* creados en el archivo *~/.emacs.d/bookmarks*.

<br>
![Bookmarks](http://drive.google.com/uc?export=view&id=0B3PWnBYHw7RQb1hrbUZLbEROclU)

<br>
Si agregamos un *bookmark* con el mismo nombre que uno ya creado Emacs simplemente moverá la posición del mismo. Las opciones de *bookmarks* se encuentran en la sección *Edit* -> *Bookmarks* del menú. Emacs también soporta crear anotaciones para un determinado *bookmark*. En el listado de *bookmarks* seleccionamos un elemento y presionamos `e`. Para salir de este modo haremos `C-c C-c`.

<br>
###Modos útiles

<br>
#####cua-mode

<br>
Asocia los atajos tradicionales (`C-c`, `C-x`, `C-v`, `C-z`) a las acciones de copiar, cortar, pegar y deshacer: `M-x cua-mode`.

<br>
#####ido-mode

<br>
Activa auto-completado de rutas de archivo y nombres de buffer para ciertos comandos: `M-x ido-mode`.

<br>
#####evil-mode

<br>
Es un modo dirigido a usuarios habituales de Vim para mayor comodidad: `M-x evil-mode`.

<br>
#####flyspell-mode

<br>
Activa el modo de auto-corrección. Flyspell chequeará las palabras a medida que las tecleamos: `M-x flyspell-mode`.

<br>
###Más Emacs

<br>
Emacs posee más funcionalidades que las exhibidas en este tutorial. Algunos temas no se cubrieron extensivamente para no saturar y desalentar al lector. Aparte de los temas vistos podríamos mencionar características como la integración con *Bash*, la creación de *Macros* o el modo *Dired*. Estas se dejan como curiosidad, pudiendo ser visitadas más adelante. A continuación se listan algunos enlaces de interés en caso de que el lector desee explorar más acerca de Emacs.

<br>
 * [.Emacs](https://www.youtube.com/watch?v=MRYzPWnk2mE) - Serie de vídeos introductorios para Emacs.
 * [Emacs Tutorial](https://www.youtube.com/watch?v=ujODL7MD04Q) - Otro tutorial introductorio para Emacs.
 * [Emacs Mini Manual](http://tuhdo.github.io/emacs-tutor.html) - Una guía más avanzada con ejemplos y animaciones (orientados a programadores C/C++).
 * [Org tutorial](http://orgmode.org/worg/org-tutorials/orgtutorial_dto.html) - Un tutorial de *org-mode*, el organizador de Emacs.
 * [Emacs Prelude](https://github.com/bbatsov/prelude) - Emacs Prelude, la distribución Emacs recargada.
 * [Spacemacs](https://github.com/syl20bnr/spacemacs) - Spacemacs, un Emacs integrado con evil-mode.
 
<br>
Tanto *Emacs Prelude* como *Spacemacs* son proyectos muy robustos e interesantes. Se alienta al lector a probar estas extensiones una vez se haya familiarizado con el modo de trabajo en Emacs.
