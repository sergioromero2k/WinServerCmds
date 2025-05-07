# Comandos básicos Windows Server
---

```powershell

Get-Help  # Muestra la ayuda sobre comandos o cmdlets disponibles.
# Uso: Get-Help <cmdlet> (Ej. Get-Help Get-Process)

Get-Command  # Muestra una lista de todos los comandos disponibles en PowerShell.
# Uso: Get-Command

Get-Service  # Obtiene el estado de los servicios en el sistema.
# Uso: Get-Service (Muestra todos los servicios) o Get-Service <nombre del servicio> (Ej. Get-Service wuauserv para ver el servicio de actualizaciones)

Start-Service  # Inicia un servicio en el sistema.
# Uso: Start-Service <nombre del servicio> (Ej. Start-Service wuauserv)

Stop-Service  # Detiene un servicio en el sistema.
# Uso: Stop-Service <nombre del servicio> (Ej. Stop-Service wuauserv)

Get-Process  # Muestra una lista de los procesos que están ejecutándose en el sistema.
# Uso: Get-Process

Stop-Process  # Detiene un proceso específico en el sistema.
# Uso: Stop-Process -Name <nombre del proceso> (Ej. Stop-Process -Name notepad)

Get-EventLog  # Obtiene eventos de los registros de eventos del sistema.
# Uso: Get-EventLog -LogName Application (Ej. para obtener eventos de la aplicación)

Clear-EventLog  # Limpia los registros de eventos del sistema.
# Uso: Clear-EventLog -LogName Application (Limpia los eventos de la aplicación)

Get-LocalUser  # Muestra todos los usuarios locales en el sistema.
# Uso: Get-LocalUser

New-LocalUser  # Crea un nuevo usuario local en el sistema.
# Uso: New-LocalUser -Name <nombre de usuario> -Password (ConvertTo-SecureString "<contraseña>" -AsPlainText -Force)

Set-LocalUser  # Modifica las propiedades de un usuario local.
# Uso: Set-LocalUser -Name <nombre de usuario> -AccountDisabled $true (Desactiva la cuenta del usuario)

Add-LocalGroupMember  # Añade un usuario a un grupo local.
# Uso: Add-LocalGroupMember -Group "Administrators" -Member <nombre de usuario>

Remove-LocalGroupMember  # Elimina un usuario de un grupo local.
# Uso: Remove-LocalGroupMember -Group "Administrators" -Member <nombre de usuario>

Set-ExecutionPolicy  # Establece la política de ejecución de scripts de PowerShell.
# Uso: Set-ExecutionPolicy RemoteSigned (Permite la ejecución de scripts firmados localmente y remotos)

Get-ADUser  # Obtiene información sobre usuarios en Active Directory.
# Uso: Get-ADUser -Identity <nombre de usuario>

Set-ADUser  # Modifica las propiedades de un usuario en Active Directory.
# Uso: Set-ADUser -Identity <nombre de usuario> -Title "Administrador"

Get-ADComputer  # Obtiene información sobre las computadoras en Active Directory.
# Uso: Get-ADComputer -Filter * (Muestra todas las computadoras)

Add-ADGroupMember  # Agrega un usuario a un grupo de Active Directory.
# Uso: Add-ADGroupMember -Identity <nombre del grupo> -Members <nombre del usuario>

Remove-ADGroupMember  # Elimina un usuario de un grupo en Active Directory.
# Uso: Remove-ADGroupMember -Identity <nombre del grupo> -Members <nombre del usuario>

Get-ADDomain  # Muestra información sobre el dominio de Active Directory.
# Uso: Get-ADDomain

Get-ADTrust  # Muestra la configuración de relaciones de confianza en Active Directory.
# Uso: Get-ADTrust

Restart-Computer  # Reinicia una computadora de manera remota.
# Uso: Restart-Computer -ComputerName <nombre del equipo>

Shutdown-Computer  # Apaga una computadora de manera remota.
# Uso: Shutdown-Computer -ComputerName <nombre del equipo>

Get-Content  # Muestra el contenido de un archivo.
# Uso: Get-Content "C:\ruta\al\archivo.txt"

```






































