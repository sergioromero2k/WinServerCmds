# Comandos básicos Windows Server
---

1. Get-Help             # Muestra la ayuda sobre comandos o cmdlets disponibles             || Get-help <cmdlet> or Get-Help Get-Process
2. Get-Command          # Muestra una lista de todos los comandos disponibles en PowerShell || Get-Command


3. Get-Service          # Obtiene el estado de los servicios en el sistema                  || Get-Service (Muestra todos los servicios) or Get-Service <nombre del servicio>
4. Start-Service        # Inicia una servicio en el sistema                                 || Start-Service <nombre del servicio> 
5. Stop-Service         # Detiene un servicio en el sistema                                 || Stop-Service <nombre del servicio>

6. Get-Process          # Muestra una lista de los procesos que están ejecutándose en el sistema
7. Stop-Process         # Detiene un proceso específico en el sistema

8. Get-EventLog         # Obtiene eventos de los registros de eventos del sistema
9. Clear-EventLog       # Limpia los registros de eventos del sistema









# Servicios
---
Get-Service wuauserv para ver el servicio de actualizaciones











































Get-Help

Función: Muestra la ayuda sobre comandos o cmdlets disponibles.
Uso: Get-Help <cmdlet> (Ej. Get-Help Get-Process)
Get-Command

Función: Muestra una lista de todos los comandos disponibles en PowerShell.
Uso: Get-Command
Get-Service

Función: Obtiene el estado de los servicios en el sistema.
Uso: Get-Service (Muestra todos los servicios) o Get-Service <nombre del servicio> (Ej. Get-Service wuauserv para ver el servicio de actualizaciones)
Start-Service

Función: Inicia un servicio en el sistema.
Uso: Start-Service <nombre del servicio> (Ej. Start-Service wuauserv)
Stop-Service

Función: Detiene un servicio en el sistema.
Uso: Stop-Service <nombre del servicio> (Ej. Stop-Service wuauserv)
Get-Process

Función: Muestra una lista de los procesos que están ejecutándose en el sistema.
Uso: Get-Process
Stop-Process

Función: Detiene un proceso específico en el sistema.
Uso: Stop-Process -Name <nombre del proceso> (Ej. Stop-Process -Name notepad)
Get-EventLog

Función: Obtiene eventos de los registros de eventos del sistema.
Uso: Get-EventLog -LogName Application (Ej. para obtener eventos de la aplicación)
Clear-EventLog

Función: Limpia los registros de eventos del sistema.
Uso: Clear-EventLog -LogName Application (Limpia los eventos de la aplicación)
Get-LocalUser

Función: Muestra todos los usuarios locales en el sistema.
Uso: Get-LocalUser
New-LocalUser

Función: Crea un nuevo usuario local en el sistema.
Uso: New-LocalUser -Name <nombre de usuario> -Password (ConvertTo-SecureString "<contraseña>" -AsPlainText -Force)
Set-LocalUser

Función: Modifica las propiedades de un usuario local.
Uso: Set-LocalUser -Name <nombre de usuario> -AccountDisabled $true (Desactiva la cuenta del usuario)
Add-LocalGroupMember

Función: Añade un usuario a un grupo local.
Uso: Add-LocalGroupMember -Group "Administrators" -Member <nombre de usuario>
Remove-LocalGroupMember

Función: Elimina un usuario de un grupo local.
Uso: Remove-LocalGroupMember -Group "Administrators" -Member <nombre de usuario>
Set-ExecutionPolicy

Función: Establece la política de ejecución de scripts de PowerShell.
Uso: Set-ExecutionPolicy RemoteSigned (Permite la ejecución de scripts firmados localmente y remotos)
Get-ADUser

Función: Obtiene información sobre usuarios en Active Directory.
Uso: Get-ADUser -Identity <nombre de usuario>
Set-ADUser

Función: Modifica las propiedades de un usuario en Active Directory.
Uso: Set-ADUser -Identity <nombre de usuario> -Title "Administrador"
Get-ADComputer

Función: Obtiene información sobre las computadoras en Active Directory.
Uso: Get-ADComputer -Filter * (Muestra todas las computadoras)
Add-ADGroupMember

Función: Agrega un usuario a un grupo de Active Directory.
Uso: Add-ADGroupMember -Identity <nombre del grupo> -Members <nombre del usuario>
Remove-ADGroupMember

Función: Elimina un usuario de un grupo en Active Directory.
Uso: Remove-ADGroupMember -Identity <nombre del grupo> -Members <nombre del usuario>
Get-ADDomain

Función: Muestra información sobre el dominio de Active Directory.
Uso: Get-ADDomain
Get-ADTrust

Función: Muestra la configuración de relaciones de confianza en Active Directory.
Uso: Get-ADTrust
Restart-Computer

Función: Reinicia una computadora de manera remota.
Uso: Restart-Computer -ComputerName <nombre del equipo>
Shutdown-Computer

Función: Apaga una computadora de manera remota.
Uso: Shutdown-Computer -ComputerName <nombre del equipo>
Get-Content

Función: Muestra el contenido de un archivo.
Uso: Get-Content "C:\ruta\al\archivo.txt"
Estos son solo algunos de los comandos básicos que puedes utilizar para administrar y configurar Windows Server mediante PowerShell. Cada uno tiene múltiples opciones y parámetros que te permiten afinar y personalizar las tareas según tus necesidades.