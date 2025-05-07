# Principales causas de problemas de replicación de DNS
---

#### 1. Las zonas están configuradas como "almacenadas en Active Directory" pero sólo replican dentro de su dominio

Por defecto, las zonas DNS almacenadas en AD pueden estar configuradas para replicarse:
* Solo a controladores de dominio en el mismo dominio.
* O a todos los controladores de dominio en el bosque.

Si están configuradas solo para su dominio, no se replican automáticamente a otro Tree Root, aunque esté en el mismo bosque.

#### 2. **Problemas de permisos o derechos de replicación.**

Puede que no haya confianza (trust) configurada correctamente o permisos para replicar esas zonas.

#### 3. Configuración de replicación de Active Directory Sites and Services.

Si los sitios de AD no están bien configurados o la replicación entre sitios no es óptima, puede impactar la replicación DNS.

#### 4. Tipo de zona DNS

Si las zonas son primarias estándar o secundarias, se comportan diferente que las almacenadas en AD.

#### 5. Errores de configuración de redes, firewalls o puertos bloqueados.

La replicación de AD y DNS requiere puertos abiertos (RPC, LDAP, DNS, Kerberos, etc.).