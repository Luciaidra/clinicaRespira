# Respira · Telerrehabilitación pulmonar

Prototipo navegable de un sistema web de telerrehabilitación y seguimiento de pacientes para un centro de rehabilitación pulmonar. Sirve para validar el diseño y los flujos con el cliente antes de desarrollar el sistema real.

> **Estado:** prototipo de demostración con datos de ejemplo. No guarda información en un servidor ni maneja datos reales de pacientes.

## Cómo verlo

- **En tu computadora:** descargá el repositorio y abrí `index.html` con doble clic. No requiere instalar nada.
- **En la web:** si GitHub Pages está activado, el demo queda publicado en `https://<tu-usuario>.github.io/<nombre-del-repo>/`.

Arriba de la pantalla, el selector **"Ver como"** cambia entre los cuatro roles. Cada vista tiene una guía de "Qué probar".

## Roles y funcionalidades

| Rol | Qué puede hacer |
|---|---|
| **Paciente** | Ver su próximo turno y unirse a la videollamada de Google Meet (se habilita 10 minutos antes), ver los ejercicios del día, registrar Borg y saturación después de cada ejercicio, ver su evolución y sus turnos. |
| **Neumonóloga** | Agenda del día, ficha clínica con gráficos de SpO₂ y test de marcha de 6 minutos, cargar evaluaciones pulmonares (calcula FEV1/FVC y la clasificación GOLD), prescribir el plan de tratamiento con umbrales de seguridad y escribir notas de evolución. |
| **Kinesiólogo** | Bandeja con alertas domiciliarias y planes sin rutina, biblioteca de ejercicios con filtros, asignación de ejercicios con series, repeticiones y frecuencia, y notas cruzadas con neumonología. |
| **Recepción** | Agenda por profesional, alta de turnos presenciales y virtuales (con enlace de Meet generado), control de superposición de horarios y alta de pacientes. No accede a la historia clínica. |

### Recorrido sugerido para una demo

1. Como **Paciente**, registrá un ejercicio con saturación de **86%**: aparece el aviso de seguridad.
2. Cambiá a **Kinesiólogo**: la alerta ya figura en la bandeja.
3. Como **Recepción**, creá un turno virtual y mirá el enlace de Meet generado.

## Qué está simulado

- **Google Meet:** el botón abre una sala nueva de Meet. En el sistema real, cada turno virtual tiene su sala, creada automáticamente con la API de Google Calendar.
- **Videos de ejercicios:** se reemplazan por una animación que guía el ritmo respiratorio.
- **Datos:** son ficticios y los cambios se guardan solo en el navegador de quien usa el demo (`localStorage`). El botón **Reiniciar demo** vuelve al estado inicial.
- **Notificaciones** (emails, recordatorios, invitaciones): se muestran como mensajes en pantalla.

## Tecnología del prototipo

Un único archivo `index.html` con HTML, CSS y JavaScript, sin dependencias ni paso de compilación. Las tipografías se cargan desde Google Fonts.

## Stack planeado para el sistema real

| Capa | Tecnología |
|---|---|
| Frontend | Angular 18+ (componentes standalone, Signals) |
| Backend | ASP.NET Core 8 Web API con Clean Architecture |
| Persistencia | Entity Framework Core 8 sobre SQL Server o PostgreSQL |
| Identidad | ASP.NET Core Identity + JWT con roles |
| Videollamadas | Google Calendar API con `conferenceData` (Google Meet) |
| Videos | Almacenamiento privado (Azure Blob o S3) con URLs firmadas |
| Tareas programadas | Hangfire (recordatorios de turnos) |

Modelo de datos principal: `Pacientes`, `Profesionales`, `Especialidades`, `Turnos`, `EvaluacionesPulmonares`, `PlanesTratamiento`, `Ejercicios`, `EjerciciosAsignados`, `RegistrosEjecucion` y `NotasEvolucion`.

## Normativa a contemplar (Argentina)

- Ley 26.529 de Derechos del Paciente: historia clínica inalterable (las notas no se editan, se agregan correcciones).
- Ley 25.326 de Protección de Datos Personales.
- Resolución 581/2022 del Ministerio de Salud sobre teleasistencia: consentimiento informado para telemedicina.
