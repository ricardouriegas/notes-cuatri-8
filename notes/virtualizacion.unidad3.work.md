---
id: cqggeyrqhawombnhuw29l4r
title: Work
desc: ''
updated: 1742564424993
created: 1742564401626
---
# Alta Disponibilidad y Seguridad de los Datos

## 1. Diferencia entre alta prestación y alta disponibilidad en un entorno virtualizado
**Alta Prestación (High Performance):**  
Se enfoca en maximizar el rendimiento de recursos (CPU, RAM, almacenamiento) para garantizar cargas de trabajo intensivas. Ejemplo: clusters de servidores para procesamiento paralelo.  

**Alta Disponibilidad (High Availability):**  
Garantiza que los servicios estén operativos el mayor tiempo posible, incluso ante fallos. Usa redundancia (ej: máquinas en clúster con failover automático).  

**Diferencia clave:**  
- Alta prestación → Optimización de recursos para velocidad.  
- Alta disponibilidad → Redundancia para minimizar tiempo de inactividad.

---

## 2. Importancia de definir indicadores de rendimiento en sistemas virtualizados
**Importancia:**  
Evitar cuellos de botella y garantizar que las VMs no compitan por recursos. Ejemplo: Si no se limita el uso de CPU de una VM, podría monopolizarla y degradar otras cargas.  

**Ejemplo:**  
Un indicador clave es el **CPU Ready Time** (tiempo que una VM espera por CPU física). Si supera el 5%, se debe optimizar la asignación de recursos.

---

## 3. Escenario crucial para tolerancia a fallos
**Escenario:** Un hospital con sistemas de historiales médicos electrónicos.  
**Razón:** Un fallo podría impedir el acceso a datos críticos durante una emergencia.  
**Solución:** Usar tolerancia a fallos (ej: VMware FT) para mantener una réplica sincronizada en tiempo real de la VM principal.

---

## 4. Protocolos de replicado
| Protocolo | Funcionamiento | Caso de Uso |
|-----------|----------------|-------------|
| **SRM (Site Recovery Manager)** | Replica VMs entre sitios físicos. Usa snapshots y sincronización asíncrona. | Disaster Recovery en VMware. |
| **vSphere Replication** | Replicación a nivel de hipervisor sin necesidad de almacenamiento compartido. | Migración de VMs entre clusters. |
| **Ceph RADOS** | Replicación distribuida en clusters de almacenamiento con consistencia eventual. | Almacenamiento hiperconvergente (HCI). |

---

## 5. Impacto de protocolos de migración en el rendimiento
**Ventaja:** Permiten mover VMs entre hosts sin downtime (ej: vMotion). Ideal para mantenimiento preventivo.  
**Desventaja:** Consumo de ancho de banda durante la migración, lo que puede afectar redes saturadas.  

---

## 6. Migración en caliente vs. en frío
- **Migración en caliente (Live Migration):**  
  La VM sigue ejecutándose durante el traslado (ej: VMware vMotion). Cero downtime.  
- **Migración en frío (Cold Migration):**  
  La VM se apaga antes de moverla. Requiere interrupción del servicio.  

---

## 7. Protocolos de restauración y minimización de pérdidas
Un protocolo de restauración (ej: backups incrementales + snapshots) permite recuperar datos hasta el último estado conocido antes del fallo. Por ejemplo, si un servidor se corrompe, restaurar desde un snapshot de hace 5 minutos reduce la pérdida a solo esos minutos de actividad.

---

## 8. Ejemplo de empresa con alta disponibilidad
**Empresa:** Netflix  
**Estrategias:**  
- Uso de AWS con múltiples regiones (failover automático).  
- Arquitectura de microservicios con balanceo de carga.  
- **Chaos Monkey**: Herramienta para simular fallos y asegurar resiliencia.  

---

## 9. Implementación de tolerancia a fallos en un centro de datos
1. **Redundancia física:** Múltiples fuentes de energía y conexiones de red.  
2. **Hipervisores en clúster:** Ej: VMware HA o Hyper-V Failover Clustering.  
3. **Almacenamiento replicado:** RAID 10 o SAN con replicación síncrona.  
4. **Monitoreo proactivo:** Herramientas como Nagios para alertar antes de fallos.  
5. **Pruebas periódicas:** Simular fallos para validar la recuperación.  

---

## 10. Medición de efectividad de replicado
**Indicadores clave:**  
- **RPO (Objetivo de Punto de Recuperación):** Tiempo máximo de datos perdidos (ej: 15 minutos).  
- **RTO (Objetivo de Tiempo de Recuperación):** Tiempo para restaurar el servicio (ej: 30 minutos).  
- **Consistencia de datos:** Verificar integridad post-replicación.  
- **Throughput de replicación:** Velocidad de transferencia (ej: 1 Gbps).  