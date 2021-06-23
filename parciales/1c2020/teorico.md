# Parcial teorico de promocion

## Ejercicio 1

No es exactamente hacer la cuentita por todos los overheads que hay

Primero la cota minima

- Capa 2:
  - Colisiones por medio compartido (exponential backoff)
  - Retransmisiones dependiendo del tipo de sliding window
  - Cambios de topologia (recalcular STP)
- Capa 3:
  - Cambios de topologia (recalcular tablas de ruteo / forwarding con OSPF)
  - Posibles circuitos virtuales (si los usas, tenes el overhead de
    establecimiento de conexiones)
- Capa 4:
  - Retransmisiones
  - Reordenamientos
  - Establecimiento y cierre de la conexion (seguro es TCP porque es descarga de
    archivo)
  - Congestion de la red
- Capa de aplicación:
  - Andando lento el servidor
  - Que se caiga el servidor
  - DDoS

## Ejercicio 2

Algunos de los mecanismos que ayuda al control de congestión son Random Early
Detection (RED) y la estimación más precisa del timeout de retransmisión en TCP
(RTO) ¿Podría explicar como se modelan como sistemas de control de lazo cerrado?

