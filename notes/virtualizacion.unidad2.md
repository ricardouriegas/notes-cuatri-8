---
id: 8wjne7qwoujiodkk7t2tq3r
title: Unidad2 - Maquinas Virtuales
desc: ''
updated: 1739820209801
created: 1736361282650
---
## Virtualizacion de recursos
- Permite dividir los recursos de hardware de un sistema - como procesadores, memoria y almacenamiento, entre varios sistemas virtuales, denominados maquinas virtuales (VM).
- Entre los componentes que podemos compartir son los siguiente;
  - Kernel
  - S.O
  - CPY
  - Memoria
  - Almacenamiento
  - Dispositivos de Entrada/Salida
  - Red
  - Terminal de Sistema
- Kernel: El kernel del sistema operativo **anfitrion** coordina el acceso a los recursos fisicos. En maquinas virtuales, el **hipervisor** crea un entorno en el que cada maquina virtual tiene su propio kernel virtual.
- S.O: Comparte los recursos fisicos del hardware con otros sistemas operativos invitados
- CPU: Divide la potencia de procesamiento en multiples CPUs virutales. El hipervisor asigna tiempos e procesamiento a cada maquina virtual.
- Red: Crea redes virtuales independientes de la infraestructura fisica.
- Memoria: Permite que varias maquinas virtuales compartan y administren la memoria RAM de forma eficiente. El hipervisor administra la memoria y evita que una maquina virtual use mas recursos de los asignados.
- Almacenamiento: Agrupa dispositivos fisicos de almacenamiento para presentarlos como una unica unidad logica
- Entrada/Salida: Es el proceso mediante el cual los dispositivos de entrada y salida (como USB, discos duros, impresoras, etc) pueden ser utilizados por maquinas virtuales.
