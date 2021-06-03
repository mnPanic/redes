# Port scanning

nmap www.dc.uba.ar

Mandan paquets con SYN a ver si reciben SYN+ACK. Intenta de establecer una
conexion TCP. Hay otras formas de darse cuenta.

closed: cerrado explicitamente, no es que mande un SYN y me quede esperando,
sino que es un cerrado explícito.

nmap -A -T4 www.df.uba.ar

va mas allá del syn+ack, manda mas cosas