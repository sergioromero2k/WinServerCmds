# Unidades Organizativas en Windows Server

Las **Unidades Organizativas (OU)** son contenedores dentro de **Active Directory** que permiten organizar y gestionar objetos como usuarios, grupos y computadoras en una red.

## ¿Para qué sirven?

1. **Organización**: Facilitan la organización jerárquica de los objetos dentro de un dominio, mejorando la administración de recursos.
   
2. **Delegación de control**: Permiten delegar permisos administrativos a diferentes usuarios, para que gestionen solo partes específicas del directorio sin afectar el dominio completo.

3. **Aplicación de políticas de grupo (GPOs)**: Se pueden aplicar GPOs a OUs específicas, controlando configuraciones y políticas de seguridad para los objetos dentro de esa unidad.

4. **Mejora en la administración**: Simplifican la gestión de grandes entornos de red, permitiendo una administración más eficiente de los recursos.

En resumen, las Unidades Organizativas son clave para una administración efectiva de usuarios y recursos en un entorno Windows Server.

## Comandos

```powershell
## Activar la protección contra eliminación
Set-ADOrganizationalUnit -Identity "OU=NombreDeLaOU,DC=dominio,DC=com" -ProtectedFromAccidentalDeletion $true

## Desactivar la protección contra eliminación
Set-ADOrganizationalUnit -Identity "OU=NombreDeLaOU,DC=dominio,DC=com" -ProtectedFromAccidentalDeletion $false

## Para eliminar una Unidad Organizativa (OU) en PowerShell recursivamente
Remove-ADOrganizationalUnit -Identity "OU=NombreDeLaOU,DC=dominio,DC=com" -Recursive -Confirm:$false
```

