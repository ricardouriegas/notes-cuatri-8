---
id: k6poz0ubcu1l7nr6ccb1ire
title: Tarea
desc: ''
updated: 1737860790741
created: 1737860682422
---
# Respuesta sobre la arquitectura de Netflix

## Servicios de AWS utilizados
Netflix usa varios servicios de AWS para soportar su infraestructura global y escalar según las necesidades:
- **EC2 (Elastic Compute Cloud)**: Proporciona la capacidad de cómputo para manejar el tráfico masivo y adaptarse a cambios de demanda.
- **S3 (Simple Storage Service)**: Almacena grandes cantidades de datos, como copias de seguridad, contenido multimedia y archivos relacionados.
- **DynamoDB**: Base de datos NoSQL usada para manejar metadatos y datos dinámicos, como preferencias de usuario.
- **CloudFront**: Servicio CDN que ayuda a distribuir contenido multimedia a nivel mundial, asegurando baja latencia y mayor velocidad.
- **EMR (Elastic MapReduce)**: Utilizado para procesar grandes volúmenes de datos, como el análisis de hábitos de usuarios para mejorar las recomendaciones.

---

## ¿Por qué usan microservicios y no un monolito?

### Microservicios
Los microservicios son componentes pequeños e independientes que trabajan juntos. Cada uno tiene su propia función y se comunica con los demás a través de APIs bien definidas. Por ejemplo, puede haber un microservicio solo para recomendaciones y otro para manejar la búsqueda.

**Ventajas de los microservicios**:
- Escalabilidad independiente: Si un servicio tiene más tráfico (como las recomendaciones), solo ese se escala.
- Mejor resiliencia: Si un microservicio falla, no afecta al sistema completo.
- Desarrollo modular: Equipos diferentes pueden trabajar en servicios específicos sin interferir.

### Monolito
Un monolito es una aplicación unificada donde todo está en un único bloque de código. Si crece demasiado, puede volverse difícil de manejar.

**Problemas de los monolitos**:
- Difícil de escalar por partes: Hay que escalar toda la aplicación aunque solo una funcionalidad lo necesite.
- Mayor riesgo: Un fallo puede tumbar todo el sistema.
- Mantenimiento complejo: Cualquier cambio puede afectar a todo el sistema.

**¿Por qué Netflix usa microservicios?**
- Para ser más flexible, escalar solo lo necesario y evitar que un problema en una parte detenga toda la plataforma.

---

## ¿Por qué usan un CDN?

- **CDN (Red de Entrega de Contenido)**: Es una red de servidores distribuidos en diferentes lugares que entregan contenido desde el nodo más cercano al usuario.
- **Beneficios**:
  - Reduce la latencia: Los datos llegan más rápido al usuario.
  - Mejora la experiencia: Streaming sin interrupciones.
  - Maneja la carga: Distribuye el tráfico para evitar saturaciones.

Netflix usa **Amazon CloudFront** como su CDN principal, permitiendo que los usuarios de cualquier lugar tengan acceso rápido al contenido sin importar la distancia del servidor principal.

---

## Solución de caché

Netflix utiliza **EVCache**, que es una solución de caché distribuida basada en **Memcached**.

- **¿Qué hace?**: Almacena datos frecuentes en memoria, como los metadatos de películas o el historial de visualización de los usuarios.
- **¿Por qué lo usan?**:
  - Acelera las respuestas al usuario.
  - Disminuye la carga en las bases de datos principales.
  - Aumenta la disponibilidad de datos incluso si otros sistemas están lentos.

**Cómo funciona**:
1. Cuando un usuario accede a Netflix, los datos de su perfil y recomendaciones se obtienen primero de EVCache.
2. Si no están en caché, se consultan en la base de datos y luego se almacenan en EVCache para futuras consultas rápidas.

---

## Tipos de bases de datos usadas

Netflix usa diferentes bases de datos para distintas tareas:

1. **DynamoDB**:
   - Base de datos NoSQL.
   - Ideal para almacenar metadatos, configuraciones y preferencias de usuario.
   - Es rápida, con baja latencia y escalable globalmente.

2. **Cassandra**:
   - Otra base de datos NoSQL.
   - Diseñada para manejar grandes volúmenes de datos, como registros de actividad, logs de usuarios y métricas.

3. **MySQL**:
   - Base de datos relacional.
   - Se usa para datos que requieren transacciones complejas, como facturación y administración de cuentas.

**¿Por qué usan varias bases de datos?**
Cada una está optimizada para diferentes tipos de datos y usos, lo que mejora la eficiencia y el rendimiento del sistema.
