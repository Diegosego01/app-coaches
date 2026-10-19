# Fase 3: Requisitos funcionales

**Versión:** 0.4 · 2026-10-19 (credencial obligatoria para coaches y currículum opcional)
**Estado:** borrador para revisión de Diego
**Fuente:** [ficha de idea](00-ficha-idea.md) y [descubrimiento](02-descubrimiento.md) v1.0. Entre paréntesis se indica la pregunta del descubrimiento de la que sale cada requisito (P1 a P20).

**Prioridad (MoSCoW):** M = Debe (sin esto no hay lanzamiento) · S = Debería (importante, pero se puede lanzar sin ello) · C = Podría (si hay tiempo).

## Supuestos por confirmar

| # | Tema | Supuesto usado |
|---|---|---|
| A | País y moneda (P6) | **Confirmado por Diego el 2026-10-19:** lanzamiento en Valencia, Venezuela, con precios en dólares estadounidenses (USD), guardados en centavos. Zona horaria America/Caracas. |
| B | Especialidades de lanzamiento (P3) | Entrenador de gimnasio, preparación física funcional, tenis, pádel y fisioterapia (pádel y fisioterapia añadidas por Diego el 2026-10-19). El catálogo admite más sin cambiar la app. |
| C | Confirmación del representante (P16) | Se hace por email: el menor indica el email de su representante, que recibe un enlace para declarar que es mayor de 18 y autorizar la cuenta. |
| D | Revisión de títulos y reportes (P7) | La hace a mano una persona del equipo desde una herramienta interna mínima, no desde la app. |
| E | Cómo se comprueba la experiencia laboral (FR-33) | El coach adjunta una constancia o carta laboral, o da el contacto de una referencia; el equipo revisa el documento o llama a la referencia. |

## Fuera del alcance de la v1

Pagos y reservas dentro de la app, reseñas, feed social con publicaciones, videollamadas, planes de entrenamiento, versión web, estadísticas para el coach (más allá del contador de solicitudes), límite de likes, varios países o monedas, y una cuenta con los dos roles a la vez.

## 1. Cuenta y acceso

| ID | Requisito | P | Criterios de aceptación (Dado / Cuando / Entonces) |
|---|---|---|---|
| FR-01 | Registrarse con email y contraseña (P17) | M | Dado un email válido y una contraseña de al menos 8 caracteres, cuando me registro, entonces se crea la cuenta y recibo un email para confirmar mi dirección. Dado un email ya registrado, entonces se muestra "Este email ya tiene una cuenta" y no se crea otra. Dado una contraseña de menos de 8 caracteres, entonces se muestra el error y no se envía el formulario. |
| FR-02 | Entrar con Google o Apple (P17) | M | Dado que elijo Google o Apple, cuando autorizo el acceso, entonces entro a la app; si es la primera vez, se crea mi cuenta. Dado que cancelo la autorización, entonces vuelvo a la pantalla de inicio sin error. En iPhone, el botón de Apple aparece siempre que aparezca el de Google. |
| FR-03 | Elegir rol al registrarse (P1) | M | Dado que acabo de crear la cuenta, cuando elijo "Soy coach" o "Soy deportista", entonces paso a crear el perfil de ese rol. Dado que ya elegí un rol, entonces no puedo cambiarlo desde la app (solo creando otra cuenta). |
| FR-04 | Declarar fecha de nacimiento y aplicar la edad mínima (P16) | M | Dado que tengo 18 años o más, cuando ingreso mi fecha de nacimiento, entonces continúo sin pasos extra. Dado que tengo menos de 16, entonces se muestra que la edad mínima es 16 y no se crea el perfil. Dado que soy coach, entonces debo tener 18 años o más. |
| FR-05 | Autorización del representante para deportistas de 16 y 17 años (P16) | M | Dado que tengo 16 o 17 años, cuando ingreso el email de mi representante, entonces le llega un enlace para declarar que es mayor de 18 y autorizar la cuenta. Dado que el representante aún no autoriza, entonces puedo completar mi perfil pero no puedo dar like ni chatear, y veo el estado "Esperando autorización". Dado que el representante rechaza o el enlace caduca a los 7 días, entonces la cuenta sigue bloqueada y puedo reenviar la solicitud. Dado que pongo mi propio email como representante, entonces se rechaza. |
| FR-06 | Recuperar la contraseña (P11) | M | Dado un email registrado, cuando pido recuperar la contraseña, entonces recibo un enlace para crear una nueva. Dado un email no registrado, entonces se muestra el mismo mensaje genérico, sin revelar si la cuenta existe. |
| FR-07 | Cerrar sesión y eliminar la cuenta (P16) | M | Dado que estoy dentro, cuando cierro sesión, entonces vuelvo al inicio. Cuando elijo eliminar la cuenta y lo confirmo, entonces mi perfil deja de ser visible al instante y mis datos se borran, incluidas fotos y chats. |

## 2. Perfil de coach

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-08 | Crear el perfil de coach (P4) | M | Dado que soy coach, cuando completo nombre, al menos 3 fotos, al menos 1 especialidad, precio por sesión, zona de trabajo con radio en km, al menos 1 modalidad y años de experiencia, entonces mi perfil queda completo. Dado que falta alguno de esos campos, entonces se indica cuál y el perfil no aparece en el descubrimiento. Dado un precio de 0 o negativo, entonces se muestra el error. Además, el perfil solo aparece en el descubrimiento cuando tiene **al menos un título o certificación verificada (FR-10) o, si no tiene ninguno, al menos una experiencia laboral comprobada (FR-33)**; mientras tanto veo el estado "Pendiente de verificación". Bio, precio por paquete, lugar de trabajo y disponibilidad son opcionales. |
| FR-09 | Subir y ordenar fotos (P4) | M | Dado que subo fotos, cuando tengo entre 3 y 6, entonces se guardan y puedo elegir cuál es la principal. Dado que intento borrar una foto y me quedarían menos de 3, entonces se impide y se me pide subir otra antes. Dado que intento subir una séptima, entonces se impide. Dado un archivo que no es imagen o pesa más de 10 MB, entonces se rechaza con un mensaje. |
| FR-10 | Verificar cada certificación (P7) | M | Dado que añado una certificación a mi perfil, cuando subo la foto del documento, entonces queda "En revisión" y no se muestra a los deportistas. Cuando el equipo la aprueba, entonces aparece en mi perfil como verificada, y con la primera aprobada mi perfil muestra la insignia de verificado. Dado que la rechaza, entonces recibo el motivo, no se muestra y puedo subir otra. Dado que añado una certificación sin documento, entonces no se puede guardar. En ningún caso se muestra una certificación no verificada, y las fotos de los documentos nunca son visibles para otros usuarios. |
| FR-11 | Verificación obligatoria para especialidades sanitarias (P7) | M | Dado que mi especialidad es fisioterapia o psicología deportiva, cuando mi título no está aprobado, entonces mi perfil no aparece en el descubrimiento para esa especialidad y veo el estado "En revisión". Para estas especialidades la experiencia laboral comprobada no sustituye al título. |
| FR-33 | Registrar experiencia laboral comprobable (P4, P7) | M | Dado que soy coach, cuando añado una experiencia con lugar, cargo, fecha de inicio y fin (o "actual") y un comprobante (constancia o carta laboral, o el nombre y teléfono de una referencia), entonces queda "En revisión" y no se muestra. Cuando el equipo la comprueba, entonces aparece en mi perfil como experiencia verificada. Dado que la rechaza, entonces recibo el motivo y puedo corregirla. Dado que falta el comprobante o la fecha de inicio es posterior a la de fin, entonces no se puede guardar. |
| FR-34 | Subir el currículum de forma opcional (P4) | M | Dado que soy coach, cuando subo mi currículum en PDF de hasta 10 MB, entonces queda en mi perfil y puedo reemplazarlo o borrarlo. Dado un archivo que no es PDF o pesa más de 10 MB, entonces se rechaza con un mensaje. Dado que no subo currículum, entonces mi perfil puede completarse igual. Al subirlo se me recuerda no incluir mi dirección ni documentos de identidad. El currículum no cuenta como verificación (FR-08) y se muestra como "Documento aportado por el coach". |
| FR-12 | Editar y pausar el perfil (P4) | M | Dado que edito cualquier campo, cuando guardo, entonces los cambios se ven en el descubrimiento. Cuando pauso el perfil, entonces deja de mostrarse a deportistas nuevos, pero conservo mis solicitudes y chats. |

## 3. Perfil de deportista

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-13 | Crear el perfil de deportista (P5) | M | Dado que soy deportista, cuando completo nombre, deporte u objetivo, nivel y zona aproximada, entonces puedo empezar a descubrir coaches. Foto, presupuesto y modalidad preferida son opcionales. Dado que falta un campo obligatorio, entonces se indica cuál. |
| FR-14 | Elegir la zona en un mapa (P16, P17) | M | Dado que elijo mi zona en el mapa o permito la ubicación del teléfono, entonces se guarda solo una ubicación aproximada (ver NFR de privacidad). Dado que no doy permiso de ubicación, entonces puedo escribir mi barrio o ciudad. |

## 4. Descubrimiento de coaches

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-15 | Ver tarjetas de coaches cercanos (P8, P12) | M | Dado que soy deportista con perfil completo, cuando abro la app, entonces veo una tarjeta por coach con foto principal, nombre, especialidad, precio por sesión, distancia en km, modalidades e insignia si está verificado. Solo aparecen coaches con perfil completo, no pausado, dentro de mi distancia máxima y cuya zona de trabajo me cubre si ofrecen domicilio. |
| FR-16 | Filtrar coaches (P3, P5) | M | Dado que abro los filtros, cuando elijo especialidad, distancia máxima (1 a 50 km), rango de precio o modalidad, entonces las tarjetas se actualizan. Por defecto: mi deporte u objetivo, 10 km y sin límite de precio. Dado que ningún coach cumple los filtros, entonces veo "No hay coaches con estos filtros" y un botón para ampliarlos. |
| FR-17 | Dar like a un coach (P8) | M | Dado una tarjeta, cuando deslizo a la derecha o toco el botón de like, entonces se envía una solicitud al coach y pasa la siguiente tarjeta. Dado que ya le envié una solicitud pendiente o aceptada, entonces ese coach no vuelve a aparecer. Dado que soy menor sin autorización (FR-05), entonces el like se bloquea con un aviso. |
| FR-18 | Pasar a un coach (P9) | M | Dado una tarjeta, cuando deslizo a la izquierda o toco el botón de pasar, entonces pasa la siguiente tarjeta y ese coach no se me vuelve a mostrar durante 30 días, salvo que yo elija verlo otra vez desde "Ver coaches anteriores" (FR-20). |
| FR-19 | Ver el perfil completo del coach (P4) | M | Dado una tarjeta, cuando la toco, entonces veo todas las fotos, bio, especialidades, precios, lugar de trabajo, modalidades, años de experiencia, títulos y certificaciones verificados, experiencias laborales verificadas, disponibilidad y, si lo subió, un botón para ver su currículum, con los botones de like y pasar. |
| FR-20 | Fin de las tarjetas y volver a ver coaches pasados | M | Dado que no quedan coaches por mostrar, entonces veo un mensaje que lo explica, sugiere ampliar la distancia o los filtros y ofrece el botón "Ver coaches anteriores". Cuando lo toco, entonces vuelven a aparecer como tarjetas los coaches a los que di "pasar" y que cumplen mis filtros actuales, del más reciente al más antiguo, y puedo darles like o pasar de nuevo. El botón aparece **solo** cuando ya vi todos los perfiles de coaches disponibles en mi zona con mis filtros actuales; mientras quede algún coach nuevo por mostrar, no está disponible en ninguna parte de la app. Dado que no pasé a ningún coach, entonces el botón no aparece. Los coaches con solicitud pendiente o aceptada, o bloqueados, nunca vuelven a aparecer. |
| FR-21 | Deshacer el último pasar | C | Dado que acabo de pasar a un coach, cuando toco deshacer, entonces vuelve su tarjeta. Solo se puede deshacer el último. |

## 5. Solicitudes y match

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-22 | Ver las solicitudes recibidas (P12, P13) | M | Dado que soy coach, cuando abro la app, entonces veo mis solicitudes pendientes, más recientes primero, con foto, nombre, objetivo, nivel, distancia aproximada y la marca "Menor de edad" si corresponde. Veo también el número total de solicitudes recibidas. |
| FR-23 | Aceptar o rechazar una solicitud (P8) | M | Dado una solicitud pendiente, cuando la acepto, entonces se crea el match y se abre un chat con el deportista. Cuando la rechazo, entonces desaparece de mi lista y el deportista no recibe aviso del rechazo. Dado que la solicitud lleva 30 días sin respuesta, entonces caduca y el coach puede volver a aparecerle al deportista. |
| FR-24 | Ver mis solicitudes enviadas | S | Dado que soy deportista, cuando abro mis solicitudes, entonces veo las pendientes y las aceptadas. Las rechazadas y caducadas se muestran como "Sin respuesta". |

## 6. Chat

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-25 | Chatear tras el match (P8) | M | Dado un match, cuando escribo un mensaje de texto y lo envío, entonces la otra persona lo ve en la conversación sin recargar. Dado que no hay match aceptado, entonces no existe forma de escribir a esa persona. Dado un mensaje vacío o de más de 2.000 caracteres, entonces no se envía. |
| FR-26 | Ver la lista de conversaciones (P12) | M | Dado que tengo matches, cuando abro "Chats", entonces veo cada conversación con el último mensaje, la hora y el número de mensajes sin leer. |
| FR-27 | Ver los últimos chats sin conexión (P15) | S | Dado que no tengo internet, cuando abro un chat ya cargado, entonces veo sus mensajes y un aviso de que no hay conexión. Dado que intento enviar un mensaje sin conexión, entonces se muestra que no se pudo enviar. |

## 7. Avisos

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-28 | Notificaciones push (P11) | M | Dado que acepté recibir notificaciones, entonces recibo una cuando: (coach) llega una solicitud nueva; (deportista) un coach acepta mi solicitud; (ambos) llega un mensaje nuevo y no tengo ese chat abierto. Dado que desactivo un tipo de aviso en Ajustes, entonces dejo de recibirlo. |
| FR-29 | Emails de cuenta (P11) | M | Recibo un email al confirmar la cuenta (bienvenida), al recuperar la contraseña y, si soy representante, al pedir la autorización (FR-05). No se envían emails de marketing en la v1. |

## 8. Seguridad y moderación

| ID | Requisito | P | Criterios de aceptación |
|---|---|---|---|
| FR-30 | Reportar a un usuario (P16) | M | Dado un perfil o un chat, cuando reporto al usuario eligiendo un motivo (perfil falso, acoso, contenido inapropiado, otro), entonces el reporte llega al equipo y veo una confirmación. |
| FR-31 | Bloquear a un usuario (P16) | M | Dado un perfil o un chat, cuando bloqueo al usuario, entonces ninguno de los dos vuelve a ver al otro en tarjetas, solicitudes ni chats, y la conversación se cierra. |
| FR-32 | Herramienta interna de moderación (P7) | M | Dado que soy del equipo, cuando abro la herramienta interna, entonces veo los títulos, certificaciones y experiencias laborales pendientes y los reportes, y puedo aprobar o rechazar cada uno con un motivo y suspender una cuenta. Dado que suspendo una cuenta, entonces su perfil deja de mostrarse y no puede entrar a la app. |

## Puerta de salida de la fase

- [x] Cada requisito se puede probar con un sí o un no.
- [ ] Diego revisa la lista y las prioridades.
- [x] Diego confirma el supuesto A (país y moneda).
