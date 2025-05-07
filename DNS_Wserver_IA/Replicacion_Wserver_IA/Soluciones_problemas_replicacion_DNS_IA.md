# Soluciones posibles
---

#### 1. Revisar cómo están almacenadas las zonas
* Abre la consola DNS Manager.
* Clic derecho en una zona problemática > Properties > General.
* Verifica si dice **"AD-integrated"** (integrada en Active Directory).
* Si es así, revisa el apartado de Replication:

    * Cambia la opción a **"To all DNS servers in the forest"** (Todos los servidores DNS en el bosque), si quieres que pase entre Tree Roots.

#### 2. Verificar relaciones de confianza (Trusts)
Asegúrate de que hay una confianza bidireccional y transitable configurada entre ambos Tree Roots, si pertenecen a dominios distintos.

#### 3. Forzar la replicación de AD
Usa **repadmin /syncall /AdeP** para forzar la replicación entre los DCs.

#### 4. Exportar e importar zonas manualmente (si es necesario)
Si no quieres o no puedes modificar la configuración de AD, puedes:

Exportar la zona desde el primer DNS
```bash
dnscmd /zoneexport nombredelazona nombrearchivo.dns
Importarla manualmente en el segundo DNS creando una nueva zona y usando el archivo exportado.
```

#### 5. Verificar registros de eventos
Mira en Event Viewer (Visor de eventos) aqui suele aparecer el error específico que causó la falla.
* DNS Server Logs.
* Directory Service Logs.
* Replication Logs.

