# Contexto del proyecto: App de coaches y deportistas

## Qué es
App móvil (iPhone y Android) que combina red profesional y descubrimiento tipo Tinder. Los coaches (gimnasio, tenis, preparación física funcional, fisioterapia, psicología deportiva, etc.) publican su perfil con precio, zona, modalidad y currículum. Los deportistas deslizan tarjetas de coaches cercanos: like envía una solicitud y, si el coach la acepta, se abre un chat. Idioma: español. Lanzamiento en Valencia, Venezuela; precios en USD; zona horaria America/Caracas.

## Estado actual (octubre de 2026)
- Hecho: plan de arranque e investigación (2026-10-16), ficha de idea (2026-10-17), descubrimiento cerrado (2026-10-19), requisitos funcionales FR-01 a FR-33 y no funcionales NFR-01 a NFR-25 en borrador (2026-10-19).
- Pendiente: revisión de requisitos por Diego; luego documento funcional, arquitectura y diseño de datos. No se programa todavía.
- Reglas ya decididas: like = solicitud que el coach acepta; "pasar" oculta al coach 30 días; solicitudes caducan a los 30 días; edad mínima 16 años, y de 16 a 17 con autorización por email de un representante mayor de 18; coaches mayores de 18. Especialidades de lanzamiento: gimnasio, preparación física funcional, tenis, pádel y fisioterapia. Toda certificación y experiencia se verifica a mano antes de mostrarse. Un coach solo aparece si tiene al menos un título o certificación verificada o, si no, una experiencia laboral comprobada; los fisioterapeutas siempre necesitan el título.

## Stack (propuesto, se confirma en la fase 6–7)
- App: React Native + Expo (TypeScript), tarjetas con rn-swiper-list.
- Backend: Supabase (Postgres con PostGIS, Auth, Storage, Realtime).
- Avisos: Expo Push Notifications; email con Brevo.

## Estructura
```
README.md        estado del proyecto por fases
CONTEXTO.md      este archivo
docs/            un documento por fase (00-ficha-idea, 02-descubrimiento, ...)
```

## Cómo funciona
Por definir en la arquitectura (fase 6).

## Modelo de datos
Por definir en el diseño de datos (fase 8).

## Seguridad
Reglas previstas: Row Level Security en todas las tablas, ubicación del deportista solo aproximada, sin datos de pago en la v1, sin claves privadas en el repositorio.

## Reglas de trabajo
- Una fase, un documento; no se avanza sin cerrar la puerta de salida de la fase anterior.
- Las dudas se preguntan; lo asumido se marca "Supuesto por confirmar".
- Los requisitos llevan criterios Dado / Cuando / Entonces.
- Un requisito a la vez en la construcción, con pruebas y aprobación antes del commit.
- Dinero en centavos enteros; fechas como texto AAAA-MM-DD.

## Comandos
Aún no hay código.

## Servicios externos
Por configurar: Supabase, Expo/EAS, Apple Developer, Google Play. Nunca poner claves privadas aquí.

## Referencias
- Plan de arranque e investigación: https://claude.ai/code/artifact/e454c190-0e27-4b3d-a9b4-d0bc4e50b068
