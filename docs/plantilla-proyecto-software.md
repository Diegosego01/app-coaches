# Plantilla de proyecto de software: de la idea a la publicación

Basada en el proyecto **Control de Suscripciones** (septiembre a octubre de 2026). Úsala como punto de partida para cualquier proyecto nuevo: copia el prompt de cada fase, reemplaza lo que está entre `[CORCHETES]` y avanza solo cuando cumplas la puerta de salida.

## Tabla de contenido

1. Reglas del método
2. Mapa de fases
3. Prompt maestro CREFA
4. Fases 0 a 11 (prompt, entregable y puerta de salida)
5. Banco de preguntas de descubrimiento
6. Plantillas de documentos
7. Plantilla del archivo de contexto
8. Reglas de trabajo para la construcción
9. Checklist de seguridad
10. Checklist de publicación
11. Lecciones aprendidas
12. Ruta rápida para proyectos pequeños

---

## 1. Reglas del método

1. **Una fase, un documento.** No se empieza una fase sin que la anterior haya dejado algo escrito.
2. **Preguntar antes de decidir.** Si hay ambigüedad, se hacen preguntas (máximo 3 a 5 por ronda) y lo que se asuma queda marcado como "supuesto por confirmar".
3. **Todo requisito es medible.** Cada requisito tiene criterios de aceptación en formato Dado / Cuando / Entonces, incluyendo casos de error.
4. **Un requisito a la vez en la construcción.** Al terminar cada uno: pruebas pasando, explicación de qué cambió y cómo probarlo, y aprobación antes del commit.
5. **Decidir qué NO se hace.** El alcance incluye explícitamente lo que queda fuera.
6. **Los documentos viven junto al código** y se actualizan al cerrar cada requisito.

---

## 2. Mapa de fases

| Fase | Nombre | Entregable | En Control de Suscripciones |
|---|---|---|---|
| 0 | Idea | Ficha de idea | "No sé cuánto gasto ni cuándo se renueva cada servicio" |
| 1 | Prototipo mínimo (opcional) | Prompt CREFA del prototipo | Página en un HTML con localStorage |
| 2 | Descubrimiento | Respuestas al cuestionario y supuestos | 18 preguntas en 6 bloques |
| 3 | Requisitos funcionales | FR con criterios de aceptación | FR-01 a FR-21 |
| 4 | Requisitos no funcionales | NFR medibles | NFR-01 a NFR-14 |
| 5 | Documento funcional | Perfil, alcance, reglas, historias, casos de uso, casos borde, métricas, glosario | `requisitos-control-suscripciones.md` |
| 6 | Arquitectura | Documento con diagramas, ADR y riesgos | `arquitectura-control-suscripciones.md` |
| 7 | Stack tecnológico | Tabla de tecnologías y decisiones de detalle | Sección 4.2 de la arquitectura |
| 8 | Diseño de datos | Tablas, restricciones, reglas de acceso, migraciones | Esquema con RLS en Supabase |
| 9 | Construcción | Código, pruebas y archivo de contexto | Repositorio con 179 pruebas |
| 10 | Publicación | App en producción probada con datos reales | Vercel (pendiente) |
| 11 | Operación y mejora | Respaldos, versionado, changelog y documentos "tal como se construyó" | Pendiente |

---

## 3. Prompt maestro CREFA

Todos los prompts de esta plantilla usan este esqueleto. **C**ontexto, **R**ol, **E**jemplo, **F**ormato y **A**ditivo.

```
## CONTEXTO
[Qué es el proyecto, quién lo usa, qué problema resuelve y en qué fase estamos.
Pega aquí los documentos de las fases anteriores.]

## ROL
Actúa como [rol específico: por ejemplo, ingeniero de software senior, analista
funcional, arquitecto de software]. [Cómo debe comunicarse: claro, sin jerga,
preciso, sin inventar datos.]

## EJEMPLO
[Un ejemplo corto del resultado esperado, con el nivel de detalle que quieres.]

## FORMATO
[Qué debe entregar, en qué estructura (tablas, secciones, diagramas) y con qué
IDs (FR-, NFR-, BR-, US-, UC-, EC-, ADR-, R-).]

## ADITIVO
- Antes de escribir, hazme un máximo de [3 a 5] preguntas si algo es ambiguo.
- Marca todo supuesto como "Supuesto por confirmar".
- [Restricciones: sin servicios de pago, sin librerías externas, idioma, extensión.]
- [Qué NO debe hacer.]
```

**Truco que funcionó:** cambiar solo el **Rol** cambia la profundidad del resultado. Con "desarrollador web" se obtiene una página; con "ingeniero de software senior con experiencia en requisitos, arquitectura y QA" se obtienen los documentos de ingeniería.

---

## 4. Fases

### Fase 0: Idea

**Objetivo:** convertir una molestia en un problema claro.

```
## CONTEXTO
Tengo esta idea: [describe la idea en 2 o 3 frases]. Hoy resuelvo el problema
así: [cómo lo haces ahora]. Me molesta porque: [dolor concreto].

## ROL
Actúa como analista de producto. Ayudas a aclarar ideas sin imponer soluciones
ni elegir tecnología todavía.

## EJEMPLO
Ficha de idea:
- Problema: no sé cuánto gasto al mes en suscripciones.
- Usuario: solo yo.
- Meta: cancelar las que no uso.
- No debe: conectarse a mi banco ni pedir contraseñas.
- Riesgo principal: que los datos queden desactualizados.

## FORMATO
Hazme máximo 5 preguntas. Luego entrega la ficha de idea: problema, usuario,
meta, qué NO debe hacer, riesgo principal y un resumen en una frase.

## ADITIVO
Si ya existe un producto que resuelve esto, dime en qué se diferencia o si
conviene construirlo. No propongas tecnología.
```

**Entregable:** ficha de idea.
**Puerta de salida:** puedes explicar el proyecto en una frase y decir cómo sabrás que funcionó.

---

### Fase 1: Prototipo mínimo (opcional)

**Objetivo:** probar rápido si la idea sirve, con la versión más simple posible. Si ya tienes claro lo que necesitas, sáltala.

```
## CONTEXTO
[Ficha de idea]. Lo usaré [solo yo / mi equipo] desde [computador / celular].
Mi experiencia técnica es [ninguna / básica / media], así que necesito algo simple
que guarde los datos en el propio navegador.

## ROL
Actúa como desarrollador web senior y diseñador UX. Explicas sin tecnicismos y
entregas código limpio, comentado y fácil de modificar.

## EJEMPLO
[Un registro de ejemplo con sus campos y un resumen de ejemplo del panel principal.]

## FORMATO
Un solo archivo HTML con CSS y JavaScript incluidos, que se abra directo en el
navegador. Funciones mínimas: [lista de 4 a 6 funciones]. Diseño responsive,
código comentado, e instrucciones breves de uso.

## ADITIVO
- Hazme máximo 3 preguntas antes de escribir código.
- Prioriza pocas funciones bien hechas.
- Sin librerías que requieran instalación ni servicios de pago.
```

**Entregable:** prototipo funcional.
**Puerta de salida:** lo usaste unos días y sabes qué le falta. Anota esas ideas para la Fase 2.

---

### Fase 2: Descubrimiento

**Objetivo:** reunir todas las decisiones antes de escribir requisitos. **Hazla antes de redactar requisitos**: en el proyecto original se hizo después y hubo que rehacer los documentos.

```
## CONTEXTO
[Ficha de idea y, si existe, descripción del prototipo.]

## ROL
Actúa como analista funcional. Haces preguntas claras, sin jerga técnica, y
propones una opción razonable cuando no sé la respuesta.

## EJEMPLO
"3. ¿Cómo sabrás que el proyecto fue un éxito? (por ejemplo: 'cancelar al
menos 2 suscripciones que no uso')"

## FORMATO
Preguntas numeradas, agrupadas en 6 bloques: (1) objetivo y usuarios, (2) datos,
(3) funcionamiento y reglas, (4) pantallas y reportes, (5) alcance y
restricciones, (6) preferencias de la documentación. Máximo 20 preguntas.

## ADITIVO
- Si respondo "no sé" o "propón tú", sugiere una opción y márcala como
  "Supuesto por confirmar".
- Incluye siempre preguntas sobre: dispositivos, si debe funcionar sin internet,
  datos sensibles y qué NO debe hacer.
- Al final, lista los documentos que vas a generar con mis respuestas.
```

**Entregable:** respuestas y lista de supuestos.
**Puerta de salida:** cada pregunta tiene respuesta o supuesto marcado. Ver el banco de preguntas en la sección 5.

---

### Fase 3: Requisitos funcionales

**Objetivo:** definir qué hace el sistema, de forma verificable.

```
## CONTEXTO
[Ficha de idea + respuestas del descubrimiento.]

## ROL
Actúa como ingeniero de software senior con experiencia en requisitos
(IEEE 830 / ISO/IEC/IEEE 29148). Eres preciso y no inventas funciones.

## EJEMPLO
- ID: FR-01 | Título: Agregar suscripción | Prioridad: M
- Descripción: el sistema permite registrar una suscripción con nombre,
  categoría, costo, frecuencia y estado.
- Criterios: Dado datos válidos, cuando guardo, entonces aparece en la lista.
  Dado un campo vacío o un costo negativo, entonces se muestra el error y no
  se guarda.

## FORMATO
Tabla con: ID, requisito, prioridad (MoSCoW), criterios de aceptación en formato
Dado / Cuando / Entonces. Cada criterio cubre el caso feliz y al menos un caso
de error o borde.

## ADITIVO
- Un requisito = una función verificable.
- Marca como "Podría" todo lo que no sea imprescindible.
- Máximo 3 preguntas antes de escribir.
```

**Entregable:** lista de FR con criterios.
**Puerta de salida:** cada FR se puede probar con un sí o un no.

---

### Fase 4: Requisitos no funcionales

**Objetivo:** definir **cómo** debe comportarse el sistema, con números.

```
## CONTEXTO
[Requisitos funcionales y respuestas del descubrimiento.]

## ROL
Actúa como ingeniero de software senior especializado en calidad.

## EJEMPLO
- NFR-01 | Rendimiento: con hasta 200 registros, la página carga en menos de
  2 segundos y cada acción responde en menos de 300 ms.

## FORMATO
Tabla con ID, categoría, requisito y criterios medibles en formato Dado /
Cuando / Entonces. Categorías: rendimiento, usabilidad, accesibilidad,
compatibilidad, portabilidad, privacidad, seguridad, fiabilidad, respaldo y
recuperación, mantenibilidad, escalabilidad, exactitud de cálculo.

## ADITIVO
- Prohibido usar "rápido" o "fácil" sin una métrica.
- Si no se puede verificar, márcalo "Por confirmar".
```

**Entregable:** lista de NFR.
**Puerta de salida:** cada NFR tiene un número o una prueba concreta.

---

### Fase 5: Documento funcional consolidado

**Objetivo:** reunir todo en un documento único que se pueda leer sin contexto.

```
## CONTEXTO
[Descubrimiento + FR + NFR.]

## ROL
Actúa como ingeniero de software senior y redactor técnico. Eres bilingüe
(español e inglés) y trazable: nada se inventa.

## EJEMPLO
[Una fila de cada tabla: regla de negocio, historia de usuario, caso de uso y
caso borde.]

## FORMATO
Un documento Markdown con tabla de contenido y estas secciones: decisiones por
confirmar, perfil de usuario, alcance (dentro y fuera), reglas de negocio (BR-),
requisitos funcionales, requisitos no funcionales, historias de usuario (US-),
casos de uso (UC-), casos borde (EC-), métricas de éxito y glosario.

## ADITIVO
- Idioma: [español / inglés / ambos].
- IDs consistentes para poder trazar requisito, prueba y código.
- Ejemplos solo con datos ficticios.
```

**Entregable:** documento funcional v1.0 en `.md`.
**Puerta de salida:** una persona ajena al proyecto lo entiende y no encuentra contradicciones.

---

### Fase 6: Arquitectura

**Objetivo:** decidir cómo se organizan las piezas. **Pregunta pronto dónde viven los datos y si debe funcionar sin internet**: esas dos respuestas cambian requisitos ya escritos.

```
## CONTEXTO
[Documento funcional completo.] Restricciones ya decididas: [por ejemplo, base de
datos requerida, hospedaje, avisos].

## ROL
Actúa como arquitecto de software senior. Justificas cada decisión y señalas lo
que cuesta.

## EJEMPLO
- ADR-01: usar [tecnología] como backend. Razón: [razón]. Costo: [costo].

## FORMATO
Documento con: (1) qué cambia en los requisitos por estas decisiones, (2) vista
general con diagrama Mermaid, (3) componentes y responsabilidades, (4) flujos
clave con diagramas de secuencia, (5) modelo de datos conceptual con diagrama ER,
(6) seguridad y privacidad, (7) ambientes y despliegue, (8) ADR, (9) riesgos
con probabilidad, impacto y mitigación, (10) preguntas abiertas.

## ADITIVO
- Hazme las preguntas que cierren decisiones antes de escribir el documento.
- No escribas código todavía.
- Si una decisión contradice un requisito anterior, dímelo y propón el cambio.
```

**Entregable:** documento de arquitectura.
**Puerta de salida:** las preguntas abiertas están respondidas y los requisitos afectados se actualizaron (versión 1.1).

---

### Fase 7: Stack tecnológico

**Objetivo:** elegir pocas piezas y justificar cada una.

```
## CONTEXTO
[Arquitectura y restricciones.] Mi nivel técnico es [nivel].

## ROL
Actúa como ingeniero de software senior que prefiere soluciones simples.

## FORMATO
Tabla con: capa, tecnología, para qué se usa y notas. Después, una tabla de
decisiones de detalle (dinero, fechas, librerías, compatibilidad) y una lista de
lo que NO se usa y por qué.

## ADITIVO
- Prefiere lo simple sobre lo moderno.
- Cada tecnología debe cubrir un requisito concreto.
- Indica qué cosas hay que validar antes de depender de ellas.
```

**Decisiones de detalle que valió la pena tomar temprano:**
- Dinero en centavos enteros (evita errores de redondeo).
- Fechas como texto `AAAA-MM-DD` sin hora (evita corrimientos por zona horaria).
- Librerías copiadas al repositorio si la app debe funcionar sin internet.

**Entregable:** sección de stack con ADR.
**Puerta de salida:** cada tecnología tiene una razón y las dudas están en el registro de riesgos.

---

### Fase 8: Diseño de datos

**Objetivo:** dejar el esquema listo antes de programar.

```
## CONTEXTO
[Arquitectura, modelo conceptual y requisitos.]

## ROL
Actúa como ingeniero de datos senior con experiencia en [Postgres / la base elegida].

## FORMATO
Para cada tabla: propósito, columnas con tipo, restricciones, índices y reglas de
acceso. Luego: relaciones, vistas calculadas, reglas de seguridad por fila,
estrategia de migraciones y cómo se sincronizan los cambios si hay uso sin
internet.

## ADITIVO
- Todas las tablas con: id, dueño, fechas de creación y modificación, y borrado
  suave si hay sincronización.
- Los valores por defecto y catálogos viven en un solo lugar.
- Cada cambio de esquema es una migración versionada.
```

**Entregable:** diseño de datos y primera migración.
**Puerta de salida:** probaste que un segundo usuario de prueba no puede ver datos ajenos.

---

### Fase 9: Construcción

**Objetivo:** programar requisito por requisito.

```
## CONTEXTO
[Archivo de contexto del proyecto, sección 7.] Vamos a implementar el
requisito [FR-XX]: [descripción y criterios de aceptación].

## ROL
Actúa como ingeniero de software senior. Escribes código simple, con pruebas.

## FORMATO
1. Escribe primero las pruebas del requisito.
2. Implementa lo mínimo para que pasen.
3. Al terminar, dime: qué cambió, qué archivos tocaste y cómo lo pruebo yo.
4. Espera mi aprobación antes del commit.

## ADITIVO
- Un requisito a la vez; no avances al siguiente sin mi aprobación.
- Respeta las reglas de trabajo del archivo de contexto.
- Si el cambio altera una regla ya documentada, avísame antes.
```

**Entregable:** código, pruebas y archivo de contexto actualizado.
**Puerta de salida:** todos los FR de prioridad "Debe" cumplen sus criterios y las pruebas pasan.

---

### Fase 10: Publicación

**Objetivo:** llevar la app a producción y probarla con datos reales.

Pasos: publicar el sitio, cargar la configuración y los secretos de producción, probar con tu cuenta real en tus dispositivos, y activar la verificación en dos pasos. Usa el checklist de la sección 10.

**Entregable:** app en producción.
**Puerta de salida:** el flujo principal funciona en tus dispositivos reales, incluido el caso sin internet y los avisos.

---

### Fase 11: Operación y mejora

**Objetivo:** mantener el proyecto vivo y entendible.

- Actualizar los documentos a la versión "tal como quedó construido" (nombres reales de tablas, funciones y flujos).
- Mantener un `CHANGELOG` con versionado semántico.
- Revisar el respaldo y probar una restauración.
- Pasar las ideas descartadas al backlog con prioridad MoSCoW.

**Entregable:** documentos alineados con el código y backlog.
**Puerta de salida:** alguien que no participó puede entender y modificar el proyecto con solo leer `docs/` y el archivo de contexto.

---

## 5. Banco de preguntas de descubrimiento

Selecciona las que apliquen y adáptalas.

**1. Objetivo y usuarios**
1. ¿Cuál es el problema principal que quieres resolver?
2. ¿Quién lo usará? ¿Solo tú o más personas?
3. ¿Cómo sabrás que el proyecto fue un éxito?

**2. Datos**
4. ¿Qué información necesitas guardar de cada elemento?
5. ¿Qué tipos, frecuencias o variantes existen?
6. ¿Hay dinero, fechas, monedas o zonas horarias involucradas?
7. ¿Hay casos especiales (compartidos, temporales, descuentos)?

**3. Funcionamiento y reglas**
8. ¿Qué estados puede tener cada elemento?
9. ¿Qué debe calcularse automáticamente?
10. ¿Qué categorías o clasificaciones necesitas?
11. ¿Quieres alertas o recordatorios? ¿Con cuánta anticipación y por qué canal?

**4. Pantallas y reportes**
12. ¿Qué es lo primero que quieres ver al abrir la app?
13. ¿Qué reportes necesitas?

**5. Alcance y restricciones**
14. ¿Desde qué dispositivos la usarás? ¿Necesitas que los datos se sincronicen?
15. ¿Debe funcionar sin internet?
16. ¿Qué datos sensibles maneja? ¿Qué NO debe guardar ni pedir?
17. ¿Se conecta con otros sistemas (banco, correo, calendario)? ¿Cuáles no?
18. ¿Hay fecha límite, presupuesto o servicios obligatorios?

**6. Documentación**
19. ¿En qué idioma quieres los documentos?
20. ¿Para quién son: solo tú, un cliente, un equipo, un portafolio?

---

## 6. Plantillas de documentos

### Requisito funcional

| ID | Requisito | P | Criterios de aceptación (Dado / Cuando / Entonces) |
|---|---|---|---|
| FR-XX | [Verbo + objeto] | M / S / C | Dado [situación], cuando [acción], entonces [resultado]. Dado [caso de error], entonces [comportamiento]. |

### Requisito no funcional

| ID | Categoría | Requisito y criterio medible |
|---|---|---|
| NFR-XX | [Categoría] | [Condición medible: número, unidad y cómo verificarlo] |

### Regla de negocio

| ID | Regla |
|---|---|
| BR-XX | [Regla con fórmula, umbral o condición exacta] |

### Historia de usuario

| ID | Historia |
|---|---|
| US-XX | Como [usuario], quiero [acción] para [beneficio]. |

### Caso de uso

| ID | Caso | Flujo principal | Flujos alternos |
|---|---|---|---|
| UC-XX | [Nombre] | 1. [Paso]. 2. [Paso]. 3. [Paso]. | [Error o variante]: [qué pasa] |

### Caso borde

| ID | Situación | Comportamiento esperado |
|---|---|---|
| EC-XX | [Situación límite] | [Qué debe pasar] |

### Decisión de arquitectura (ADR)

| ID | Decisión | Razón | Costo |
|---|---|---|---|
| ADR-XX | [Qué se decidió] | [Por qué] | [Qué se sacrifica] |

### Riesgo

| ID | Riesgo | Prob. | Impacto | Mitigación |
|---|---|---|---|---|
| R-XX | [Qué puede pasar] | Baja / Media / Alta | Baja / Media / Alta | [Qué se hace para evitarlo o reducirlo] |

### Supuesto por confirmar

| # | Tema | Supuesto usado |
|---|---|---|
| A | [Tema] | [Qué asumiste y por qué] |

---

## 7. Plantilla del archivo de contexto

Crea este archivo desde el primer día (por ejemplo `CONTEXTO.md` en la raíz del repositorio). Sirve para retomar el proyecto en un chat nuevo sin explicar todo otra vez. **Adjúntalo como archivo en lugar de copiarlo y pegarlo**: pegar texto largo puede truncarlo.

```
# Contexto del proyecto: [Nombre]

## Qué es
[2 a 4 frases: qué hace, para quién, cómo se usa. Zona horaria, moneda e idioma.]

## Estado actual ([mes y año])
- Hecho: [lista corta]
- Pendiente: [lista corta]

## Stack
[Tecnologías y por qué; cómo se instalan las dependencias.]

## Estructura
[Árbol de carpetas con una línea por carpeta.]

## Cómo funciona
[Flujos principales: datos, sincronización, conflictos, avisos.]

## Modelo de datos
[Tablas y campos comunes.]

## Seguridad
[Acceso, claves, qué se guarda y qué no, protecciones del frontend.]

## Reglas de trabajo
[Cómo se trabaja: un requisito a la vez, convenciones de dinero y fechas,
qué hacer al agregar archivos, migraciones, diseño.]

## Comandos
[Comandos para ejecutar, probar y publicar.]

## Servicios externos
[Proyecto, identificadores públicos, guía de configuración.
Nunca pongas claves privadas aquí.]
```

---

## 8. Reglas de trabajo para la construcción

Tomadas del proyecto original; ajústalas a cada caso.

1. Requisitos de uno en uno. Al terminar: pruebas pasando, explicar qué cambió y cómo probarlo, y esperar aprobación antes del commit.
2. Dinero en centavos enteros; fechas como texto `AAAA-MM-DD`.
3. Catálogos y valores por defecto en un único lugar.
4. Cada archivo nuevo de la app se registra donde corresponda (por ejemplo, lista de archivos del Service Worker) y se sube la versión del caché. Una prueba automática falla si falta alguno.
5. Si cambian reglas que usa el servidor, regenerar la copia y volver a desplegar.
6. Cada cambio de esquema es una nueva migración versionada.
7. Nunca insertar datos del usuario como HTML; usar siempre texto escapado.
8. Diseño: móvil primero, contraste WCAG AA, áreas táctiles de al menos 44 px, revisión en varios anchos (320, 390, 768, 1024 y 1440 px).
9. Las librerías se copian al repositorio con versión fija cuando la app debe funcionar sin internet.

---

## 9. Checklist de seguridad

Para proyectos con cuentas y base de datos en la nube.

- [ ] Reglas de acceso por fila activadas en el 100% de las tablas.
- [ ] Probado con una segunda cuenta que no se ven datos ajenos.
- [ ] Registro público desactivado si es de un solo usuario.
- [ ] Verificación en dos pasos activada y códigos de recuperación guardados.
- [ ] En el frontend solo van claves públicas; las claves de servicio y de terceros son secretos del servidor.
- [ ] Las tareas programadas se autorizan con un secreto que nunca sale de la base.
- [ ] Los datos sensibles de terceros (por ejemplo, archivos del banco) se procesan en el dispositivo y solo se guarda lo confirmado.
- [ ] No se guardan números completos de tarjeta, contraseñas ni credenciales bancarias.
- [ ] Los avisos externos (correo, push) incluyen el mínimo de datos.
- [ ] Política de contenido (CSP) estricta y encabezados de seguridad en el hospedaje.
- [ ] Revisión de los avisos de seguridad del proveedor de base de datos.

---

## 10. Checklist de publicación

- [ ] Todas las pruebas pasan.
- [ ] Ramas principal y de desarrollo alineadas.
- [ ] Variables y secretos de producción cargados.
- [ ] Configuración pública (URL, claves públicas) apunta a producción.
- [ ] La app se instala y abre en computadora y celular.
- [ ] Probado el flujo sin internet y la sincronización al volver.
- [ ] Probados los avisos por cada canal con la cuenta real.
- [ ] Respaldo exportado y restauración probada al menos una vez.
- [ ] Verificación en dos pasos activada.
- [ ] Documentos y archivo de contexto actualizados.

---

## 11. Lecciones aprendidas

| # | Lección | Qué pasó en Control de Suscripciones |
|---|---|---|
| 1 | Pregunta pronto dónde viven los datos, cuántos dispositivos usas y si debe funcionar sin internet. | Aparecieron después de los requisitos y obligaron a reescribir la privacidad (NFR-05), la portabilidad (NFR-11), la sincronización (FR-17) y a revisar una decisión de arquitectura (ADR-03). |
| 2 | Haz el descubrimiento antes de redactar requisitos. | Se redactaron dos veces los requisitos porque el cuestionario llegó después. |
| 3 | Marca los supuestos y confírmalos. | Tres supuestos (conexión al banco, sincronización, alertas) condicionaban requisitos enteros. |
| 4 | Decide qué NO se guarda. | Procesar el CSV del banco en el dispositivo redujo el riesgo de filtración. |
| 5 | Mantén los documentos junto al código. | La documentación quedó atrás: nombres de tablas en inglés frente a español en el código, y tablas que no estaban en el diseño. |
| 6 | Crea el archivo de contexto desde el día uno. | Permitió retomar el proyecto en un chat nuevo en minutos. |
| 7 | Adjunta archivos largos en lugar de pegarlos. | El contexto pegado llegó con partes truncadas. |
| 8 | Diseña la seguridad desde la arquitectura, no al final. | Las reglas de acceso, los secretos y el procesamiento local ya estaban en el diseño antes de programar. |

---

## 12. Ruta rápida para proyectos pequeños

Si el proyecto es pequeño o es un experimento, usa solo estas fases:

| Fase | Qué hacer |
|---|---|
| 0 | Ficha de idea. |
| 2 | 5 a 8 preguntas de descubrimiento, siempre incluyendo datos sensibles y uso sin internet. |
| 3 | Requisitos funcionales con criterios de aceptación (solo los "Debe"). |
| 9 | Construcción con el archivo de contexto y pruebas. |
| 10 | Checklist de publicación. |

Y vuelve a la ruta completa si el proyecto guarda datos de otras personas, maneja dinero o necesita varios dispositivos.
