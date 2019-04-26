# Taller2_AlgoritmosdeProgramacion_2019A

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


