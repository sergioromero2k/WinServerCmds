# DNS
---

## 1. Revisar la configuración de replicación de la zona  
1. Abre la consola DNS Manager (`dnsmgmt.msc`).  
2. Navega a **Zonas de búsqueda directa** y selecciona la zona afectada.  
3. En la pestaña **General**, revisa la opción **Replicación** y asegúrate de que esté configurada correctamente para incluir el servidor DNS.  

###  Verificar que el servidor DNS está en la partición correcta

```powershell
dnscmd /enumdirectorypartitions                         # Abre una ventana de Símbolo del sistema como administrador y ejecuta.
dnscmd /enlistdirectorypartition <PartitionName>        # Si la partición esperada no aparece, debes agregar el servidor a la partición.
```

### Asegurar que el servidor DNS es un controlador de dominio válido

Si el servidor DNS no es un Controlador de Dominio (DC) o tiene problemas de sincronización con Active Directory, intenta:

```powershell
dcdiag      /test:dns                   # Para verificar errores relacionados con DNS y Active Directory.
repadmin    /syncall /APeD              # Si hay problemas, forzar la replicación.
repadmin    /replsummary                # Si el problema persiste, revisa el estado del AD ejecutando.
```

## 2.  Ejemplos
---

### Enlistar el servidor en las particiones de Active Directory

**Enunciado**
```powershell
PS C:\Users\Administrator> dnscmd /enumdirectorypartitions
Enumerated directory partition list:

        Directory partition count = 3
            DomainDnsZones.sergio.local               Not-Enlisted
            DomainDnsZones.tech.sergio.local          Not-Enlisted
            ForestDnsZones.sergio.local               Not-Enlisted Auto Forest

Command completed successfully.
PS C:\Users\Administrator>
```

Tu **servidor DNS** no está enlistado en ninguna de las particiones de Active Directory para la replicación de zonas DNS. Esto explica el error que estás viendo. Para solucionar este problema, debes enlistar el servidor DNS en las particiones correspondientes.

Ejecuta los siguientes **comandos en PowerShell** con privilegios de administrador para enlistar el servidor en las particiones de replicación:

```powershell
dnscmd /enlistdirectorypartition DomainDnsZones.sergio.local
dnscmd /enlistdirectorypartition DomainDnsZones.tech.sergio.local
dnscmd /enlistdirectorypartition ForestDnsZones.sergio.local
```

### Verificar la inscripción

```powershell
dnscmd /enumdirectorypartitions
Restart-Service DNS                 #  Reiniciar el servicio DNS
repadmin /syncall /APeD             #  Comprobar la replicación
```

## 3. ¿Puedes hacer que el servidor DNS se enliste automáticamente en las particiones de Active Directory?
---
Sí, puedes hacer que el servidor DNS **se enliste automáticamente en las particiones de Active Directory** mediante **Group Policy (GPO)** o asegurándote de que el rol de DNS se configure correctamente al promover el controlador de dominio.

### Verificar que el servicio DNS está correctamente instalado y configurado
Si el servidor DNS fue instalado después de promover el servidor a controlador de dominio, podría no haberse enlistado automáticamente.

```powershell
    Install-WindowsFeature -Name DNS -IncludeManagementTools    # Asegurarse que el servidor DNS fue install correct.
    Restart-Service DNS                                         # Luego, reinicia el servicio.
```
### Forzar que Active Directory incluya automáticamente el servidor en las particiones de DNS
Usa el siguiente comando para registrar el servidor en las **particiones de AD**
Esto debería crear y enlistar automáticamente el servidor en las particiones predeterminadas de DNS.

```powershell
dnscmd /createdefaultdirectorypartitions    
```

## 4. Particiones en Active Directory
---
Las particiones de directorio son divisiones lógicas dentro de la base de datos de AD que almacenan información específicia y y controlan su replicación.

Cuando un servidor DNS está integrado con Active Directory, **las zonas DNS** pueden almacenarse en estas particiones en lugar de archivos planos (.dns). **Para que un servidor DNS puede participar en la replicación de zonas**, deber estar enlistado en la partición correspondiente. 

Son particiones dentro de la base de datos de AD utilizadas específicamente para almacenar información de zonas DNS está integrado con Active Directory. En un lugar de usar archivos planos(.dns), los datos de las zonas se almacenan en AD y se replican de manera eficiente entre los servidores DNS autorizados.

###  🔹Tipos de Particiones en Active Directory

**1️⃣ ForestDNSZones**

1. **Replicación**.- Se replcia en todos los controladores de dominio del bosque que tienen el rol de servidor DNS.
2. **Propósito**.- Almacena las zonas DNS que deben ser accesibles en todo el bosque de Active Directory.

**2️⃣ DomainDNSZones**

1.  **Replicación**.- Se replica solo entre los controladores de dominio dentro de un mismo dominio que tienen el rol de servidor DNS.
2. **Propósito**.- Almacena las zonas DNS que son específicas de un solo dominio.

###  🔹¿Por qué son necesarias las particiones DNS en AD?

1.  **Replicación eficiente** 🔄.- En lugar de usar la replicación estándar de zonas DNS (como en servidores DNS tradicionales), AD usa su propio mecanismo de replicación, optimizado para sincronizar datos DNS entre controladores de dominio.

2. **Mayor seguridad** 🔐.- Los datos DNS almacenados en AD heredan las mismas protecciones y permisos de seguridad que los demás objetos de AD.

3. **Menos riesgo de inconsistencias** ⚖️.- Al estar integradas en AD, las zonas DNS se replican junto con la base de datos de AD, evitando discrepancias entre servidores DNS.

4. **Reducción del tráfico de red** 📉.- La replicación basada en AD es más eficiente que la replicación estándar de DNS, reduciendo el tráfico innecesario en la red.

5. **Administración centralizada** 🛠️.- Las zonas DNS almacenadas en AD pueden administrarse fácilmente desde la consola de administración de DNS, sin necesidad de gestionar archivos manualmente.

En resumen, las particiones de DNS en AD optimizan la replicación, seguridad y administración del DNS en entornos emrpesariales con Active Directory.
