# Diagnóstico rápido que te recomiendo hacer
---
* repadmin /showrepl
* dcdiag /test:DNS
* dnslint

### 1. repadmin /showrepl
Este comando muestra el **estado de la replicación de Active Directory.**
**Te dice**
* Entre qué controladores de dominio se está replicando.
* Qué particiones de AD (naming contexts) se están replicando.
* Cuándo fue la última replicación exitosa.
* Si hay errores de replicación (como problemas de conexión, autenticación, etc.).
* Si la replicación de Active Directory está fallando, las zonas DNS almacenadas en AD tampoco se van a replicar.
* Puedes ver si hay errores entre el SERVER 1 y SERVER 2, o si solo afecta ciertas particiones.
* También verás si el problema es puntual (solo DNS) o global (todo AD está fallando).

### 2. dcdiag /test:DNS
Este comando corre una batería de pruebas específicas sobre el DNS configurado en el servidor.
**Chequea**
* La correcta configuración de los registros de servicio (SRV).
* Si el servidor DNS responde correctamente.
* Problemas de configuración de zonas y delegaciones.
* Integridad del DNS vinculado a Active Directory.
* Detecta problemas en la configuración del DNS que impedirían su replicación o correcto funcionamiento.
* Si faltan registros vitales (como _msdcs, _sites, _tcp, _udp) que AD usa para replicarse, aquí lo verás.
También indica si hay problemas de permisos en las zonas DNS integradas.

### 3. dnslint
Este es una herramienta más especializada (más antigua pero potente) que ayuda a:

* Diagnosticar problemas de resolución DNS.
* Verificar registros SRV de AD, muy importantes para la localización de servicios como DCs.
* Validar replicación de zonas DNS de manera más profunda.
* Puedes usarlo para validar que los servidores DNS en SERVER 1 y SERVER 2 pueden resolver los registros esenciales de AD.

Si no se resuelven correctamente, es una causa directa de problemas de replicación de DNS y Active Directory.