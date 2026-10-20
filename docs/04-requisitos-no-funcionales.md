# Fase 4: Requisitos no funcionales

**Versión:** 0.2 · 2026-10-20 (cambios del marco legal)
**Estado:** borrador para revisión de Diego
**Fuente:** [requisitos funcionales](03-requisitos-funcionales.md) y [descubrimiento](02-descubrimiento.md) v1.0.

Cada requisito tiene un número o una prueba concreta. Lo que todavía no se puede verificar está marcado **Por confirmar**.

| ID | Categoría | Requisito y criterio medible |
|---|---|---|
| NFR-01 | Rendimiento | Dado un teléfono de gama media con 4G, cuando el deportista abre la app con sesión iniciada, entonces la primera tarjeta aparece en menos de 3 segundos. |
| NFR-02 | Rendimiento | Dado el mazo cargado, cuando deslizo una tarjeta, entonces la animación va a 60 cuadros por segundo y la siguiente tarjeta aparece en menos de 300 ms (se precargan al menos 5 tarjetas). |
| NFR-03 | Rendimiento | Dado dos usuarios con conexión, cuando uno envía un mensaje, entonces el otro lo ve en menos de 2 segundos con el chat abierto. |
| NFR-04 | Rendimiento | Dado el aviso de una solicitud, aceptación o mensaje, entonces la notificación push sale del servidor en menos de 10 segundos. |
| NFR-05 | Usabilidad | Una persona nueva completa el registro y su perfil de deportista en menos de 3 minutos, y el de coach en menos de 8 minutos. Se verifica con al menos 5 personas en la prueba cerrada. |
| NFR-06 | Usabilidad | Todos los errores dicen qué pasó y cómo corregirlo, en español y sin códigos técnicos. |
| NFR-07 | Accesibilidad | Contraste de texto WCAG 2.1 AA (4,5:1), áreas táctiles de al menos 44 × 44 px, etiquetas para VoiceOver y TalkBack en todos los botones (incluidos like y pasar) y soporte del tamaño de texto del sistema hasta 200 % sin cortar contenido. |
| NFR-08 | Compatibilidad | Funciona en iOS 16 o superior y Android 10 o superior, en pantallas de 320 a 430 px de ancho. **Por confirmar** con datos de uso del país elegido. |
| NFR-09 | Privacidad | La ubicación del deportista se guarda redondeada a una cuadrícula de unos 1 km, y la distancia se muestra en km enteros. Nunca se guardan ni se muestran coordenadas exactas ni direcciones. |
| NFR-10 | Privacidad | Se piden solo los datos de los requisitos funcionales. No se guardan datos de pago, documentos de identidad ni contraseñas en texto (las gestiona el servicio de autenticación). Las fotos de títulos son privadas y solo las ve el equipo de moderación. |
| NFR-11 | Privacidad | Las notificaciones push muestran el nombre de quien escribe, pero no el contenido del mensaje en la pantalla bloqueada. |
| NFR-12 | Privacidad y legal | Antes de publicar en tiendas existen política de privacidad y términos de uso conformes a la normativa venezolana (Constitución arts. 28 y 60, sentencia TSJ 1318/2011, Ley Especial contra los Delitos Informáticos, LOPNNA y Ley contra el Odio; ver [marco legal](marco-legal.md)), con la regla de menores de 16 y 17 años (FR-05). Un abogado venezolano revisa los términos, la política de privacidad y el flujo de menores antes de publicar (L10). |
| NFR-13 | Seguridad | El 100 % de las tablas tiene reglas de acceso por fila. Se verifica con pruebas automáticas usando dos cuentas: un usuario no puede leer chats, solicitudes ni datos privados de otro. |
| NFR-14 | Seguridad | La app solo contiene claves públicas. Las claves de servicio y de terceros viven como secretos del servidor y nunca están en el repositorio. |
| NFR-15 | Seguridad | Máximo 200 likes por hora por cuenta y 5 intentos de inicio de sesión fallidos por minuto, para frenar bots. No es un límite visible para el uso normal. |
| NFR-16 | Seguridad | La herramienta de moderación (FR-32) solo es accesible para cuentas del equipo con verificación en dos pasos activada. |
| NFR-17 | Fiabilidad | Disponibilidad mensual del backend de al menos 99,5 %, según el panel del proveedor. Si el servidor falla, la app muestra un aviso y no se cierra. |
| NFR-18 | Respaldo y recuperación | Copia de seguridad diaria de la base de datos con 7 días de retención, y al menos una restauración probada antes del lanzamiento. **Por confirmar**: el plan gratuito de Supabase podría no incluir copias descargables. |
| NFR-19 | Moderación | Los reportes por odio o violencia se atienden y el contenido se retira en menos de 6 horas, también fines de semana. Los reportes que involucran a menores se revisan en menos de 24 horas, el resto en menos de 48 horas, y cada título, certificación o experiencia en menos de 72 horas. Se mide desde la herramienta interna (L6). |
| NFR-20 | Mantenibilidad | Código en TypeScript con verificación estricta. Cada cambio de base de datos es una migración versionada. Las reglas de negocio (match, caducidad, edad, distancia) tienen pruebas automáticas. |
| NFR-21 | Mantenibilidad | Todos los textos de la app están en un único archivo de traducciones, para poder añadir otro idioma sin tocar las pantallas. |
| NFR-22 | Escalabilidad | La arquitectura soporta 5.000 usuarios registrados y 50.000 deslizamientos al día sin rediseño; solo puede requerir subir de plan en el proveedor. **Por confirmar** los límites del plan gratuito en la fase de arquitectura. |
| NFR-23 | Exactitud | Los precios se guardan en centavos enteros y se muestran con el formato de la moneda elegida. Las fechas sin hora (nacimiento) se guardan como texto AAAA-MM-DD. La distancia calculada no se desvía más de 1 km del valor real. |
| NFR-24 | Conformidad con tiendas | Cumple las normas de App Store y Google Play que aplican: inicio de sesión con Apple si hay Google, eliminación de cuenta dentro de la app (FR-07), herramientas de reporte y bloqueo (FR-30, FR-31) y política de privacidad enlazada. |
| NFR-25 | Costes | Hasta el lanzamiento se usan solo planes gratuitos, salvo las cuentas de desarrollador (Apple 99 USD al año y Google Play 25 USD una vez). Cualquier servicio de pago adicional se aprueba antes. |

## Puerta de salida de la fase

- [x] Cada NFR tiene un número o una prueba concreta.
- [ ] Diego revisa los valores (tiempos, límites y versiones mínimas).
- [ ] Se resuelven los "Por confirmar" en la fase de arquitectura o al elegir país.
