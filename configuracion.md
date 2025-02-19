# Guía Completa de Configuración de un Switch en Cisco Packet Tracer

Este README está diseñado para guiarte a través de la configuración de un switch en **Cisco Packet Tracer** y cómo segmentar tu red utilizando **VLANs**. Esta guía está especialmente dirigida a personas que están empezando en el mundo de las redes y que nunca han utilizado Cisco Packet Tracer.

En este ejemplo, vamos a conectar tres PCs a un switch, configurar dos VLANs y hacer pruebas de comunicación entre ellas.

## Índice
1. [Requisitos](#requisitos)
2. [Sección 1: Configuración Básica del Switch](#sección-1-configuración-básica-del-switch)
    1. [Colocar Dispositivos y Conectar](#11-colocar-dispositivos-y-conectar)
    2. [Configuración Básica del Switch](#12-configuración-básica-del-switch)
    3. [Asignar Direcciones IP a las PCs](#13-asignar-direcciones-ip-a-las-pcs)
    4. [Configurar VLANs en el Switch](#14-configurar-vlans-en-el-switch)
    5. [Guardar Configuración](#15-guardar-configuración)
3. [Sección 2: Verificación de la Comunicación](#sección-2-verificación-de-la-comunicación)

## Requisitos

Antes de comenzar, asegúrate de tener lo siguiente:
- **Cisco Packet Tracer** instalado en tu computadora.
- Un **switch** (como el Switch 2960) y **3 PCs** en el área de trabajo de Packet Tracer.
- **Cables Ethernet** para conectar el switch con las PCs.

## Sección 1: Configuración Básica del Switch

### 1.1 Colocar Dispositivos y Conectar

**Paso 1: Abrir Cisco Packet Tracer**
1. Abre **Cisco Packet Tracer** en tu computadora.

**Paso 2: Colocar el Switch en el área de trabajo**
1. En la barra de dispositivos a la izquierda, selecciona el **switch** (por ejemplo, **Switch 2960**).
2. Arrastra el switch al área de trabajo en el centro de la pantalla.
![image](https://github.com/user-attachments/assets/f18b379d-feca-4d07-9b6e-7fb60e18890d)

**Paso 3: Colocar las PCs en el área de trabajo**
1. En la barra de dispositivos, selecciona **End Devices** y luego elige **PC**.
2. Arrastra **3 PCs** al área de trabajo.
![image](https://github.com/user-attachments/assets/536c8496-1940-4d67-9753-c34fabeaa9e8)

![image](https://github.com/user-attachments/assets/f151e354-6e47-47a4-bcfe-274dfb4092e8)

**Paso 4: Conectar el Switch con las PCs**
1. Usa el **cable Ethernet** (Copper Straight-Through) para conectar las **3 PCs** al switch.
![image](https://github.com/user-attachments/assets/0f46a8ce-6ac7-4a85-8f0c-902830fa6c85)

   - Conecta **PC 1** al puerto **FastEthernet0/1** del switch.
   - Conecta **PC 2** al puerto **FastEthernet0/2** del switch.
   - Conecta **PC 3** al puerto **FastEthernet0/3** del switch.
![image](https://github.com/user-attachments/assets/9082a049-ddde-4a0c-aedd-98996fc5c54c)

### 1.2 Configuración Básica del Switch

Ahora que hemos configurado las VLANs, es hora de aplicar la configuración básica del switch para proteger el acceso y darle un nombre.

1. **Acceder al CLI del switch**:  
   Haz clic en el **switch** y ve a la pestaña **CLI**.

- **Modo Privilegiado:**  
  Este modo te da acceso a los comandos avanzados. Usa el siguiente comando:
  
```bash
enable
```
Modo de Configuración Global:
Para realizar la configuración global del dispositivo, usa:

```bash
configure terminal
```
    
3. **Cambiar el nombre del switch**:  
   Es una buena práctica asignar un nombre único al switch. Usa el siguiente comando:
```bash
hostname Prueba1
```
![image](https://github.com/user-attachments/assets/b57dbe4d-070d-4585-ac02-46cc53a3396b)

  Configurar una contraseña para el modo privilegiado:
Protege el acceso a los comandos avanzados del switch con una contraseña:

```bash
enable secret MiClaveSegura
```

  Configurar una contraseña para acceso a la consola:
Protege el acceso físico al switch configurando una contraseña para la consola:

```bash
line con 0
password Consola123
login
end
```

  Guardar la configuración:
Para asegurarte de que los cambios se guarden, utiliza el siguiente comando:

```bash
write memory
```
![image](https://github.com/user-attachments/assets/019d07db-b892-42e0-bd74-214369c5c8aa)

### 1.3 Asignar Direcciones IP a las PCs

Para que las PCs se puedan comunicar, necesitamos asignar direcciones IP a cada una de ellas.

1. Haz clic en **PC 1** y ve a la pestaña **Config**.
2. Asigna la siguiente dirección IP a **PC 1**:
   - Dirección IP: `192.168.1.10`
   - Máscara de subred: `255.255.255.0`
3. Repite el proceso para **PC 2** y **PC 3**, asignando las siguientes direcciones:
   - **PC 2**:
     - Dirección IP: `192.168.1.20`
     - Máscara de subred: `255.255.255.0`
   - **PC 3**:
     - Dirección IP: `192.168.2.10`
     - Máscara de subred: `255.255.255.0`
![image](https://github.com/user-attachments/assets/015f764d-5866-4aef-9ed0-6cbb75270bab)

**Nota:** La **PC 1** y la **PC 2** están en la misma subred (`192.168.1.x`), mientras que **PC 3** está en una subred diferente (`192.168.2.x`).

### 1.4 Configurar VLANs en el Switch

Ahora configuraremos dos VLANs para separar el tráfico de red.

1. Haz clic en el **switch** y ve a la pestaña **CLI** (Interfaz de Línea de Comandos).

2. Crea las siguientes VLANs:
   - Para la **VLAN 10** (para **PC 1** y **PC 2**):
```bash
vlan 10
name VLAN10
```

   - Para la **VLAN 20** (para **PC 3**):
```bash
vlan 20
name VLAN20
```
![image](https://github.com/user-attachments/assets/45547ef6-34dd-43fb-810b-3085c2ecdbbc)

3. Asigna los puertos a las VLANs correspondientes:
   - Asigna el puerto **FastEthernet0/1** y **FastEthernet0/2** a la **VLAN 10**:
```bash
interface range FastEthernet0/1 - 2
switchport mode access
switchport access vlan 10
```

   - Asigna el puerto **FastEthernet0/3** a la **VLAN 20**:
```bash
interface FastEthernet0/3
switchport mode access
switchport access vlan 20
```
![image](https://github.com/user-attachments/assets/57009da7-27d2-415e-b324-230b59d2f7fc)

  4. Guardar Configuración
    Una vez que hayas configurado las VLANs y asignado los puertos, guarda la configuración del switch:

```bash
end
```
```bash
write memory
```
![image](https://github.com/user-attachments/assets/a77716d9-bbec-48f8-ae55-e87590d1cdea)

Sección 2: Verificación de la Comunicación
  Ver si las PC1 y PC2 se comunican y esperar que no se puedan comunicar con la PC3

  1. Seleccionar la carta que esta en la parte superior de **Cisco Packet Tracer**
![image](https://github.com/user-attachments/assets/6ec3116f-e464-481a-8156-c071f04b5419)

  2. Con la carta seleccionada presiona la PC1 y luego la PC2 para observar si permite la conexion entre ellas

  3. Verifica que no se permita la conexion con la PC3 seleccionando la carta y sobre la PC1 o PC2 y luego presionando la PC3
