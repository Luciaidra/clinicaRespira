# Respira: prototipo de telerrehabilitación pulmonar

Prototipo navegable (demo para que el cliente lo apruebe) de un sistema web de telerrehabilitación y seguimiento de pacientes para un centro de rehabilitación pulmonar. Lo hace Lucia para un cliente. Comunicación en español rioplatense (voseo); la usuaria prefiere instrucciones **paso a paso, de a uno**, esperando su confirmación.

El detalle funcional (roles, recorrido de demo, qué está simulado, stack planeado y normativa) está en `README.md`: leerlo primero.

## Estado actual
- Prototipo **publicado y listo para mostrar**: https://clinicarespira.vercel.app/
- **Falta que el cliente lo vea y lo apruebe.** Si acepta y se concreta, se desarrolla el sistema real a fondo, con los datos personalizados de la clínica (nombre, sede, profesionales, logo, etc.).

## Dónde está todo
- **Código:** `index.html` (un solo archivo con HTML, CSS y JavaScript, sin dependencias ni compilación). Los datos son ficticios y se guardan en `localStorage`; el botón "Reiniciar demo" vuelve al estado inicial.
- **Carpeta:** `Escritorio\CLINICA RESPIRA` (antes se llamaba `clinicaRespira`).
- **GitHub:** https://github.com/Luciaidra/clinicaRespira (rama `main`; primer commit `a47500b`). Esta carpeta es un repo git con `origin` configurado; la PC ya tiene las credenciales de GitHub guardadas.
- **Publicación:** en **Vercel**, importando el repo de GitHub (Framework Preset: Other, sin build). Link: https://clinicarespira.vercel.app/

## Roles del demo
Selector "Ver como" en la parte superior: Paciente, Neumonóloga, Kinesiólogo y Recepción. Hay alertas de seguridad (por ejemplo, SpO₂ 86% genera un aviso que aparece en la bandeja del kinesiólogo) y turnos virtuales con un enlace de Google Meet simulado.

## Próximo paso (si el cliente aprueba)
1. Pedirle a la clínica los datos reales para personalizar: nombre y logo, sede/dirección, profesionales, obras sociales, ejercicios propios y videos.
2. Desarrollar el sistema real con el stack del README: Angular 18+ y ASP.NET Core 8 (Clean Architecture), EF Core, Identity + JWT, Google Calendar API para Meet y Hangfire.
3. Contemplar las leyes 26.529 y 25.326 y la Resolución 581/2022.
