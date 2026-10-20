# Marco legal y normas de las tiendas

**Versión:** 0.1 · 2026-10-20
**Estado:** investigación inicial para revisión de Diego
**Alcance:** lanzamiento en Valencia, Venezuela, con usuarios desde 16 años, publicación en App Store y Google Play.

> **Aviso:** esto es una investigación hecha con fuentes públicas, no asesoría legal. Antes de publicar la app, la política de privacidad, los términos de uso y el flujo de menores deben revisarse con un abogado venezolano. Donde no pude abrir el texto oficial de una norma, lo indico.

## Resumen

1. **Venezuela no tiene una ley general de protección de datos.** Rigen los artículos 28 y 60 de la Constitución y los principios que fijó el Tribunal Supremo de Justicia (sentencia 1318 de 2011). En la práctica exigen consentimiento previo, informado y revocable; usar los datos solo para lo que se dijo; guardarlos de forma segura y permitir consultarlos, corregirlos y borrarlos.
2. **Usar o divulgar datos personales sin consentimiento es delito** según la Ley Especial contra los Delitos Informáticos (2001), con penas de 2 a 6 años de prisión y multas también para la empresa.
3. **Los menores de 16 y 17 años** están protegidos por la LOPNNA. Nuestra regla de autorización del representante (FR-05) va en la línea correcta, pero conviene reforzar la protección de su imagen y su seguridad.
4. **La Ley contra el Odio (2017) obliga a las plataformas a retirar ciertos contenidos en 6 horas**, bajo pena de multa y bloqueo. Nuestro plazo actual de revisión de reportes (48 horas, NFR-19) no lo cumple para esos casos.
5. **Los fisioterapeutas deben tener el título universitario registrado y estar inscritos en su colegio.** Conviene verificar también el número de colegiado.
6. **Las tiendas exigen** política de privacidad, consentimiento, eliminación de cuenta dentro de la app y desde una web, términos aceptados antes de publicar contenido, reportar, bloquear, **filtrar contenido ofensivo** y un contacto publicado. Nos faltan el filtro, la web de eliminación y el contacto.

## Normas y su impacto en la app

| Norma | Qué exige | Impacto en la app |
|---|---|---|
| [Constitución, arts. 28 y 60](https://www.dlapiperdataprotection.com/?c=VE&t=law), y [sentencia TSJ 1318/2011](https://www.dlapiperdataprotection.com/?c=VE&t=law) | Derecho a acceder a los propios datos, saber para qué se usan y pedir su corrección o destrucción (habeas data). Consentimiento previo, libre, informado, inequívoco y revocable. Finalidad específica, datos no excesivos, conservación limitada, seguridad. No transferir datos a países sin protección similar. No hay autoridad de control ni obligación de notificar brechas. | Pedir consentimiento explícito al registrarse, con política de privacidad clara. Permitir ver y descargar mis datos, corregirlos y borrarlos. Informar que los servidores están fuera de Venezuela y pedir consentimiento para ello. |
| [Ley Especial contra los Delitos Informáticos](https://iin.oea.org/badaj/wp-content/uploads/2014/07/Ley_Especial_contra_Delitos_Inform%c3%a1ticos.pdf) (Gaceta 37.313, 30-10-2001) | Arts. 20 a 22: tomar, usar, modificar o divulgar datos personales o comunicaciones ajenas sin consentimiento, de 2 a 6 años de prisión y multa. Art. 5: la empresa responde con multa doble. Art. 24: usar la imagen de un menor con fines exhibicionistas o pornográficos, de 4 a 8 años. | Nunca compartir datos con terceros sin consentimiento. El equipo solo accede a lo necesario para moderar y queda registrado. Revisar fotos reportadas con prioridad, sobre todo si hay menores. |
| LOPNNA, Ley Orgánica para la Protección de Niños, Niñas y Adolescentes (Gaceta 5.933 Extraordinario, 2007) | Protección integral de menores de 18 años, incluida su privacidad e imagen. No pude abrir el texto oficial; el detalle de artículos debe confirmarlo el abogado. | Mantener FR-05 (autorización del representante). Guardar la prueba de esa autorización. Recomendado: que la ficha de un deportista menor solo la vea el coach al que envió solicitud, y que los reportes que involucren menores se revisen en menos de 24 horas. |
| [Ley contra el Odio](https://accesoalajusticia.org/wp-content/uploads/2026/10/Ley-contra-el-Odio-no-solo-establece-delitos-y-penas-de-prision.pdf) (Gaceta 41.276, 10-11-2017) | Las redes y plataformas deben retirar los contenidos prohibidos por la ley en 6 horas; si no, multa de 50.000 a 100.000 UT y posible bloqueo. Organizaciones civiles la critican por su amplitud, pero según la fuente sigue vigente. | Añadir el motivo de reporte "Odio o violencia" con aviso inmediato al equipo y retiro preventivo en menos de 6 horas. |
| [Ley sobre Mensajes de Datos y Firmas Electrónicas](https://vlexvenezuela.com/vid/decreto-fuerza-ley-n-910096321) (Decreto 1.204, 2001) | Los mensajes de datos tienen la misma fuerza probatoria que un documento escrito, y las partes pueden contratar por medios electrónicos. | La aceptación de términos con un toque y la autorización del representante por email son válidas como prueba. Guardar qué versión se aceptó, quién la aceptó y cuándo. |
| [Ejercicio de la fisioterapia](https://www.consejo-fisioterapia.org/documentos/asociacionessudamerica.pdf) (Resolución, Gaceta 35.784 de 1995, según la Federación Venezolana de Colegios de Fisioterapeutas) | Solo puede ejercer quien tiene título universitario registrado y está inscrito en la Federación y en el colegio de su estado. La fuente menciona una ley en proyecto cuyo estado no está claro. | En FR-11 pedir, además del título, el número de colegiado y verificarlo. |
| [Normativa cambiaria sobre precios en divisas](https://finanzasdigital.com/consecomercio-precios-dolares-tasa-euro-venezuela/) (según Consecomercio, junio de 2025) | Se pueden fijar precios en dólares, pero el pago en bolívares se calcula con la tasa oficial del BCV. La fuente es un gremio, no el texto legal. | En la v1 no hay pagos en la app, así que basta mostrar el precio en USD como referencia y aclarar que el pago se acuerda con el coach. Revisar de nuevo cuando haya pagos o suscripciones, incluidos los impuestos. |
| Sanciones de EE. UU. sobre Venezuela | No lo verifiqué. Algunos servicios estadounidenses han limitado cuentas o pagos desde Venezuela en el pasado. | Confirmar antes de elegir el stack que se pueden abrir y pagar las cuentas de Apple, Google y Supabase con la titularidad prevista. Es la pregunta 5 del stack. |

## Normas de las tiendas

| Tienda | Qué exige | Estado en nuestros requisitos |
|---|---|---|
| [App Store, 1.2](https://developer.apple.com/app-store/review/guidelines/) (contenido de usuarios) | Filtro de contenido ofensivo antes de publicarse, reportar, bloquear y datos de contacto publicados | Reportar (FR-30) y bloquear (FR-31) cubiertos. **Faltan el filtro y el contacto.** |
| [App Store, 5.1.1](https://developer.apple.com/app-store/review/guidelines/) (datos) | Política de privacidad en la ficha y dentro de la app, consentimiento con forma fácil de retirarlo, eliminación de cuenta dentro de la app | Eliminación cubierta (FR-07). **Faltan el consentimiento explícito y la política dentro de la app.** |
| [App Store, 4.8](https://developer.apple.com/app-store/review/guidelines/) (inicio de sesión) | Si hay login con Google, ofrecer otro equivalente que limite datos y permita ocultar el email | Cubierto con Apple (FR-02). |
| [Google Play, contenido de usuarios](https://support.google.com/googleplay/android-developer/answer/9876937?hl=en) | Aceptar términos que prohíban contenido ofensivo antes de publicar; moderación continua; reportar y bloquear dentro de la app | Reportar y bloquear cubiertos. **Falta aceptar los términos al registrarse.** |
| [Google Play, eliminación de cuenta](https://support.google.com/googleplay/android-developer/answer/13327111?hl=en) | Eliminación dentro de la app y **también desde una página web** sin reinstalar; borrar los datos también en los proveedores; informar qué se conserva | **Falta la página web de eliminación** y declarar qué se conserva (por ejemplo, reportes por seguridad). |

## Cambios propuestos a los requisitos

Aprobados por Diego y aplicados el 2026-10-20 en los requisitos funcionales v0.5 y no funcionales v0.2.

| # | Cambio | Requisito |
|---|---|---|
| L1 | Al registrarse, aceptar términos de uso y política de privacidad, con consentimiento explícito para el tratamiento de datos y para su almacenamiento fuera de Venezuela. Guardar versión, fecha y usuario. | Nuevo FR-35 (M) |
| L2 | Ver y descargar mis datos desde Ajustes (habeas data). | Nuevo FR-36 (S) |
| L3 | Página web para pedir la eliminación de la cuenta sin la app, y política que diga qué se conserva y cuánto tiempo. | Ampliar FR-07 |
| L4 | Filtro automático de palabras ofensivas en bio, nombre y chat, y revisión de fotos reportadas. | Nuevo FR-37 (M) |
| L5 | Email de contacto y soporte visible en Ajustes y en la ficha de las tiendas. | Ampliar FR-30 |
| L6 | Motivo de reporte "Odio o violencia" con aviso inmediato y retiro en menos de 6 horas; reportes con menores en menos de 24 horas. | Ampliar FR-30 y NFR-19 |
| L7 | Fisioterapeutas: pedir y verificar el número de colegiado además del título. | Ampliar FR-11 |
| L8 | La ficha de un deportista menor de 18 solo la ve el coach al que envió solicitud. | Ampliar FR-22 |
| L9 | Precio mostrado como referencia en USD, con la nota "El pago se acuerda con el coach". | Ampliar FR-15 |
| L10 | Revisión de términos, política de privacidad y flujo de menores por un abogado venezolano antes de publicar. | Ampliar NFR-12 |

## Fuentes consultadas (2026-10-20)

- DLA Piper, [Data Protection in Venezuela](https://www.dlapiperdataprotection.com/?c=VE&t=law) (revisado en 2022)
- IAPP, [Venezuela data breach highlights scattered privacy regulation](https://iapp.org/news/a/venezuela-data-breach-highlights-scattered-privacy-regulation) (agosto de 2025)
- [Ley Especial contra los Delitos Informáticos](https://iin.oea.org/badaj/wp-content/uploads/2014/07/Ley_Especial_contra_Delitos_Inform%c3%a1ticos.pdf), texto publicado por la OEA
- Acceso a la Justicia, [Ley contra el Odio no solo establece delitos y penas de prisión](https://accesoalajusticia.org/wp-content/uploads/2026/10/Ley-contra-el-Odio-no-solo-establece-delitos-y-penas-de-prision.pdf)
- vLex, [Decreto 1.204 de Mensajes de Datos y Firmas Electrónicas](https://vlexvenezuela.com/vid/decreto-fuerza-ley-n-910096321)
- Confederación Mundial de Fisioterapia, [asociaciones de Sudamérica](https://www.consejo-fisioterapia.org/documentos/asociacionessudamerica.pdf)
- Finanzas Digital, [Consecomercio sobre precios en dólares](https://finanzasdigital.com/consecomercio-precios-dolares-tasa-euro-venezuela/) (junio de 2025)
- Apple, [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- Google Play, [User Generated Content](https://support.google.com/googleplay/android-developer/answer/9876937?hl=en) y [account deletion requirements](https://support.google.com/googleplay/android-developer/answer/13327111?hl=en)
