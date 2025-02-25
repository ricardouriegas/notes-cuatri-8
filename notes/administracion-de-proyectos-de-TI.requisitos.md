---
id: t7pbh720x1icmsj6zvogezx
title: requisitos
desc: ''
updated: 1740500363925
created: 1739372774447
---
# Requisitos

## Requisitos Funcionales
Los requisitos funcionales describen lo que el sistema debe hacer.

1. **Generación de progresiones armónicas**  
   - El sistema debe generar progresiones armónicas en base a parámetros definidos.

2. **Exportación a MIDI** _este_
   - El sistema debe permitir exportar las progresiones generadas en formato **MIDI** para su uso en software de producción musical.  

3. **Configuración de parámetros** _este_
   - El usuario podrá personalizar:
     - Tempo (**BPM**).
     - Longitud de la progresión (cantidad de acordes).
     - Duración de cada acorde (en compases).  

4. **Interfaz gráfica intuitiva**
   - El sistema debe contar con una interfaz gráfica desarrollada en **PyQt6**, que permita la configuración y generación de progresiones sin necesidad de modificar código.  

5. **Generación aleatoria con coherencia musical**  
   - El sistema debe generar progresiones armónicas de forma aleatoria, asegurando que sean **coherentes dentro de una tonalidad**.  

6. **Soporte para múltiples escalas** *(Opcional en futuras versiones)*  
   - El sistema podría permitir elegir entre diferentes escalas y modos armónicos para diversificar las progresiones.  

---

## Requisitos No Funcionales
Los requisitos no funcionales describen **cómo** debe funcionar el sistema en términos de rendimiento, seguridad, usabilidad, etc.

1. **Usabilidad**  
   - La interfaz debe ser **minimalista y elegante**, facilitando la interacción del usuario sin sobrecargarl  o con opciones innecesarias.  

2. **Compatibilidad**  
   - El software debe ejecutarse en **Windows, Linux y macOS**, sin requerir configuraciones avanzadas.  

3. **Eficiencia**  
   - La generación de progresiones y la exportación a MIDI deben realizarse en **menos de 2 segundos** en equipos de gama media.  

4. **Portabilidad**  
   - El generador debe estar escrito en **Python puro** con dependencias mínimas, evitando requerimientos excesivos o software propietario.  

5. **Extensibilidad**  
   - El código debe estar diseñado de manera modular para facilitar futuras mejoras como:
     - Integración con DAWs.
     - Añadir más escalas o patrones de progresión.   

6. **Documentación**  
   - Se debe incluir documentación clara y concisa para desarrolladores y usuarios finales.  
