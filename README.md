# GymPilot 🏋️

![.NET](https://img.shields.io/badge/.NET-10-512BD4?logo=dotnet&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?logo=csharp&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?logo=microsoftsqlserver&logoColor=white)
![Estado](https://img.shields.io/badge/estado-en%20planificaci%C3%B3n-yellow)

GymPilot es una plataforma integral para la gestión de gimnasios, con aplicación web (Blazor WebAssembly), API RESTful y aplicación de escritorio Windows Forms, desarrollada con .NET 10 y C#.

> Proyecto académico desarrollado en el marco del **Seminario I** de la carrera **Analista Universitario en Sistemas**.

## Tabla de Contenidos

- [Descripción](#descripción)
- [Características](#características)
- [Roles y permisos](#roles-y-permisos)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Base de Datos](#base-de-datos)
- [Equipo](#equipo)

## Descripción

GymPilot centraliza la operación diaria de un gimnasio: socios, membresías, pagos, asistencia, rutinas de entrenamiento, clases grupales y reportes. El sistema ofrece tres roles (Administrador, Entrenador y Cliente) y cada uno cuenta con una interfaz adecuada a sus tareas:

- **Aplicación web:** orientada a clientes y entrenadores.
- **Aplicación de escritorio:** orientada a la administración y la recepción del gimnasio.
- **API REST:** núcleo común que consumen ambas aplicaciones.

## Características

- **Gestión de usuarios y roles:** alta, edición, baja lógica y cambio de rol.
- **Membresías y suscripciones:** planes configurables, control de vigencia, renovación y vencimiento.
- **Pagos:** registro de pagos con método y comprobante, historial y deudas.
- **Asistencia:** check-in validando que el cliente tenga una suscripción vigente.
- **Ejercicios y rutinas:** catálogo de ejercicios, rutinas por días con series y repeticiones, y asignación a clientes.
- **Clases grupales:** cupos, salas, horarios y reservas.
- **Seguimiento del progreso:** medidas corporales, evolución y notas del entrenador.
- **Dashboards y reportes en PDF:** ingresos, morosidad, asistencia y retención.
- **Notificaciones y auditoría** de acciones críticas.
- **Autenticación JWT** con autorización por roles.

## Roles y permisos

| Funcionalidad | Administrador | Entrenador | Cliente |
|---|:---:|:---:|:---:|
| Gestionar usuarios y roles | ✅ | ❌ | ❌ |
| Gestionar planes, suscripciones y pagos | ✅ | ❌ | ❌ |
| Registrar asistencia (check-in) | ✅ | ✅ | Autocheck-in opcional |
| Crear ejercicios y rutinas | ✅ | ✅ | ❌ |
| Asignar rutinas a clientes | ✅ | ✅ (sus clientes) | ❌ |
| Ver rutina asignada | ✅ | ✅ | ✅ (propia) |
| Registrar medidas y progreso | ✅ | ✅ | ✅ (propias) |
| Crear y gestionar clases | ✅ | ✅ (propias) | ❌ |
| Reservar clases | ✅ | ❌ | ✅ |
| Ver reportes globales | ✅ | ❌ | ❌ |

## Tecnologías Utilizadas

### Backend

- **.NET 10 / ASP.NET Core:** framework principal
- **Entity Framework Core:** ORM para acceso a datos
- **SQL Server:** base de datos relacional
- **AutoMapper:** mapeo entre entidades y DTOs
- **FluentValidation:** validación de DTOs
- **BCrypt.NET:** hash de contraseñas
- **JWT:** autenticación basada en tokens
- **QuestPDF:** generación de reportes PDF
- **Swagger / OpenAPI:** documentación de la API

### Frontend

- **Blazor WebAssembly:** aplicación web SPA
- **MudBlazor:** biblioteca de componentes UI
- **Windows Forms:** aplicación de escritorio

### Calidad y herramientas

- **xUnit y Moq:** pruebas unitarias
- **Git y GitHub:** control de versiones y colaboración


## Base de Datos

El proyecto utiliza **SQL Server** con **Entity Framework Core**. El modelo se organiza en cuatro grandes módulos:

- **Usuarios y acceso:** `Users`, `ClientProfiles`, `TrainerProfiles`
- **Membresías y pagos:** `MembershipPlans`, `Subscriptions`, `Payments`, `Attendances`
- **Entrenamiento y seguimiento:** `MuscleGroups`, `Exercises`, `Routines`, `RoutineDays`, `RoutineExercises`, `ClientRoutines`, `BodyMeasurements`, `TrainerNotes`
- **Clases y sistema:** `Rooms`, `GroupClasses`, `ClassBookings`, `Notifications`, `AuditLogs`

### Reglas de integridad principales

- Email único por usuario.
- Un cliente no puede tener dos suscripciones activas superpuestas.
- No se puede registrar asistencia sin una suscripción vigente.
- Las reservas no pueden superar el cupo de la clase.
- Borrado lógico en usuarios, planes y ejercicios para conservar el historial.

## Equipo

- **Nicolas Dinolfo**
- **Juan Schiavoni** — [@JuanSchiavoni](https://github.com/JuanSchiavoni)
