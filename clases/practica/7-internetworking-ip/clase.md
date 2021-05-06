# Clase 7 - Internetworking

Traceroute: No permite saber la vuelta si viene por el mismo camino, pero si la
ida,

## Resumen

{copiar}

ICMP

## Direcciones IP especiales

- 255.255.255.255
- 127.0.0.1: Loopback, direccion de software. No esta montado a una placa de
  red, si quiero montar IP sobre un equipo que no tiene placa la puedo montar
  sobre eso.

  Si quiero hacer ping a mi mismo le puedo mandar a 127.0.0.1

## Direcciones IP privadas

No tienen que salir a internet para que no molesten. Por lo general tienen
filtros los routers. Se puede salir con privadas pero no vuelven las respuestas.

10.*
172.*
192.*

El router hace PAT, agarra toda la red privada y la saca con la misma publioca.
Con netstat se pueden ver los puertos y que hay muchas privadas internamente,
pero hacia afuera se ve una única pública.

Para la práctica 3 siempre hay que usar IPs públicas o privadas. Las privadas no
salen a internet.

## Problemas

/16 quiere decir que hay 16 1s en la mascara y 16 0s.

Cuando defino una red con su máscara implícitamente hablo de un rango, que está
correspondido con la máscara

la 40.40.0.0/16 va hasta 40.40.255.255, es una ip dentro de ese rango.

(no puedo usar para equipos ni la .0 ni la .255)

Posibilidades: 2^16.

Broadcast genera tráfico innecesario y no sirve. Si tengo un equipo choto, puede
levantar muchos broacast y perder utilidad.

## Problema con broadcast

Si es una red plana, los broadcast de un lado pueden hacer que se caiga un
enlace del otro.

{diapo 15}

Para solucionarlo, subredes IP. y poner un router en el medio y subnetear la red

## Subredes IP

Dividir una red grande en subredes mas chiquitas. Para el mundo exterior, la red
sigue siendo la misma.

Los broadcast no pasan porque las intrfaces del router dividen la red en
dominios de broadcast.

Concepto: tengo una red grande y lo parto en pedazos mas chicos.

No lo haria porque sale caro, no lo necesito, no me conviene.

## Mascaras no multiplos de 8

No todas son de 255 hosts, puedo tener mas.

## Mini redes

Se usan para punto a punto entre redes. Le tengo que poner IP a cada punta del
cable, y poniendo una /30 pongo dos máquinas con el menor desperdicio.

## Ejemplo de ruta por defecto

Ultimos dos bits en 1 para broadcast ip

## Ejercicios

Para no equivocarse, conviene arrancar por la más grande e ir a la más chica.
Arrancando de cualquier lado es más fácil equivocarse, pueden superponerse las
redes.

Se pueden usar privadas para los punto a punto pero dificulta el debugging (no
se puede hacer traceroute ni ping). Si quiero que todo me conteste uso publicas.
Si uso privadas para punto a punto, el router no puede contestar, porque tiene
que contestar por la misma interfaz por la que le llegó, y no puede porque es
privada.
