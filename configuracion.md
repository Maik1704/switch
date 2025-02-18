# Configuración Básica de un Switch

## Requisitos

- **Switch físico** o **simulador Cisco Packet Tracer**.
- **Cable de consola** (si usas un switch físico).
- **Software de terminal** como **PuTTY** o **Tera Term** (si usas un switch físico).
- **Conexión a red** en caso de usar un switch virtual en Cisco Packet Tracer.

## Pasos para Configuración Básica de un Switch

### 1. **Acceder al Switch**

#### **Con Switch Físico:**
1. Conecta el **cable de consola** desde el puerto de consola del switch al puerto COM de tu computadora.
2. Abre el programa **PuTTY** o **Tera Term**.
3. Selecciona el puerto adecuado (usualmente **COM1** o **COM3**) y haz clic en **Open**.
4. Verás una terminal donde podrás ingresar los comandos.

#### **Con Cisco Packet Tracer:**
1. Abre **Cisco Packet Tracer**.
2. En el menú de dispositivos, selecciona un **switch** y arrástralo al área de trabajo.
3. Haz clic en el **switch** para acceder a la configuración.
4. En la ventana emergente, selecciona la pestaña **CLI** (Command Line Interface).
---
### 2. **Acceder al CLI (Command Line Interface)**

Una vez que accedas al **CLI**, realiza lo siguiente:

1. Para acceder al **modo privilegiado**:
```shell
enable
```

2. Accede al modo de configuración global:
```shell
configure terminal
```
---
### 3. **Configuración Básica**
Ahora, configuraremos lo básico:

Asignar un nombre al switch:

Para cambiar el nombre del switch, usa el siguiente comando:
```shell
hostname Switch1
```
Configurar una contraseña para acceso privilegiado:

Esta contraseña protegerá el acceso al modo privilegiado:
```shell
enable secret MiClaveSegura
```
Configurar una contraseña para acceso a la consola:

Esto protegerá el acceso a la consola del switch:
```shell
line con 0
password Consola123
login
```
Guardar la configuración:

Para guardar los cambios, usa:
```shell
write memory
```
---
### 4. **Pruebas de Configuración**
Para verificar que la configuración se haya realizado correctamente, usa los siguientes comandos:

Verifica el nombre configurado:
```shell
show running-config
```

Verifica las contraseñas configuradas:
```shell
show startup-config
```

Con estos pasos, has configurado el switch básico correctamente. Ahora está listo para pasar a configuraciones más avanzadas. Si tienes más preguntas o deseas realizar configuraciones adicionales, sigue con el siguiente nivel de configuración.
