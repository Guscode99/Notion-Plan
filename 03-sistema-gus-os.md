# Campus (Gus OS): mapa del sistema construido

> Construido el 11 oct 2026 y rehecho el 13 oct 2026 como réplica de la versión A "Campus" del PDF de propuestas, que se basa en Student OS. Alcance: solo estudio.
> Página principal (privada): https://app.notion.com/p/3f63e6776c67819f9f67ee4441a520da

## Estructura (13 oct 2026, versión compacta estilo Gus Life's)

El usuario comparó Campus con su panel viejo "Gus Life's" y pidió aprovechar mejor el espacio. Gus Life's tiene un solo bloque de 3 columnas de arriba a abajo: listas cortas con una o dos propiedades, un calendario grande al centro y una barra de accesos a la derecha. Campus se rehízo con esa lógica:

```
🏛️ Campus  (portada azul marino campus.png)
├─ Panel azul (widget campus.html, ocupa todo el alto de su marco):
│    saludo + semana del ciclo + próximo hito │ lo que viene (4 fechas) │ pomodoro 25/5/15
├─ Una fila de 3 columnas (27 / 48 / 25)
│    Izquierda (tu día):  ⭐ Hoy · 🔁 Repaso de hoy · 🔥 Hábitos de hoy · 📥 Bandeja
│    Centro:              📅 Calendario (Tareas por fecha límite) · 🎓 Mis cursos (pestañas por programa, tarjetas pequeñas)
│    Derecha (navegación): 🧭 páginas (Repaso, Tareas, Analítica, Revisión semanal, Biblioteca) · 🏛️ programas ·
│                          ➕ bases de datos · 📝 próximas evaluaciones · 📚 lecturas en curso · 🔗 accesos rápidos
├─ 🗄️ Más vistas (desplegable cerrado, con pestañas): Kanban · Esta semana · Entregas · Clases de hoy · Clases ·
│    Por procesar · Repasar clases · Cursos · Hábitos · Progreso (gráfico)
└─ 📖 Cómo usar Campus (desplegable)
```

Las vistas de la portada muestran solo una o dos propiedades:

- Hoy: tarea y prioridad.
- Repaso: pregunta y responder.
- Evaluaciones: nombre y días que faltan.
- Bandeja: el ítem.
- Lecturas: nombre y avance.
- Calendario: solo el título.

Cada callout de color funciona como encabezado de sección, igual que en Gus Life's.

Páginas hijas:

| Página | ID | Contenido |
|---|---|---|
| 🔁 Repaso | `3f83e6776c678187b609fd3df7564e68` | Cómo repasar, las 5 cajas y pestañas Toca hoy · Lo que viene · Nuevas · Difíciles (Fallos ≥ 2) · Todo el mazo |
| ✅ Tareas | `3f83e6776c6781f082dfeb33204198a2` | Kanban · Hoy · Calendario · Por curso · Hechas |
| 📊 Analítica | `3f83e6776c678115881ccd759e8372d6` | Programas (avance, promedio) y pestañas Cursos · Notas y pesos · Dominio de tarjetas · Historial de estudio |
| 🗓️ Revisión semanal | `3f83e6776c67811d8461d07848e98cca` | Checklist del viernes y pestañas Bandeja · Clases · Evaluaciones · Próxima semana |

Hubs de programa (filas de 🎓 Programas):

- **Maestría:** acciones; pestañas Cursos, Sesiones, Tarjetas, Conceptos y Normas; Evaluaciones del ciclo y Cronograma lado a lado; Lecturas.
- **Societario, Fórmula 100K, Inglés y Bolsa:** Cursos, Sesiones y Tareas.
- **Filtros por curso:** las vistas de los hubs filtran por los cursos del programa. Si se agrega un curso nuevo, hay que sumarlo al filtro.

Modo entrega: la evaluación "2.ª entrega escrita" (`3f83e6776c6781b8b123d3bcc374155e`) tiene:

- Portada roja.
- Tarjetas de fecha, peso, trabajo y meta.
- Lista de lo que debe tener según el sílabo.
- Plan inverso: vista de las tareas D-5 a D-0.

Las páginas de Evaluaciones fijan Faltan, Fecha, Peso, Estado, Nota y Curso bajo el título.

Páginas de clase (formato Cornell con pestañas): 📄 Clase (preguntas clave | notas, resumen, explícalo a un cliente, conectado con) · 🃏 Tarjetas (vista filtrada por la clase) · 🎙️ Transcripción · ❓ Dudas para el profe · 🔗 Fuentes. Modelo: S01 `3f63e6776c6781c1800fc6b004d4b42a`.

Widgets: archivos HTML subidos a Notion como bloques embed. Fuentes en `widgets/`:

- `campus.html`: el panel azul actual. Llena todo el alto de su marco y, si hay ancho de sobra, agrega la columna "Lo que viene".
- `reloj.html`, `pomodoro.html`, `hitos.html`: del diseño anterior, ya no están en la página.

Las fechas del ciclo y de los hitos están escritas en el código de `campus.html` (`CICLO` y `EVENTOS`). Cuando cambian, hay que editar el archivo y volver a subirlo.

## Bases de datos (IDs de data source)

| Base | Data source | Propiedades clave |
|---|---|---|
| 🎓 Programas | `ab7c4064-5289-4ce6-b197-9060a175516a` | Ciclo, Cursos, Orden, Carpeta Drive, Campus virtual, N° cursos, Promedio, Tarjetas hoy, Avance (barra) |
| 🎓 Cursos | `ac6fdb59-7ddf-43c1-a2a6-0bd6fed31cd8` | Programa (relación), Área, Estado, Profesor, Horario, Sesiones totales, Sesiones vistas, Avance (barra), Nota actual (ponderada), Tarjetas hoy, Portada, Carpeta Drive |
| 📚 Clases | `e5f02f9f-d1da-4975-a671-5b90d50c8cb2` | Curso, Módulo, Fecha, Hora, Sesión, Estado (incluye 🗓️ Programada), Confianza, Palabras clave, Fireflies, Materiales, N° tarjetas, Vista, Tarjetas, Normas, Artículos, Conceptos, Recursos, Tareas |
| 🧩 Módulos | `8dd858c0-cd20-438e-bb4c-f89b0bd5b017` | Subdivisiones de cada curso (por cargar cuando haya temario) |
| 🃏 Tarjetas | `9e7c7e82-ca73-488a-a678-3a3f1a795ebb` | Pregunta, Respuesta, Curso, Clase, Conceptos, Tipo, Caja (1–5), Responder, Último repaso, Fallos, Estado, Próximo repaso, Toca hoy, Hoy |
| 📝 Evaluaciones | `c0fbd9ac-df4d-4ee2-91dc-ac0836aaa761` | Curso, Fecha, Peso, Nota, Tipo, Estado, Faltan (semáforo), Aporte, Tareas |
| 📚 Lecturas | `511397ba-ecb4-47f0-8e2d-0fcd61f04329` | Curso, Autor, Páginas leídas/totales, Avance, Link, Estado, Obligatoria |
| 📥 Bandeja de captura | `47c3185d-e256-425e-b51e-e776c1db458c` | Tipo, Link, Procesado, Nota |
| 📜 Normas | `15d9156a-fc74-4d96-9f79-00314c9c58db` | Tipo, Número, Fecha, Estado, Link oficial, Resumen, Para la tesis, Artículos, Conceptos, Clases, Cursos |
| § Artículos | `2656e082-d612-4091-a13f-d418713141f0` | Norma, Texto, En simple, Conceptos, Clases, Para la tesis, Verificado en SPIJ |
| 🧠 Conceptos | `9d2a53d0-ea0b-41c5-9ffe-250fb6cacadc` | Definición, Tipo, Cursos, Clases, Dominio |
| 🔗 Recursos | `a0f54e70-8396-4bd9-88fa-2b349fac4b37` | Tipo, Link, Curso, Clase, Estado, Nota |
| ✅ Tareas | `43f01296-73da-4cf4-b4f9-c2a0d9ee3fb4` | Estado (Bandeja → Esta semana → Hoy → Haciendo → Bloqueado → Hecho), Prioridad (🐸 Rana / Alta / Normal), Tipo, Fecha límite, Siguiente acción, Pomodoros, Curso, Clase, Proyecto, Alerta (fórmula) |
| 🎯 Proyectos | `68a100b4-0b77-4182-9fe0-095d2f2d3075` | Curso, Estado, Fecha límite, Meta, Tareas |
| 🔥 Hábitos | `56b859db-7d5f-4600-89c3-7ad8ce302e92` | Fecha, 📖 Estudié 25 min, 🔁 Hice mi repaso, 📥 Procesé mis clases, 🇬🇧 Inglés 15 min, 📵 Estudié sin celular, Minutos de estudio, Qué aprendí hoy, Puntaje (0–100) |

## Repaso espaciado (por tarjeta, cajas Leitner)

- Cada pregunta es una fila de 🃏 Tarjetas. Una tarjeta nueva entra en la caja 1 y toca al día siguiente.
- Carlos elige en `Responder`: ✅ Sabía, 🤔 Dudé o ❌ No sabía. La fórmula `Próximo repaso` se recalcula en el momento, usando la hora de edición.
- Intervalos por caja: 1 → 1 día, 2 → 3, 3 → 7, 4 → 16, 5 → 35.
- ✅ sube una caja · 🤔 se queda · ❌ vuelve a la caja 1 y suma un fallo.
- Cada mañana la rutina guarda la caja, el último repaso y los fallos, y limpia `Responder`.
- Sabía en la caja 5 → 🏁 Dominada, y la tarjeta sale de la cola.
- El 13 oct, las 7 tarjetas de la S02 quedaron para hoy y las 7 de la S01 para el 14 oct, para repartir la carga.
- El repaso por clase (propiedades `Repasos` y `Dificultad` de 📚 Clases) es del diseño anterior. Se mantiene, pero ya no se usa.

## Cómo procesar una clase (procedimiento para Claude)

1. Buscar la transcripción en Fireflies o en la página "Notas" de Notion y los apuntes del usuario.
2. Crear la fila en 📚 Clases con: curso, fecha, sesión, estado `✅ Procesada`, palabras clave, link de Fireflies o de la grabación, y `Repasos` = 0.
3. Contenido de la página, en formato Cornell con pestañas. Modelo: S01.
   - 📄 Clase: preguntas clave | notas, resumen en 5 líneas, explícalo a un cliente, conectado con y, si aplica, 🎯 Para tu tesis o tu entrega.
   - 🃏 Tarjetas: vista filtrada por la clase.
   - 🎙️ Transcripción: los apuntes del usuario tal cual, lo que faltó marcado con ➕ y cada punto con un enlace 🎙️ al minuto exacto (`https://app.fireflies.ai/view/{id}?t={segundos}`).
   - ❓ Dudas para el profe.
   - 🔗 Fuentes.
4. Crear 5–10 tarjetas en 🃏 Tarjetas (caja 1). Crear o enlazar los conceptos en 🧠 Conceptos y las normas en 📜 Normas y § Artículos.
5. Si ya existe una sesión `🗓️ Programada` de esa fecha, completarla en vez de crear otra.
6. Crear en ✅ Tareas las tareas y entregas que dejó el profesor, con su fecha límite.
7. Marcar el hábito "📥 Procesé mis clases" del día.

Ejemplos: "Seminario 2 · S01 — Introducción al curso y capítulo 3" y "Seminario 2 · S02 — Simulacro de examen de grado".

## Pendiente

- **Conectores de la rutina:** agregar los conectores Fireflies y Notion a la rutina en claude.ai. Sin ellos, la rutina no hace nada.
- **Ancho completo:** activarlo en Campus (••• → Ancho completo). La API no puede activarlo.
- **Módulos:** subdivisiones reales de la Maestría PUCP y de Derecho Societario. Se cargan cuando el usuario pase el temario.
- **Normas:** verificar en SPIJ el texto literal de los artículos de § Artículos y marcar "Verificado en SPIJ".
- **Bandeja:** confirmar a qué curso pertenecen "Mock Class Presentation" (6 may) e "imo-effg-jxi" (8 oct).
- **Pesos del sílabo:** confirmar con el profesor cuáles valen. Hoy están cargados los de la tabla.
- **Grabaciones antiguas:** migrar las de Fireflies (página "Notas" de Gus Life's) y los apuntes sueltos a 📚 Clases.
- **Sistemas viejos:** archivar Gus Life's, los trackers de hábitos duplicados y las plantillas, cuando el usuario lo apruebe.
- **Límites del plan Free de Notion:**
  - Solo cabe 1 gráfico. Ya se usa en "Progreso".
  - Los botones nativos y la vista Dashboard no se pueden crear por API. Los reemplazan los callouts de acción y la propiedad `Responder`.

## Registro — 13 oct 2026: réplica del modelo Campus (versión A + Student OS)

- **Datos reales cargados:**
  - 5 programas y 7 cursos con portada.
  - Sesiones S03–S08 del Seminario 2 (S05–S08 como `🗓️ Programada`).
  - 3 evaluaciones con peso.
  - Plan inverso de la 2.ª entrega (D-5 a D-0).
  - 14 tarjetas de la S01 y la S02.
- **Red de la tesis:**
  - 7 normas: TUO LIR, Reglamento LIR, Ley 26702, TUO del Código Tributario, Res. SBS 11356-2008, Ley 30096 y GAFI.
  - 6 artículos: LIR 37, 37 d), 37 i) y 44; Reglamento 21; Ley 30096 art. 8. El texto es paráfrasis y falta verificarlo en SPIJ.
  - 6 conceptos nuevos: causalidad, pérdida extraordinaria por delito, castigo, provisión, fraude informático y gasto no deducible.
- **Lecturas:** sílabos del Seminario 1 y 2 (Drive), la 1.ª entrega (Drive) y los artículos de la LIR, el Reglamento y la SBS.
- **Bandeja:** 4 ítems por confirmar. **Hábitos:** fila "Mar 13 oct".
- **Pantallas:** Campus, Repaso, Tareas, Analítica, Revisión semanal, 5 hubs de programa, Modo entrega y páginas Cornell S01/S02.
- **Rutina:** renombrada "Campus: clases, repaso y hábitos (diario)", mismo ID y horario. Ahora hace esto cada mañana:
  - Procesa las respuestas de las tarjetas.
  - Crea la fila de hábitos.
  - Completa las sesiones programadas en formato Cornell con tarjetas.
  - Enlaza normas y artículos.
  - Ubica la Bandeja.
  - Los lunes, desmarca la revisión semanal.

## Registro — 11 oct 2026: conexión Fireflies → Notion

- Fireflies ya exportaba a Notion (página "Notas" de Gus Life's) **todas** las reuniones, incluidas las de trabajo y las personales. No se modificó esa integración (se cambia desde Fireflies → Integraciones).
- Claude lee Fireflies directamente (conector) e importa **solo clases** a 📚 Clases con estado "📥 Por procesar":
  - Seminario de Investigación 1 (1DBF09, 2026-1): S01 26 mar, S02 10 abr, S04 7 may, S05 21 may, exposición final 2 jul.
  - Seminario de Investigación 2 (1DBF12, 2026-2): S01 20 ago, S02 3 set. Sin grabación en Fireflies: 17 set y 1 oct.
  - Fórmula 100K: Clase 02 (TikTok Ads).
- Cursos actualizados desde los sílabos en Drive (MDBF, docente Bruno Debenedetti Luján). Se agregó Seminario 1 como terminado.
- Tareas: 2da entrega escrita (18 oct, 15%) y 3ra entrega/trabajo final (22 nov, 40%).
- Pendiente de clasificar: "Mock Class Presentation" (6 may) e "imo-effg-jxi" (8 oct, intermediación bursátil).
- Nota del sílabo: la tabla de pesos (15/15/15/15/40) no coincide con la fórmula (0.15·1EE + 0.25·2EE + 0.30·E + 0.30·3EE).

## Registro — 11 oct 2026: clases procesadas y rutina diaria

### Clases procesadas

- **Seminario 2 · S01 (20 ago):**
  - 7 preguntas de repaso.
  - Checklist de la 2.ª entrega (18 oct).
  - Apuntes con 🎙️ enlaces al minuto, resumen y fuentes.
  - Palabras clave: Tesis, Metodología, Evaluación, IA y plagio.
- **Seminario 2 · S02 (3 set), simulacro de examen de grado:**
  - 7 preguntas de repaso.
  - Sección "🎯 Para tu tesis", marcada como sugerencias de Claude.
  - Apuntes con 🎙️ enlaces al minuto, resumen y fuentes.
  - Palabras clave: Examen de grado, Test de proporcionalidad, GAFI / lavado, Inclusión financiera, Derecho comparado, Tesis.
- **Conceptos nuevos en 🧠 Conceptos**, enlazados a las dos clases.
- **Tareas nuevas:**
  - Verificar el requisito de inglés para sustentar.
  - Pedir asesoría personalizada antes de la 2.ª entrega.

### Rutina "Procesar clases de Fireflies"

> El 13 oct 2026 se renombró como "Campus: clases, repaso y hábitos (diario)" y se amplió (ver el registro del 13 oct). Esta sección describe la versión original.

| Campo | Valor |
|---|---|
| ID | `trig_018iKsbFzUUZxSrjsG42MVkN` |
| Horario | todos los días a las 6:46 a. m. (hora de Lima) |
| Sesión | una sesión nueva por ejecución |
| Aviso | notificación push con el reporte |

Qué hace en cada ejecución:

1. Revisa las grabaciones de Fireflies de los últimos 3 días y salta las que ya están en 📚 Clases (busca por el enlace de Fireflies).
2. Importa **solo clases**: títulos con Clase, Seminario o GRUPO 112, códigos de curso, o archivos de Zoom "GMT…Recording" que coinciden con el horario de un curso.
   - **Nunca importa** sesiones personales ("Sesión C. Huarcaya"), reuniones de trabajo o negocio, ni charlas informativas.
   - Si tiene dudas, no importa la grabación y la reporta como "por confirmar".
3. Crea la fila con curso, fecha (en hora de Lima), sesión y enlace de Fireflies.
4. Procesa la página en formato Cornell, como en el procedimiento de arriba, y le pone el estado "✅ Procesada".
5. Crea o enlaza los conceptos y crea en ✅ Tareas los trabajos con fecha que dejó el profesor.
6. No borra nada ni toca la página "Notas" de Gus Life's.

**Bloqueo pendiente:** la rutina se creó **sin conectores**, porque esta organización no permite pasarlos desde la sesión. Sin Fireflies ni Notion, la rutina solo reporta "Faltan los conectores". Para que funcione, hay que abrir la rutina en la sección de rutinas de claude.ai y agregarle los conectores **Fireflies** y **Notion**.

**Integración nativa de Fireflies:** sigue enviando todas las reuniones a la página "Notas" de Gus Life's, incluidas las personales. Para apagarla: Fireflies → Integraciones → Notion.

## Registro — 14 oct 2026 (3): panel que llena su marco, unidades y Bandeja

### Panel de Campus (widget v3)
- **Problema:** Carlos mandó una captura ("se sigue viendo del asco"). El embed ocupaba unos 755 × 560 px. El panel usaba solo 160 px arriba y el resto del marco se veía gris claro, porque el fondo transparente dejaba ver el fondo del embed. La API no puede cambiar la altura del embed.
- **Solución en `widgets/campus.html`:**
  - Fondo #191919, el mismo de Notion en modo oscuro.
  - El panel llena todo el marco con una cuadrícula de 2 × 2:
    - saludo, próximo hito y ciclo;
    - pomodoro;
    - "Lo que viene", con 5 fechas y una ficha de cuenta regresiva;
    - "Tus próximas 2 semanas", un calendario de 14 días con puntos por clase o entrega.
  - Las letras se escalan con el alto del marco.
  - Si el marco mide menos de 300 px de alto, muestra solo la franja de arriba.
  - Si mide menos de 560 px de ancho, apila las tarjetas.
- Se subió por URL de GitHub y se reemplazó el embed con replace_content. La página quedó con el mismo orden.

### Unidades (🧩 Módulos), tomadas de los sílabos
- **Seminario 2:**
  - Unidad 1, Diseño del cap. 3: S01–S03.
  - Unidad 2, Introducción y conclusiones: S04–S05.
  - Unidad 3, Propuesta final: S06–S08.
- **Seminario 1:**
  - Unidad 1, Plan de trabajo: S01–S02.
  - Unidad 2, Cap. 1 "estado del arte": S04–S05.
  - Unidad 3, Cap. 2 "problema de investigación": exposición final.
  - Sesiones sin grabación: 23 abr, 4 jun y 18 jun.
- La página de cada curso muestra primero sus Módulos.
- La vista "📚 Sesiones" del hub de la Maestría ahora se agrupa por unidad.

### Bandeja
- **"Mock Class Presentation" (6 may):** era una clase muestra de una charla de admisión a un LLM. Se marcó como procesada y se agregó como recurso de Inglés.
- **"imo-effg-jxi" (8 oct):** es una conversación con Nicolás sobre las SAB y el contrato de intermediación. Sigue pendiente; la nota pide a Carlos escribir "Bolsa" o "descartar".

### Seguimiento
- Revisión única programada (`trig_01GubLcJytcK54aN2zQyZNJc`) para el 16 oct a las 8:00 a. m. de Lima: procesar la clase S05 del Seminario 2 si la grabación ya está en Fireflies. La rutina diaria todavía no tiene conectores.

## Registro — 14 oct 2026 (2): clases pendientes, tesis corregida y guía en PDF

### Corrección importante: el tema de la tesis
- El 13 oct se cargó como tesis la "deducibilidad de pérdidas por fraude en bancos". Era un error: ese tema lo expuso **Carolina Fujita** en la exposición final del Seminario 1 (2 jul).
- La tesis de Carlos siempre fue sobre fondos de inversión. Lo expuso el 9 abr y el 2 jul. Hoy se titula *"La asamblea general de partícipes en los fondos de inversión de oferta pública en el Perú: el trasplante de la junta general de accionistas frente a las actividades principales del negocio del fondo"* (resumen ejecutivo v1.7, 28 sep 2026, en Drive).
- Su asesor temático es Aldo Fuertes, gerente de una SAFI.
- Qué se corrigió (sin borrar nada):
  - **Normas:** 5 nuevas con "Para la tesis":
    - LFI (D. Leg. 862) `3f93e6776c678175ada2d1012a857c1b`
    - RFI (Res. SMV 029-2014-SMV/01) `3f93e6776c67812c9f73cfa60ea4e20a`
    - LGS (Ley 26887) `3f93e6776c6781c9990bfe49c366ef47`
    - Reglamento de Fondos Mutuos (número por verificar) `3f93e6776c67818c910ff2014080f022`
    - Res. 052-2020-SMV/02 `3f93e6776c678175ba78dc9f5256fc59`
    - Se agregó la opción "Resolución SMV" al Tipo.
  - **Artículos:** 10 nuevos: LFI 1 y 3, 11, 30; RFI 29, 93, 94, 98, 121; LGS 111/114/115 y 125–127. Son paráfrasis del resumen ejecutivo, con "Verificado en SPIJ" sin marcar.
  - **Lo del tema de fraude:** normas, artículos y lecturas con "Para la tesis" desmarcado y rotulados "no es tu tesis".
  - **Conceptos:** 7 nuevos de la tesis: sociedad administradora, Comité de Vigilancia, partícipe retail, Régimen General vs. Simplificado, problema de agencia, trasplante jurídico y actividades principales. Patrimonio autónomo y asamblea general de partícipes se enlazaron a sus normas y artículos.
  - **Proyecto "Tesis"** (`3f63e6776c6781d3aaf3f248ba727f73`): ahora tiene página completa con:
    - pregunta e hipótesis;
    - estado por objetivo;
    - documentos de Drive;
    - normas;
    - próximas entregas.
    - También está enlazado en el Directorio de Campus, bajo PROGRAMAS.
  - **Seminario 2 · S02:** la sección "🎯 Para tu tesis" se reescribió para el tema correcto.
  - **Modo entrega:** ahora enlaza la tesis v1.7, la respuesta al dictamen, las 15 observaciones de los jurados y la página de la tesis.
  - **Rutina diaria:** el prompt se actualizó con el tema correcto y con un plan B por si se alcanza el límite de consultas de Notion.
  - **`00-lo-que-quiere-carlos.txt`:** actualizado.

### Clases procesadas (subagentes, una clase cada uno)
Cada clase quedó en formato Cornell con 5 pestañas, 8 tarjetas y la vista de tarjetas dentro de 🃏. Para repartir la carga, cada grupo de tarjetas vence en un día distinto:

| Clase | Tarjetas vencen | Notas |
|---|---|---|
| Seminario 1 · Exposición final — Tu tesis: fondos de inversión y figuras societarias (2 jul) | 15 oct | 15 observaciones de los jurados a la tesis, cada una con su minuto. Tarea "Aplicar observaciones…" (`3f93e6776c6781399d28c790da8c7e8e`) para el 17 oct. |
| Seminario 1 · S04 — Primera exposición de tesis (7 may) | 16 oct | Carlos fue jurado; no expuso. |
| Seminario 1 · S05 — Exposiciones de avance y marco teórico (21 may) | 19 oct | Respuestas del profesor a sus consultas. |
| Seminario 1 · S01 — Presentación del curso y metodología (26 mar) | 20 oct | |
| Seminario 1 · S02 — Mapa de preguntas, hipótesis e índice (9 abr; antes figuraba el 10) | 21 oct | Carlos expuso fondos de inversión; 7 comentarios del profesor. |
| Fórmula 100K · Clase 01 (pasada al formato nuevo; la fecha se cambió al 11 ago) | 22 oct | |
| Fórmula 100K · Clase 02 (13 ago según la grabación) | 23 oct | |

- En total hay 70 tarjetas.
- Conceptos nuevos de las clases:
  - problema de investigación, mapa de preguntas, medición del derecho;
  - teoría de la regulación, tensión normativa, Capítulo 1: marco teórico;
  - hipótesis de investigación, tabla de consistencia, asamblea general de partícipes;
  - patrimonio autónomo, apatía racional, voice y exit;
  - asimetría informativa, hecho de importancia, riesgo sistémico;
  - contenido de valor, humanizar la marca, objetivo publicitario, segmentación, calentamiento de cuenta.
- La tarea vieja "Repasar Clase 01 de TikTok" pasó a 📥 Bandeja con fecha 22 oct, porque ahora repasan las tarjetas.
- Seminario 2 · S03 y S04 siguen "📥 Por procesar": no tienen grabación.

### Apartados completados con datos reales de Drive
- **Carpeta Drive:**
  - Maestría: carpeta Maestría PUCP.
  - Seminario 1 y 2: sus carpetas.
  - Inglés: 5. Inglés.
  - Derecho Societario: biblioteca compartida "DERECHO SOCIETARIO".
- **🔗 Recursos:** 14 filas:
  - de la tesis: carpeta, fuentes, derecho comparado, guía de fuentes oficiales, app de estudio, matriz, exposiciones y grabaciones;
  - web: SPIJ y SMV;
  - de otros cursos: biblioteca societaria, Transacciones Corporativas PUCP, material de Bolsa ULIMA y archivos de inglés.
- **📚 Lecturas:** 7 nuevas:
  - tesis v1.7 (versión de trabajo);
  - respuesta al dictamen;
  - resumen ejecutivo;
  - guía de extensión;
  - Guía de investigación PUCP;
  - tesis modelo de La Serna (2022);
  - tesis recomendadas.

### Guía en PDF
- `06-guia-de-uso-campus.pdf` (9 páginas horizontales, fuente `06-guia-de-uso-campus.html`):
  1. Portada.
  2. Pantalla principal con maqueta.
  3. Rutina diaria.
  4. Repaso y calendario de tarjetas.
  5. Clases.
  6. Tesis y 2.ª entrega.
  7. Semana y frases.
  8. Ajustes de una sola vez.
  9. Mapa del sistema.
- La página "📖 Guía de uso" de Notion enlaza la tesis y los recursos.

### Límites encontrados
- **Consultas a bases de Notion:** el workspace llegó al límite de query-data-sources, en modo SQL y en modo rows. Se trabajó con search y fetch.
- **Chrome:** la extensión no es accesible desde la sesión en la nube. Siguen pendientes para Carlos, o para una sesión en Claude Desktop o `claude remote-control`:
  - ancho completo;
  - altura del panel;
  - botones;
  - conectores de la rutina.
- **Subida de archivos a Notion:** el proxy bloquea la subida directa a api.notion.com, así que el PDF se adjunta por URL pública de GitHub.

## Registro — 14 oct 2026: Campus versión Student OS (aprobada)

Construida según la maqueta `05-maqueta-campus-student-os.pdf`:

- **Panel oscuro:** franja de altura fija (156 px) con fondo transparente. Si el marco de Notion es más alto, lo que sobra se ve como la página.
- **Fila de 3 columnas (19 / 52 / 29):**
  - Directorio: páginas, programas, bases y accesos, con la Bandeja debajo.
  - Centro: ⭐ Hoy, 📅 Esta semana (tabla con fecha, curso y pomodoros) y 🎓 Mis cursos.
  - Derecha: 🔁 Repaso, 📝 Evaluaciones, 🔥 Hábitos y 📚 Lecturas.
- **Encabezados:** sin callouts grandes. Cada vista usa el título que Notion ya le pone.
- **Calendario:** pasó a "Más vistas".
- **Guía de uso:** página nueva dentro de Campus (`3f93e6776c6781b3a621f7b281b68b28`), enlazada en el directorio.
- **Botones:** Notion sí tiene botones en el plan gratis, pero la API no los crea. La guía explica cómo agregarlos con `/botón`.
