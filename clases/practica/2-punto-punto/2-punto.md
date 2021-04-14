# Clase 2 - Punto a punto

Estamos parados en la data link layer. Los protocolos de los que vamos a hablar
son punto a punto, entre dos nodos o dos computadoras o una compu y un router.
Pero no van mas alla de eso.

## Conceptos

- Caño serial No hay desorden

  > si puedo numerar los bits llegan con el mismo orden. Nada lo altera salvo
  > el ruido.

- Sujeto a ruido: lo que se recibe puede nop ser lo que se envio (errores de
  transmision)

## Objetivos

- Framing: encapsular los bits en frames agregando info de control. Como los
  codifico o decodifico?

  {foto frame p4}

- Proveer servicio a la capa superior: confiable o no confiable?
- Control de errores: se produjo un error? que hacemo?
- COntrol de flujo: Se ve en transporte

## Ej 1

{p5}

a. Habla de la capacidad de volumen

  velocidad = 1Mbps

## Encapsulamiento: Framing

Como se separan los frames en un tren de bits consecutivos?

- Largo fijo

  > Yo ya se como receptor cuantos bits son un frame, y se como interpretar la
  > info que me llega.

- Largo en el header
- Delimitadores con bit-stuffing

  Un flag que indica que arranca o termina. Si aparece en los datos cague.

  Por eso se usa bit-stuffing, se *escapea*.

  Cuando uno tiene caracteres especiales, uno usa una combinacion de caracteres
  para indicar que esa letra va con tilde.

La **eficicencia del frame** esta dada por largo de datos / largo del frame

## Control de errores

Estan en la bib

- Bit de paridad
- CRC: Requieren una cantidad de espacio en el frame

  Bien explicado en el peterson. Se trata de polinomios

- Checksum: Parto en palabras y sumo, de un lado y del otro me tiene que dar lo
  mismo. Si no da lo mismo es porque hay un error.

- Hamming
- Reed-Solomon
- MD5

Retransmisiones

- Explicitas: Mensajes de control especificos para pedir datos nuevamente

  > Volveme a mandar el pixel 73 porque llego mal

- Implicitas: Cuando ocurre un timeout, se asume que el dato se perdio. Entonces
  se envia devuelta.

## Tipos de servicio

- Sin conexion y sin reconocimiento: Los datos se envian sin necesidad de saber
  si llegan bien
- Sin conexion y con reconocimiento
- Orientado a conexion

  Inicia una conversacion con otro nodo, y la mantiene hasta que se transmiten
  todos los datos.

## Transmision confiable

- Stop & wait: envio uno y espero un ack hasta enviar el siguiente frame.
- SWS: Sliding window
- RWS
  - GoBackN: Si no llego alguno, descarta los siguientes
  - Sack: Bufferea los que le fueron llegando y espera al reenvio del que fallo

## Ej

a. stop & wait

  Necesito secuenciar 2 frames, entonces me alcanza con 1 bit.

  CRC y el espacio para los datos

  El ack solo necesita 1 bit y el CRC. Pueden ser dos frames distintos

b. a

  > piggybacking es que puedo en el ack enviar datos, o enviar ack en los datos
  > que envio de respuesta. Cuando la comunicacion es simetrica, y despues de
  > recibir un frame voy a enviar un dato de respuesta, puedo aprovechar y ahi
  > mandar el ack. Tengo datos para ambos lados.

c. sliding window con ack selectivo

  emisor:

  - No alcanza con un bit, sino alguna cantidad de bits.
  - Datos
  - CRC\checksum

  frame receptor (respuesta /ack):

  - CRC
  - s ack
  - ack

En go back n tengo que 