---
id: cqggeyrqhawombnhuw29l4r
title: Work
desc: ''
updated: 1742582765180
created: 1742564401626
---
# Alta Disponibilidad y Seguridad de los Datos

## 1. Diferencia entre alta prestación y alta disponibilidad en un entorno virtualizado
La alta prestación es maximizar el rendimiento de recursos como CPU, RAM y almacenamiento para cargas intensivas (por ejemplo, con clústeres de servidores). La alta disponibilidad se centra en mantener los servicios operativos en todo momento gracias a soluciones de redundancia.

---

## 2. Importancia de definir indicadores de rendimiento en sistemas virtualizados
Para evitar cuellos de botella y que las máquinas virtuales compitan por los recursos. Por ejemplo, el "CPU Ready Time" (tiempo que una VM espera para acceder a la CPU) no debería superar el 5%, lo que indica que es necesario ajustar la asignación de recursos.

---

## 3. Escenario crucial para tolerancia a fallos
Un hospital donde se gestionan historiales médicos electrónicos. Un fallo podría bloquear el acceso a datos vitales, por lo que es crucial disponer de mecanismos de tolerancia a fallos, como VMware FT, que garantiza la sincronización en tiempo real mediante réplicas.

---

## 4. Protocolos de replicado
Para replicar datos de forma segura y eficaz, existen diversos protocolos. A continuación se muestra una tabla con algunos ejemplos y sus respectivos casos de uso:

| Protocolo              | Funcionamiento                                                        | Caso de Uso                          |
|------------------------|----------------------------------------------------------------------|--------------------------------------|
| **SRM (Site Recovery Manager)**    | Replica VMs entre sitios físicos usando snapshots y sincronización asíncrona. | Disaster Recovery en VMware.         |
| **vSphere Replication**            | Replicación a nivel de hipervisor sin necesidad de almacenamiento compartido.      | Migración de VMs entre clusters.     |
| **Ceph RADOS**                     | Replicación distribuida en clusters de almacenamiento con consistencia eventual.   | Almacenamiento hiperconvergente (HCI). |

---

## 5. Impacto de protocolos de migración en el rendimiento
Las migraciones permiten trasladar VMs sin interrumpir su funcionamiento, resultando bueno para tareas de mantenimiento. Sin embargo, es importante considerar que este proceso puede consumir un ancho de banda considerable, lo cual podría afectar redes congestionadas.

---

## 6. Migración en caliente vs. en frío
En la migración en caliente; la VM continúa operando durante el traslado (por ejemplo, usando VMware vMotion), lo que significa que no se interrumpe el servicio. Por otro lado, la migración en frío requiere apagar la máquina virtual antes de moverla, causando una breve interrupción.

---

## 7. Protocolos de restauración y minimización de pérdidas
Contar con protocolos de restauración, como backups incrementales y snapshots, permite recuperar la información hasta el último punto registrado antes de un fallo. Por ejemplo, restaurar desde un snapshot tomado cinco minutos antes puede limitar la pérdida de datos a ese corto periodo.

---

## 8. Ejemplo de empresa con alta disponibilidad
Santander ilustra de manera práctica cómo se puede construir un sistema robusto. Utilizan centros de datos en diversas ubicaciones, replicación de datos en tiempo real y un monitoreo constante, lo que les permite responder rápidamente ante cualquier incidente.

---

## 9. Implementación de tolerancia a fallos en un centro de datos
Para mejorar la tolerancia a fallos en un centro de datos se pueden aplicar varias medidas: 
- Utilizar múltiples fuentes de energía y conexiones para asegurar redundancia física
- Implementar hipervisores en clúster como VMware HA o Hyper-V Failover Clustering
- Usar almacenamiento replicado mediante RAID 10 o SAN
- Establecer un monitoreo proactivo con herramientas como Nagios
- Realizar simulacros periódicos para verificar que el sistema responde apropiadamente

---

## 10. Medición de efectividad de replicado
La efectividad de la replicación se evalúa mediante indicadores como el RPO (que define el tiempo máximo permitido para la pérdida de datos, por ejemplo, 15 minutos) y RTO (el tiempo que se tarda en restaurar el servicio, por ejemplo, 30 minutos). Otros factores importantes son la consistencia de los datos y la velocidad de transferencia, que podría rondar los 1 Gbps.