# Bitácora de Trading

App personal de bitácora y análisis de operaciones.
Solo código: tus datos no viven en este repositorio.

## Dónde se guardan los datos

- **Sin sesión:** solo en el navegador donde usas la app (localStorage).
- **Con sesión de Google (opcional, en Ajustes → Sincronización):** además se
  sincronizan con Firestore (Firebase, plan gratuito) entre todos tus dispositivos.
  - Cada trade es un documento en `users/{uid}/trades/{id}`; los ajustes van en `users/{uid}/meta/settings`.
  - El precio en vivo, el escaneo de velas y la preferencia de animaciones se quedan en cada dispositivo.
  - Los datos de demostración nunca se suben.
  - La primera vez que inicias sesión en un dispositivo, la app descarga un respaldo JSON
    y, si la nube ya tiene datos, pregunta antes de combinar. localStorage nunca se borra.

## Seguridad

Las reglas de [`firestore.rules`](firestore.rules) solo dejan entrar a una cuenta de Google
(tu correo, que se escribe directamente en la consola de Firebase, no en este repositorio).
La configuración de Firebase dentro de `index.html` es pública por diseño; lo que protege
los datos son esas reglas.
