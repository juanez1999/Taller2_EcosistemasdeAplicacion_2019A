# Taller2_EcosistemasdeAplicacion_2019A

## Analisis tecnico Eclipse

### Clase Main

En esta clase sucede todo lo relacionado con la ejecución de la aplicación, los metodos que se encuentran en la logica son llamados aquí para ser ejecutados por los metodos bases como el draw y el setup, se inicializa también la variable de PApplet app para utilizarla al realizar parte gráfica.

#### Variables:

* PApplet app // Esta variable se utiliza para realizar la parte gráfica al implementar el core de proccesing.
* Logica log // Esta variable global se utiliza para llamar los metodos definidos en la clase Logica y llamarlos a los metodos definidos en el main.

#### Metodos:

* void main(String[] // Este metodo se utiliza para llamar el package con el que voy a trabajar e incluir el core de proccesing.
* void settings() // Este metodo se utiliza para dar el tamaño al lienzo de la aplicación.
* void setup() // Este motodo se utiliza para inicializar las variables globales, para luego poder utilizarlas, como en el caso de la logica, para utilizar la refencia en los demás metodos.
* void draw() // Este metodo se utiliza para realizar todo el trabajo de pintado que se ha definido en la logica.


### Clase logica

Esta clase contiene todos los metodos para que se ejecuten en el Main y así se ejecute la aplicación de manera adecuada. Es la clase donde contiene lo logico de la aplicación.

#### Variables:
* PApplet app // Esta variable la utilizo para hacer uso del PApplet y así utilizar sus metodos en la logica.
* Comunicacion ref // Esta variable es para llamar los metodos de la clase Comunicacion que se ncargaran de crear y manejar la comunicacion de la conexion entre eclipse y android y eclipse y arduino.
* PImage fondo // Variable para crear un fondo para la aplicacion de eclipse.
* boolean correcto // Variable para validar cuando haya conexion se habilite el metodo de enviar datos de la clase comunicacion

#### Metodos:

* Logica (PApplet app) // Este metodo servira para inicializar todas las variables y así mismo, hacer uso de ellas.
* void pintar() // En este metodo realizara todo lo referente al pintar de la aplicacion, traere los metodos de pintar de la clase Elemento para que todo se piense en el lienzo de la aplicación.
* void enviar() // Metodo encargado de realizar el envio de datos tanto a la aplicacion de Android y Arduino
* void Run() // Metodo que se encarga de realizar el proceso de la logica en su propio hilo.
* void validarEntradas() // Metodo encargado de validar los datos que recibe para procesarlos y luego utilizarlos en el metodo enviar.

### Clase Comunicacion

Esta clase será la encargada de realizar toda la parte de comunicacion de las conexiones entre los dispositivos que hacen parte del ecosistema, al crear la comunicacion es posible recibir y enviar datos entre los dispositivos.

#### Variables:

* MulticastSocket ms // Crea una variable de tipo Multicast encargada del envio simultaneo de paquetes que seran recibidos por un grupo de receptores determinados.
* InetAddress grupo // Define el grupo al cual los receptores se podran conectar para el envio y la recepcion de paquetes de datos.
* DatagramPacket enviar // Un paquete de datos de tipo Datagram que es el encargado de ser enviado por el grupo.
* DatagramPacket recibir // Variable encargada de recibir y contener los paquetes de datos de tipo Datagram que llegan a el para luego ser interpretados.
* String msj // Variable para guardar los paquetes que llegan y convertirlos a string para interpretarlos y hacer operaciones logicas con el mensaje recibido.
* boolean vivo // Variable para mantener el hilo de la clase activo.

#### Metodos:

* Comunicacion() // Constructor del metodo donde seran inicializadas las variables.
* void Recibir() // Metodo encargado de validar los datagramPackets que recibe e interpretarlos.
* void Enviar() // Metodo encargado del envio de datagramPackets.
* void Run() // Hilo que ejectura los metodos cada vez durante su ejecucion.

## Analisis tecnico Android

### Activity SplashInicio

Esta activity contendra el splash de inicio de la aplicacion donde se le dará la bienvenida al usuario y si es nuevo se le explicara de que consiste la aplicacion, se le permitara registrarse para guardar sus alarmas como favoritas.

#### Variables:
* Imageview logo // Encargado de pintar la imagen correspondiente al logo.
* TextView saludo // Encargado de escribir el saludo al usuario.
* EditText usuario // Campo de texto donde el usuario ingresara su nombre para luego visualizarlo en la siguiente activity al momento de colocar la alarma.
* ImageButton iniciar // Boton para cambiar de activity.
* boolean alive // Variable encargada de mantener con vida al hilo.
* MulticastSocket msocket // Variable para enviar y recibir paquetes de datos simultaneamente.
* InetAdress grupo // Variable para uniser al grupo donde sera receptor de los paquetes de datos de eclipse.

#### Metodos:
* void onCreate(Bundle) // Metodo constructor de la clase encargado de inicializar las variables.
* void recibir() // Metodo encargado de recibir los datos que son enviados desde eclipse hasta esta activity.
* void Run() // Metodo encargado de inicializar el metodo de Recibir para que constantemente este al pendiente de pedir los paquetes de datos.

### Activity MainActivity

Clase encargada de crear la interfaz y manejar la logica de la aplicacion de alarma. Además de mandar la señal a eclipse para que luego valide con el arduino y luego tambien se convierta en receptor para cambiar dependiendo lo recibido la interfaz para el usuario.

#### Variables:
* MulticastSocket msocket // Variable para enviar y recibir paquetes de datos simultaneamente.
* InetAdress grupo // Variable para uniser al grupo donde sera receptor de los paquetes de datos de eclipse.
* ImageView fondo // Variable para pintar el background de la aplicacion en una imagen.
* ImageView icono // Para pintar los iconos referentes a la interfaz.
* Imagebutton onoff // Para cambiar el estado de la alarma a encendido o apagado.
* DatagramPacket recibido // Variable encargada de recibir los paquetes de datagrama por parte de eclipse.
* DatagramPacket enviado // Variable encargada de mandar paquetes de datos hacia eclipse dependiendo de lo sucedido en la logica de la actividad, segun sea el caso.
* boolean alive // Variable encargada de mantener con vida al hilo.
* String msg // Para convertir los paquetes en string e interpretar la logica segun la informacion que contenga el string.

#### Metodos:
* void onCreate(Bundle) // Metodo constructor de la clase encargado de inicializar las variables.
* void accion(String dat) // Metodo encargado de interpretar los mensajes recibidos y segun sea el tipo de mensaje se toma un accion en la logica de la actividad.
* void Run() // Hilo que ejectura los metodos cada vez durante su ejecucion.
* void enviar(String id) // Recibe una tipo String que sera el que se envia a eclipse para su posterior interpretacion.
* void recibir() // Metodo encargado de recibir los datos de parte de eclipse e interpretarlos.
* void sonar() // Metodo encargado de crear la vibracion y el sonido de la alarma segun la interpretacion de los paquetes de datos.
