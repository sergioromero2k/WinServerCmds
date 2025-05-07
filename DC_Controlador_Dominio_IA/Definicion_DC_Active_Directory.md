# Controlador de Dominio (DC)
---
Un **Controlador de Dominio (Domain Controller, DC)** es un servidor que gestiona la autenticación y el acceso a los recursos dentro de una red de dominio.

**📌 Funciones principales de un DC**

✅ **Autenticación de usuarios** → Verifica credenciales cuando un usuario inicia sesión en la red.
✅ **Autorización de acceso** → Determina qué recursos puede usar un usuario (archivos, impresoras, servidores, etc.).
✅ **Gestión centralizada** → Administra cuentas de usuarios, grupos y políticas de seguridad.
✅ **Replica información** → Si hay varios controladores de dominio, sincronizan la información entre ellos para evitar fallos.

**📌 Ejemplo en una empresa**

Cuando un empleado en una oficina inicia sesión en su PC, su solicitud de acceso va a un Controlador de Dominio que verifica su usuario y contraseña en Active Directory. Si la autenticación es correcta, le da acceso a su perfil y recursos compartidos.

# ¿Qué es Active Directory (AD)?
---
**Active Directory (AD)** es una base de datos y un servicio desarrollado por Microsoft que almacena y administra usuarios, computadoras y recursos dentro de una red.

**📌 Funciones principales de Active Directory**

✅ **Base de datos centralizada** → Guarda información de usuarios, equipos, grupos, políticas y permisos.
✅ **Autenticación y autorización** → Permite que los usuarios accedan a recursos según sus permisos.
✅ **Administración de políticas de grupo (GPOs)** → Aplica configuraciones de seguridad y restricciones a usuarios y equipos.
✅ **Escalabilidad y organización** → Permite estructurar una red con dominios, unidades organizativas (OU) y políticas de acceso.

### Diferencia entre Active Directory y un Controlador de Dominio

| Característica              | Active Directory (AD)                                       | Controlador de Dominio (DC)                                        |
|-----------------------------|-------------------------------------------------------------|--------------------------------------------------------------------|
| **¿Qué es?**                 | Una base de datos y servicio de autenticación.              | Un servidor que ejecuta AD y gestiona autenticaciones.             |
| **¿Qué hace?**               | Almacena información sobre usuarios, equipos y permisos.    | Procesa solicitudes de autenticación y autorización.               |
| **¿Dónde se encuentra?**     | Se ejecuta dentro de un Controlador de Dominio.              | Es un servidor físico o virtual dentro de la red.                  |
| **Ejemplo práctico**         | Es como una libreta de direcciones con usuarios y contraseñas. | Es el recepcionista que verifica quién puede entrar a un edificio. |
