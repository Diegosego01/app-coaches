# Fase 2: Descubrimiento

**Versión:** 0.1 · 2026-10-17
**Estado:** esperando respuestas de Diego

Cada pregunta trae una **propuesta** basada en lo hablado hasta ahora. Si estás de acuerdo, basta con responder "ok"; si no, escribe tu respuesta. Todo lo que quede sin confirmar se trata como *supuesto por confirmar* en los requisitos.

La Fase 1 (prototipo) se omite por ahora, por decisión de Diego del 2026-10-17.

## 1. Objetivo y usuarios

1. **¿Quiénes son los usuarios y qué puede hacer cada uno?**
   Propuesta: dos roles. El coach publica su perfil y acepta o rechaza solicitudes. El deportista busca, desliza y envía solicitudes. Una persona no puede tener los dos roles en la misma cuenta en la v1.
2. **¿Cómo sabremos que el proyecto fue un éxito?**
   Propuesta: en la prueba cerrada, 30 % de los deportistas activos consigue un match aceptado y 1 de cada 5 chats acaba en una sesión real.
3. **¿Qué especialidades entran en el lanzamiento?**
   Propuesta: 2 o 3 para empezar, por ejemplo entrenador de gimnasio, preparación física funcional y tenis. El resto (fisioterapia, psicología deportiva, nutrición) se abre después.

## 2. Datos

4. **¿Qué datos necesita el perfil de coach?**
   Propuesta: nombre, fotos (hasta 6), bio, especialidades, precio por sesión y por paquete, zona y radio de trabajo, lugar donde trabaja, modalidad (gimnasio, domicilio, aire libre, online), años de experiencia, títulos y certificaciones, disponibilidad.
5. **¿Qué datos necesita el perfil de deportista?**
   Propuesta: nombre, foto, edad, deporte y objetivo, nivel, zona aproximada, presupuesto y modalidad preferida.
6. **¿En qué país, moneda y zona horaria arrancamos?**
   Propuesta: un solo país y una sola moneda al inicio. Necesito que me digas cuál.
7. **¿Cómo se verifica que un coach tiene los títulos que dice?**
   Propuesta: el coach sube una foto del título y se revisa a mano antes de mostrar la insignia de verificado. Obligatorio para fisioterapia y psicología.

## 3. Funcionamiento y reglas

8. **¿Cómo funciona el match?**
   Propuesta: el deportista da like y el coach recibe una solicitud que acepta o rechaza. Solo con la solicitud aceptada se abre el chat.
9. **¿Qué pasa con los coaches a los que el deportista dio "pasar"?**
   Propuesta: no se vuelven a mostrar durante 30 días.
10. **¿Hay límite de likes por día?**
    Propuesta: no en la v1.
11. **¿Qué avisos se envían y por qué canal?**
    Propuesta: notificación push por solicitud nueva, solicitud aceptada y mensaje nuevo. Email solo para bienvenida y recuperación de cuenta.

## 4. Pantallas

12. **¿Qué es lo primero que ve cada usuario al abrir la app?**
    Propuesta: el deportista ve las tarjetas de coaches; el coach ve sus solicitudes pendientes.
13. **¿El coach necesita ver estadísticas en la v1?**
    Propuesta: no; solo el número de solicitudes recibidas. Las estadísticas van en la suscripción Pro más adelante.

## 5. Alcance y restricciones

14. **¿Qué dispositivos?**
    Propuesta: iPhone y Android. Sin versión web en la v1.
15. **¿Debe funcionar sin internet?**
    Propuesta: no. Sin conexión se muestra un aviso; solo se conservan los últimos chats ya cargados.
16. **¿Qué datos sensibles maneja y qué NO se guarda?**
    Propuesta: se guarda la ubicación aproximada (barrio), nunca la dirección exacta. No se guardan datos de pago en la v1. Edad mínima: 18 años, o 16 con aviso, por confirmar.
    **Respuesta de Diego (2026-10-18):** edad mínima 16 años. Entre 16 y 17 años la cuenta necesita la confirmación de un representante mayor de 18.
17. **¿Se conecta con otros sistemas?**
    Propuesta: login con Google y Apple, mapas para elegir la zona, y Supabase como backend. Sin pagos ni calendario en la v1.
18. **¿Hay fecha límite, presupuesto o servicios obligatorios?**
    Propuesta: presupuesto mínimo, usando planes gratuitos (Supabase, Expo) hasta el lanzamiento. Coste fijo conocido: Apple Developer 99 USD al año y Google Play 25 USD una vez.

## 6. Documentación

19. **¿En qué idioma van los documentos y la app?**
    Propuesta: documentos en español; la app en español en la v1.
20. **¿Para quién son los documentos?**
    Propuesta: para Diego y para cualquier desarrollador que se sume después.

## Documentos que se generan con estas respuestas

| Fase | Documento |
|---|---|
| 3 | `docs/03-requisitos-funcionales.md` (FR con criterios Dado / Cuando / Entonces) |
| 4 | `docs/04-requisitos-no-funcionales.md` (NFR medibles) |
| 5 | `docs/05-documento-funcional.md` (reglas, historias, casos de uso, casos borde, métricas, glosario) |
| 6 y 7 | `docs/06-arquitectura.md` (diagramas, stack, ADR y riesgos) |
| 8 | `docs/08-diseno-datos.md` y la primera migración |

## Puerta de salida de la fase

- [ ] Cada pregunta tiene respuesta o queda marcada como supuesto por confirmar.
