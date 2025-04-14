# Cambiar hora en una máquina Windows

## Importancia de la sincronización de servidores Windows

Es muy importante que los servidores Windows estén sincronizados por varias razones clave, entre las cuales se destacan:

1. **Seguridad**  
   Muchos protocolos de seguridad, como Kerberos, dependen de la sincronización precisa del tiempo. Si los servidores tienen relojes desincronizados, pueden ocurrir problemas con la autenticación de usuarios y la validación de credenciales, lo que podría permitir ataques o accesos no autorizados.

2. **Funciones de red**  
   Muchos servicios de red, como la replicación de directorios en Active Directory, requieren que los servidores tengan la misma hora. Si hay desincronización, los servidores pueden tener problemas para comunicarse entre sí, lo que puede afectar la integridad de los datos y la disponibilidad de los servicios.

3. **Registro de eventos (logs)**  
   Los registros de eventos en Windows son fundamentales para la solución de problemas y el monitoreo de la red. Si los servidores no están sincronizados, los registros de eventos pueden tener marcas de tiempo erróneas, lo que dificulta la correlación de eventos a través de múltiples servidores, complicando la identificación de causas raíz y la resolución de problemas.

4. **Programación de tareas**  
   Si los servidores no tienen la hora sincronizada, la programación de tareas automatizadas, como copias de seguridad, actualizaciones y mantenimiento, puede fallar, o incluso ejecutarse en momentos incorrectos.

5. **Consistencia en bases de datos y aplicaciones**  
   Algunas aplicaciones y bases de datos dependen de la sincronización exacta de tiempo para garantizar la coherencia de los datos y los registros de transacciones. Desincronización en el tiempo podría llevar a inconsistencias o pérdidas de datos.

6. **Cumplimiento normativo**  
   En algunos sectores, como el financiero o el de salud, las regulaciones requieren que los sistemas estén sincronizados para garantizar la integridad de los datos y las auditorías. No cumplir con estas normativas podría resultar en sanciones.

## Solución

Para mantener la sincronización, es común utilizar protocolos como **NTP (Network Time Protocol)** que aseguran que todos los servidores en la red estén alineados con una fuente de tiempo confiable (por ejemplo, un servidor de hora global o una fuente interna). Esto ayuda a mantener la integridad de los sistemas y la seguridad general de la infraestructura.

## Comandos

### Método 1. Configuración de Windows
    * Presiona Win + I para abrir Configuración.
    * Ve a Hora e idioma > Fecha y hora.

    * Desactiva Establecer la hora automáticamente.
    * Desactiva Establecer la zona horaria automáticamente (si es necesario).

    * Haz clic en Cambiar en la sección Establecer la fecha y la hora manualmente.
    * Modifica la fecha y la hora según necesites y presiona Aceptar.

### Método 2: Símbolo del sistema (CMD) como administrador
```cmd
date DD/MM/AAAA     # Comando para cambiar la fecha
time HH:MM:SS       # Comando para cambiar la hora
```

### Método 3: PowerShell como administrador
```powershell
Set-Date -Date "16/03/2025 15:30:00"    # Reemplaza la fecha y la hora por la que necesites.
```