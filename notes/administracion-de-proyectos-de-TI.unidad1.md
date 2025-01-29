---
id: jyulhy9skxlsyoey1lzqfl1
title: Unidad1
desc: ''
updated: 1738164028380
created: 1736348452179
---

<!-- ## 7.2.1. Cronograma de Actividades

* **Análisis de Requerimientos:** 1 mes
* **Diseño del Sistema:** 2 meses
* **Desarrollo del Sistema:** 4 meses
* **Pruebas y Validación:** 1.5 meses
* **Implementación y Despliegue:** 1 mes
* **Lanzamiento del Sistema:** 1 día -->

<!-- # Cronograma de Actividades
- **Mes 1:** Definición de requisitos, boceto inicial y planificación.
- **Mes 2:** Desarrollo inicial y creación de la guía de usuario.
- **Mes 3:** Creación de reportes y riesgos identificados.
- **Mes 4:** Despliegue de la beta de la plataforma, monitoreo inicial y ejecución del plan de marketing. -->

# Cronograma de Actividades

| Semana | Actividades                                                         |
|--------|----------------------------------------------------------------------|
| 1-3    | Definición de requisitos, boceto inicial y planificación.           |
| 4-6    | Desarrollo inicial y creación de la guía de usuario.                |
| 7-9    | Creación de reportes y riesgos identificados.                       |
| 10-12  | Despliegue de la beta de la plataforma, monitoreo inicial y ejecución del plan de marketing. |


---

# Entregables del Proyecto

## Tangibles
1. **Plataforma Básica**  
   - **Fase:** Semana 10-12 (Despliegue y monitoreo).  
   - **Descripción:** Una interfaz no funcional básica que demuestra la simulación de evaluaciones anticorrupción.  

2. **Riesgos Identificados**  
   - **Fase:** Semana 7-9 (Pruebas del sistema).  
   - **Descripción:** Una hoja de cálculo simple con categorías de riesgos comunes.  

3. **Reportes de Transparencia Básicos**  
   - **Fase:** Semana 7-9 (Validación funcional).  
   - **Descripción:** Informes para destacar áreas críticas de mejora.  

4. **Guía Rápida de Usuario**  
   - **Fase:** Semana 4-6 (Codificación).  
   - **Descripción:** Documento con pasos básicos para usar la plataforma o realizar evaluaciones.  

5. **Boceto Inicial**  
   - **Fase:** Semana 1-3 (Definición de requisitos).  
   - **Descripción:** Un dibujo simple de la interfaz de usuario.  

## No Tangibles
6. **Guía Conceptual para Evaluar Riesgos de Corrupción**  
   - **Fase:** Semana 4-6 (Codificación).  
   - **Descripción:** Un conjunto de principios y recomendaciones generales para identificar y evaluar riesgos de corrupción (este se entregara al usuario encargado de realizar la auditoria).

7. **Plan de Marketing Inicial**  
   - **Fase:** Semana 10-12 (Despliegue y promoción inicial).  
   - **Descripción:** Una estrategia básica, como una publicación para dar a conocer la plataforma.  
 

--- 

# Guía Rápida de Usuario

## Introducción

Bienvenido/a a la plataforma de evaluación de riesgos de corrupción. Esta guía rápida te ayudará a navegar por la plataforma y aprovechar sus funcionalidades principales.

## Acceso a la Plataforma

1. Abre un navegador web compatible (Chrome, Firefox, Edge).
2. Ingresa la URL de la plataforma proporcionada por el administrador.
3. Inicia sesión con tu cuenta o regístrate si eres un nuevo usuario.

## Evaluación de Riesgos

1. Accede a la sección **Evaluación** desde el menú principal.
2. Completa el formulario con los datos del proceso a evaluar.
3. Usa el **Checklist para Evaluar Riesgos de Corrupción** para identificar posibles riesgos.
4. Guarda la evaluación para futuras consultas.

## Generación de Reportes

1. Dirígete a la sección **Reportes**.
2. Selecciona una evaluación previamente realizada.
3. Genera un informe en formato PDF con los resultados de la evaluación.

## Base de Datos de Riesgos

1. Explora la sección **Riesgos Identificados** para consultar riesgos documentados.
2. Filtra la información por categoría o nivel de riesgo.
3. Agrega nuevos riesgos si cuentas con permisos de edición.

## Configuración y Soporte

1. Accede a la sección **Configuración** para personalizar tu experiencia.
2. Si necesitas ayuda, consulta la sección **Soporte** o contacta al administrador.

## Conclusión

Para más información, revisa la documentación completa o contacta con el equipo de soporte.

# Base de Datos (SQL)
```sql
-- Crear la base de datos
CREATE DATABASE SistemaAnticorrupcion;

-- Seleccionar la base de datos
USE SistemaAnticorrupcion;

-- Tabla para las empresas
CREATE TABLE empresas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    sector VARCHAR(100),
    direccion VARCHAR(255),
    telefono VARCHAR(50),
    correo VARCHAR(100) NOT NULL
);

-- Tabla para los usuarios (empleados o auditores de las empresas)
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_empresa INT,
    nombre VARCHAR(100) NOT NULL,
    correo VARCHAR(100) NOT NULL UNIQUE,
    rol ENUM('Administrador', 'Auditor', 'Empleado') NOT NULL,
    contrasena VARCHAR(255) NOT NULL,
    FOREIGN KEY (id_empresa) REFERENCES empresas(id)
);

-- Tabla para las auditorías realizadas
CREATE TABLE auditorias (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_empresa INT,
    id_usuario INT,
    fecha_inicio DATETIME DEFAULT CURRENT_TIMESTAMP,
    fecha_final DATETIME,
    estado ENUM('Pendiente', 'En Progreso', 'Finalizada') NOT NULL,
    descripcion TEXT,
    FOREIGN KEY (id_empresa) REFERENCES empresas(id),
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id)
);

-- Tabla para las actividades del cronograma (adaptado para auditorías)
CREATE TABLE actividades (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_auditoria INT,
    semana_inicio INT NOT NULL,
    semana_fin INT NOT NULL,
    descripcion VARCHAR(255) NOT NULL,
    FOREIGN KEY (id_auditoria) REFERENCES auditorias(id)
);

-- Tabla para los entregables asociados a las auditorías
CREATE TABLE entregables (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_auditoria INT,
    tipo ENUM('Tangibles', 'No Tangibles') NOT NULL,
    nombre VARCHAR(255) NOT NULL,
    fase VARCHAR(100) NOT NULL,
    descripcion TEXT NOT NULL,
    FOREIGN KEY (id_auditoria) REFERENCES auditorias(id)
);

-- Tabla para los riesgos identificados en una auditoría
CREATE TABLE riesgos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_auditoria INT,
    categoria VARCHAR(100) NOT NULL,
    nivel_riesgo ENUM('Bajo', 'Medio', 'Alto') NOT NULL,
    descripcion TEXT NOT NULL,
    FOREIGN KEY (id_auditoria) REFERENCES auditorias(id)
);

-- Tabla para las evaluaciones realizadas durante las auditorías
CREATE TABLE evaluaciones (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_auditoria INT,
    id_usuario INT,
    fecha DATETIME DEFAULT CURRENT_TIMESTAMP,
    proceso_nombre VARCHAR(255) NOT NULL,
    riesgos_identificados TEXT,
    FOREIGN KEY (id_auditoria) REFERENCES auditorias(id),
    FOREIGN KEY (id_usuario) REFERENCES usuarios(id)
);

-- Tabla para los reportes generados en una auditoría
CREATE TABLE reportes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_auditoria INT,
    id_evaluacion INT,
    formato ENUM('PDF', 'Excel', 'Word') NOT NULL,
    contenido TEXT,
    FOREIGN KEY (id_auditoria) REFERENCES auditorias(id),
    FOREIGN KEY (id_evaluacion) REFERENCES evaluaciones(id)
);
```