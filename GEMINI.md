# Reglas del proyecto Amigo Invisible

- Aplicación web de un solo archivo (`index.html`) publicada en GitHub Pages (`marc-post/amigo-invisible`) y conectada a Firebase Firestore.
- **PROHIBIDO modificar** la configuración de Firebase (`projectId: amigo-invisible-8a0c3`, `apiKey`), el `appId` (`amigo-invisible-navidad-app`) ni borrar/sobrescribir el documento histórico `artifacts/amigo-invisible-navidad-app/public/data/app_state/estado_global` (se mantiene intacto como respaldo de solo lectura para migración).
- Modelo multi-organizador en Firestore bajo `artifacts/amigo-invisible-navidad-app/public/data`:
  - `draws/{drawId}`: 1 documento independiente por sorteo con campo `ownerId` (UID de Google del organizador). Los organizadores inician sesión con Google Sign-In y solo listan/gestionan sus propios sorteos; los invitados acceden por `?s={drawId}` con sesión anónima y PIN de 4 dígitos.
  - `app_config/avatars`: catálogo global de avatares compartido (edición reservada a `SUPER_ADMIN_EMAILS`).
  - `avatar_requests/{reqId}`: solicitudes de nuevos avatares enviadas por participantes.
- **PROHIBIDO cambiar** la clave local `MY_BAG_KEY = 'amigo_invisible_mi_mochila_v3'`.
- **Nunca** sobrescribir Firestore con datos de ejemplo al iniciar la app ni antes de recibir el primer snapshot real de la nube.
- Cualquier funcionalidad nueva debe ser 100 % retrocompatible con los sorteos y participantes ya guardados en Firestore.
- Haz siempre ediciones mínimas y quirúrgicas sobre `index.html`, sin reescribir el archivo completo innecesariamente.
