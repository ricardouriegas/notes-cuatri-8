---
id: cs41mwgod7rlcymwixu7xyd
title: Manual De Virtualización
desc: ''
updated: 1738352503318
created: 1738346129661
---
# Manual De Virtualización (Gnome-Boxes)
_Ricardo Emmanuel Uriegas Ibarra - 2230122_

## Pasos para Crear y Configurar la Máquina Virtual en Gnome Boxes

### 1. Creación de la Máquina Virtual
1. Abrir Gnome Boxes y hacer clic en "Nueva" lo cual te mandara a elegir el archivo ISO correspondiente al sistema operativo a instalar.
![alt text](image-28.png)
2. Asigna un nombre a la máquina virtual y selecciona el tipo y la versión del sistema operativo.
![alt text](Screenshot_20250131_083918.png)
    
### 2. Instalación del Sistema Operativo
1. Automáticamente se monta la imagen ISO de Windows 10 en la unidad virtual.
![alt text](Screenshot_20250131_084044.png)
![alt text](Screenshot_20250131_084119.png)
2. Sigue los pasos de instalación de Windows como si fueras a instalar en una computadora normal.
![alt text](Screenshot_20250131_084219.png)
![alt text](Screenshot_20250131_084254.png)
![alt text](Screenshot_20250131_084313.png)
![alt text](Screenshot_20250131_084356.png)
![alt text](Screenshot_20250131_084451.png)
![alt text](Screenshot_20250131_084506.png)
![alt text](Screenshot_20250131_090627.png)
![alt text](Screenshot_20250131_090658.png)
![alt text](Screenshot_20250131_091722.png)
![alt text](Screenshot_20250131_092022.png)
![alt text](Screenshot_20250131_092041.png)
![alt text](Screenshot_20250131_092057.png)
![alt text](Screenshot_20250131_092114.png)
![alt text](Screenshot_20250131_092143.png)
![alt text](Screenshot_20250131_092203.png)
![alt text](Screenshot_20250131_092220.png)
![alt text](Screenshot_20250131_092250.png)
![alt text](Screenshot_20250131_092325.png)
![alt text](Screenshot_20250131_092520.png)
    
### 3. Configuración y Ajuste de Recursos
1. Ajusta la memoria RAM y núcleos de CPU desde la sección de configuración. También en esta sección se puede administrar el almacenamiento mas no la red (ya que esta por defecto se toma del anfitrión).
![alt text](image-29.png)
![alt text](Screenshot_20250131_125108.png)
![alt text](Screenshot_20250131_125129.png)
2. Si desea ajustar mas a fondo (como por ejemplo controladores de red) debes tener conocimientos mas profundos y modificar el archivo XML de la máquina virtual.
![alt text](image-31.png)
![alt text](image-30.png)
3. También se puede configurar snapshots (copias de seguridad que toman una foto al sistema para poder regresar a ese punto en caso de fallo). 
![alt text](Screenshot_20250131_125144.png)