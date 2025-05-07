# ¿Como saber el que función tiene el servidor?
---

## CMD || PowerShell
systeminfo | findstr /i "Domain"

*Ejemplo*
```powershell
PS C:\Users\Administrator> systeminfo | findstr -i "domain"
OS Configuration:          Primary Domain Controller
Domain:                    sergio.local
PS C:\Users\Administrator>
```

net config workstation
*Ejemplo*
```powershell
C:\Users\Administrator>net config workstation
Computer name                        \\DC01
Full Computer name                   dc01.sergio.local
User name                            Administrator

Workstation active on
        NetBT_Tcpip_{63D3A242-C609-4FD1-98B2-1FACC17B3023} (00155D5D7914)

Software version                     Windows Server 2019 Standard Evaluation

Workstation domain                   SERGIO
Workstation Domain DNS Name          sergio.local
Logon domain                         SERGIO

COM Open Timeout (sec)               0
COM Send Count (byte)                16
COM Send Timeout (msec)              250
The command completed successfully.
```

C:\Users\Administrator>

## CMD
echo %logonserver%
    Te muestra el nombre del servidor que autenticó tu sesión. Si estás en el servidor local y es DC, verás su propio nombre.

*Ejemplo*
```cmd
C:\Users\Administrator>echo %logonserver%
\\DC01
C:\Users\Administrator>
```

## PowerShell
Get-WmiObject Win32_ComputerSystem | Select-Object DomainRole
(Get-WmiObject Win32_ComputerSystem).DomainRole

    Te muestra el nombre del servidor que autenticó tu sesión. Si estás en el servidor local y es DC, verás su propio nombre.

Los valores posibles de DomainRole.
Si el valor es 4 o 5, entonces es un controlador de dominio.


| Valor | DomainRole                   |
|-------|------------------------------|
| 0     | Standalone Workstation       |
| 1     | Member Workstation           |
| 2     | Standalone Server            |
| 3     | Member Server                |
| 4     | Backup Domain Controller     |
| 5     | Primary Domain Controller    |


*Ejemplo*
```powershell
PS C:\Users\Administrator> get-wmiobject win32_computersystem | select-object domainrole
domainrole
----------
         5
```