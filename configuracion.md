# Configuración Básica de un Switch

## Objetivo

Este documento cubre los pasos básicos para configurar un switch, ya sea físico o en simuladores como Cisco Packet Tracer. La configuración incluye aspectos básicos como la asignación de nombre, la configuración de contraseñas y la configuración de puertos.

## Requisitos

- **Switch físico** o **simulador** como **Cisco Packet Tracer** o **GNS3**.
- **Cable de consola** para switches físicos o conexión mediante SSH/Telnet para switches remotos.
- Software de terminal como **PuTTY** o **Tera Term**.
- Conocimiento básico de comandos CLI (Command Line Interface).

## Pasos para Configurar un Switch

### 1. **Conexión al Switch**
- **Con un Switch físico**: Conecta un cable de consola entre el switch y tu PC.
- **Con Cisco Packet Tracer**: Agrega un switch desde el menú de dispositivos y conéctalo a otros dispositivos de red.

### 2. **Acceso a la Configuración**
- **Acceso por consola**: Utiliza un software como **PuTTY** o **Tera Term** para acceder al switch.
- **Acceso remoto (SSH/Telnet)**: Si el switch ya tiene una IP configurada, puedes acceder mediante SSH o Telnet.

### 3. **Configuración Básica**
Para ingresar al **modo privilegiado** en el switch:
```shell
enable
```

Accede al modo de configuración:

```shell
configure terminal
```
### 4. **Comandos Básicos**
Configurar el nombre del switch:
```shell
hostname Switch1
```
Configurar la contraseña de acceso:
```shell
enable secret ClaveSegura123
```
Configurar el puerto de consola para contraseñas:
```shell
line con 0
```
```shell
password Consola123
```
```shell
login
```
### 5. **Pruebas de Configuración**
Verificar el nombre configurado:
```shell
show running-config
```
Verificar la configuración de contraseñas:
```shell
show startup-config
```
