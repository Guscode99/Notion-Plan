# Inventario del sistema "Campus" en Notion

Relevamiento de solo lectura hecho el 15 oct 2026 con `notion-fetch` sobre páginas, bases y data sources. No se usó `query-data-sources`. Las filas de ejemplo que se citan son las que Notion devuelve al hacer fetch de cada data source: hasta 3, elegidas al azar. **No son todas las filas.**

Limitaciones:
- **El código de las fórmulas no se puede leer.** El fetch de `formulaCode://9e7c7e82-…/dFNZag` (Tarjetas · Próximo repaso) devolvió *"URL type formulaCode not currently supported for fetch tool."* No se intentó con las demás fórmulas (Toca hoy, Faltan, Puntaje). Los propósitos de las fórmulas que aparecen abajo se **infieren del nombre** y de los textos de las páginas.
- **Tampoco se ven los valores calculados.** Fórmulas y rollups vuelven como referencias `formulaResult://…` / `rollupResult://…`.
- Ninguna fórmula tiene descripción. Solo tienen descripción 7 propiedades manuales, citadas en B.

Convenciones:
- Para los IDs de vistas se da el ID del bloque de base inline. Su URL es `https://app.notion.com/p/<id>`.
- "≠" = *no es igual*; "contiene" = *relation contains*.
- Abreviaturas de cursos de la Maestría, deducidas de Módulos y Recursos:
  - **SI2** = Seminario de Investigación 2 · 1DBF12 (`3f63e6776c67811d8bf6ce828237318e`), ciclo actual.
  - **SI1** = Seminario de Investigación 1 (`3f63e6776c678196…67968f`), ciclo 2026-1.

---

## A) Páginas

### A.1 Portada "Campus"
- URL: https://app.notion.com/p/3f63e6776c67819f9f67ee4441a520da
- Icono 🏛️. Portada `campus.png` (GitHub).
- Propósito: tablero diario y puerta de entrada a todo el sistema.

Bloques en orden:

1. **Embed `campus.html`**, un archivo incrustado. Según la Guía es el "panel oscuro": saludo, próximo hito, pomodoro, lo que viene y próximas 2 semanas.
2. **Columnas 19 % / 52 % / 29 %.**

**Columna 1 (19 %): "🧭 Directorio"**
- **CAMPUS:** enlaces a las subpáginas Repaso, Tareas, Analítica, Revisión semanal, Biblioteca y Guía de uso.
- **PROGRAMAS:** menciones a Mi tesis, Maestría, Societario, 100K, Inglés y Bolsa.
- **CONSULTAR:** menciones a las bases 📚 Clases, 🃏 Tarjetas, 📜 Normas, § Artículos, 🧠 Conceptos y 🔗 Recursos.
- **ACCESOS:** enlaces externos a PAIDEIA, Campus Virtual, Fireflies y Drive.
- **Vista "📥 Bandeja de captura"** (`3f83e6776c678185ba7edbf5afec9f13`)
  - Tipo lista, base Bandeja de captura.
  - Filtro: Procesado no es verdadero.
  - Orden: Creado descendente.
  - Propiedades: Item.

**Columna 2 (52 %)**
- **"⭐ Hoy"** (`3f63e6776c6781ef95f2edf327191cf6`)
  - Tipo lista, base Tareas.
  - Filtro: Estado = ⭐ Hoy **o** 🔨 Haciendo.
  - Orden: Prioridad ascendente.
  - Propiedades: Tarea, Prioridad, Pomodoros.
- **"📅 Esta semana"** (`3f93e6776c6781cb854affdf5697b0a8`)
  - Tipo tabla, base Tareas.
  - Filtro: Estado ≠ ✅ Hecho **y** Fecha límite ≥ hoy **y** ≤ dentro de una semana.
  - Orden: Fecha límite ascendente.
  - Propiedades: Tarea, Fecha límite, Curso, Pomodoros.
- **"🎓 Mis cursos · avance por sesiones vistas"**: un bloque de pestañas. Todas son vistas galería de la base Cursos, con portada tomada de la propiedad Portada y tarjetas pequeñas.

| Pestaña | Vista (ID) | Filtro | Orden | Propiedades |
|---|---|---|---|---|
| 🎓 Maestría | "🎓 Maestría PUCP" (`3f83e6776c6781869d89f72dfa23c1af`) | Programa contiene hub Maestría | Estado asc. | Curso, Avance, Nota actual |
| ⚖️ Societario | "⚖️ Derecho Societario" (`3f83e6776c678125ae2eff77a27368b4`) | Programa contiene hub Societario | — | Curso, Avance |
| 📱 100K | "📱 Fórmula 100K" (`3f83e6776c678125bb9ac5db068e453b`) | Programa contiene hub 100K | — | Curso, Avance |
| 🇬🇧 Inglés | "🇬🇧 Inglés" (`3f83e6776c6781e491fde1a149f22535`) | Programa contiene hub Inglés | — | Curso, Avance |
| 📈 Bolsa | "📈 Bolsa de Valores" (`3f83e6776c67814688adc34797fc73aa`) | Programa contiene hub Bolsa | — | Curso, Avance |

**Columna 3 (29 %)**
- **"🔁 Repaso de hoy"** (`3f83e6776c6781ad8256dd4089dca437`)
  - Tipo lista, base Tarjetas.
  - Filtro: Toca hoy (fórmula de texto) = "🔁 Sí".
  - Orden: Caja ascendente.
  - Propiedades: Pregunta, Responder.
- **"📝 Próximas evaluaciones"** (`3f83e6776c6781d29baaccf8f21da8bc`)
  - Tipo lista, base Evaluaciones.
  - Filtro: Estado = ⏳ Pendiente.
  - Orden: Fecha ascendente.
  - Propiedades: Evaluación, Faltan.
- **"🔥 Hábitos de hoy"** (`3f63e6776c678171ac22da61e3d36372`)
  - Tipo galería, base Hábitos.
  - Filtro: Fecha = hoy.
  - Propiedades: Día, 📖 Estudié 25 min, 🔁 Hice mi repaso, 📥 Procesé mis clases, 🇬🇧 Inglés 15 min, 📵 Estudié sin celular.
- **"📚 Lecturas en curso"** (`3f83e6776c678155ba5fe6358c2a092c`)
  - Tipo lista, base Lecturas.
  - Filtro: Estado ≠ ✅ Terminada.
  - Orden: Estado descendente.
  - Propiedades: Lectura, Avance.

3. **Toggle H3 "🗄️ Más vistas"**: un bloque de pestañas que no tiene filtros salvo donde se indica.

| Pestaña | Vista (ID) | Base | Tipo | Filtro | Orden / agrupación | Propiedades |
|---|---|---|---|---|---|---|
| 📅 Calendario | "📅 Calendario" (`3f63e6776c6781a482c2e29987d51b37`) | Tareas | calendario por Fecha límite | — | — | Tarea |
| 🗂️ Kanban | "Kanban" (`3f63e6776c6781c6ba05c69b4faa76a6`) | Tareas | tablero agrupado por Estado (oculta grupos vacíos) | — | Prioridad asc. | Tarea, Prioridad, Curso, Fecha límite, Alerta, Pomodoros |
| 📆 Semana (lista) | "📅 Esta semana" (`3f83e6776c67813f9922c5164a06d1e5`) | Tareas | lista | Estado = 📅 Esta semana | Fecha límite asc. | Tarea, Fecha límite, Alerta |
| 📌 Entregas | "📌 Próximas entregas" (`3f63e6776c67810c8bb2f024b61fb4f4`) | Tareas | lista | Estado ≠ ✅ Hecho y Fecha límite no vacía | Fecha límite asc. | Tarea, Fecha límite, Alerta |
| 🗓️ Clases de hoy | "🗓️ Clases de hoy" (`3f83e6776c67811492c5fad75547622c`) | Clases | lista | Fecha = hoy | Hora asc. (Hora es texto) | Clase, Hora, Curso, Estado |
| 📚 Clases | "📚 Ruta de mis clases" (`3f63e6776c67813a9a3cff84235fb1cb`) | Clases | tablero agrupado por Estado | — | Fecha desc. | Clase, Curso, Fecha, Palabras clave |
| 📥 Por procesar | "Por procesar" (`3f63e6776c678191a603f813ec979164`) | Clases | lista | Estado = 📥 Por procesar | Fecha asc. | Clase, Curso, Fecha |
| 🔁 Repasar clases | "🔁 Repasar hoy" (`3f63e6776c67816db131cb0c163132d6`) | Clases | lista | Toca repasar (fórmula de texto) = "🔁 Sí" | Fecha asc. | Clase, Curso, Dificultad |
| 🎓 Cursos | "🎓 Cursos por programa" (`3f63e6776c678165bd0fc28449d81b93`) | Cursos | tablero agrupado por **Área** (select) | — | — | Curso, Estado, Horario |
| 🔥 Hábitos | "🔥 Historial de hábitos" (`3f63e6776c6781c7920de09e8f133967`) | Hábitos | tabla | — | Fecha desc. | Día, las 5 casillas, Minutos de estudio, Puntaje |
| 📈 Progreso | "📈 Tareas por estado" (`3f63e6776c678146987cc3d06255dba1`) | Tareas | gráfico de dona: conteo por Estado, oculta vacíos | — | — | — |

### A.2 Repaso
- URL: https://app.notion.com/p/3f83e6776c678187b609fd3df7564e68
- Icono 🔁. Portada `repaso.png`.
- Propósito: repasar las tarjetas con el sistema de cajas de Leitner.

Bloques en orden:

1. **Callout 🧠 (azul) "Cómo repasar (1 minuto por tarjeta)"**, en 3 pasos:
   1. Leer la pregunta y responderla en voz alta sin mirar.
   2. Abrir la tarjeta y desplegar "👀 Ver respuesta".
   3. En Responder elegir ✅ Sabía, 🤔 Dudé o ❌ No sabía.

   Termina con "La tarjeta se reprograma sola."
2. **5 columnas con un callout cada una:**
   - 1️⃣ Caja 1: vuelve mañana.
   - 2️⃣ Caja 2: en 3 días.
   - 3️⃣ Caja 3: en 7 días.
   - 4️⃣ Caja 4: en 16 días.
   - 5️⃣ Caja 5: en 35 días · 🏁.
3. **Texto de reglas:** "✅ Sabía = sube una caja · 🤔 Dudé = se queda · ❌ No sabía = vuelve a la caja 1. Cada mañana Claude ordena las cajas y limpia la columna Responder."
4. **Pestañas**, todas sobre la base Tarjetas:

| Pestaña | Vista (ID) | Tipo | Filtro | Agrupación / orden | Propiedades |
|---|---|---|---|---|---|
| 🔁 Toca hoy | "🔁 Toca hoy" (`3f83e6776c67819ca808cbc5235c5bd2`) | tabla | Toca hoy = "🔁 Sí" | agrupa por Curso (oculta vacíos); Caja asc. | Pregunta, Responder, Caja, Tipo, Clase |
| 📆 Lo que viene | "📆 Lo que viene" (`3f83e6776c6781e7b8f0f21329cd83fe`) | tabla | Estado ≠ 🏁 Dominada | Próximo repaso asc. | Pregunta, Próximo repaso, Caja, Curso |
| 🆕 Nuevas | "🆕 Nuevas" (`3f83e6776c678122ac48d516badd2b00`) | tabla | Estado = 🆕 Nueva | Próximo repaso asc. | Pregunta, Curso, Próximo repaso, Tipo |
| ❌ Difíciles | "❌ Difíciles" (`3f83e6776c6781a4905ad8d1ea306c0d`) | tabla | Fallos ≥ 2 | Fallos desc. | Pregunta, Fallos, Caja, Curso, Próximo repaso |
| 🗂️ Todo el mazo | "🗂️ Todo el mazo" (`3f83e6776c67813d98d5ea558c28097d`) | tablero agrupado por Estado | — | Próximo repaso asc. | Pregunta, Curso, Caja, Próximo repaso |

### A.3 Tareas
- URL: https://app.notion.com/p/3f83e6776c6781f082dfeb33204198a2
- Icono ✅. Portada `campus.png`, la misma que la portada principal.
- Propósito: gestionar las tareas.

Bloques en orden:

1. **Callout 🐸 (verde):** "Regla del día: máximo 3 tareas en ⭐ Hoy. Empieza por la 🐸 Rana (la más difícil) con un pomodoro. Si una tarea pasa de 3 pomodoros, pídele a Claude que la divida."
2. **Pestañas**, todas sobre la base Tareas:

| Pestaña | Vista (ID) | Tipo | Filtro | Agrupación / orden | Propiedades |
|---|---|---|---|---|---|
| 🗂️ Kanban | "🗂️ Kanban" (`3f83e6776c6781f687c1d72b11ac8d00`) | tablero agrupado por Estado | — | Prioridad asc., Fecha límite asc. | Tarea, Prioridad, Fecha límite, Pomodoros, Curso, Siguiente acción |
| ⭐ Hoy | "⭐ Hoy" (`3f83e6776c6781399aacec4374ac2d7c`) | tabla | Estado = ⭐ Hoy o 🔨 Haciendo | Prioridad asc. | Tarea, Estado, Prioridad, Pomodoros, Siguiente acción, Fecha límite |
| 📅 Calendario | "📅 Calendario" (`3f83e6776c6781faa374ff237f6b51a3`) | calendario por Fecha límite | — | — | Tarea, Estado |
| 🎓 Por curso | "🎓 Por curso" (`3f83e6776c6781f8a311ed35a321406d`) | tabla | Estado ≠ ✅ Hecho | agrupa por Curso (oculta vacíos); Fecha límite asc. | Tarea, Estado, Prioridad, Fecha límite, Alerta |
| ✅ Hechas | "✅ Hechas" (`3f83e6776c6781b5923bc48591023475`) | tabla | Estado = ✅ Hecho | Fecha límite desc. | Tarea, Curso, Fecha límite, Pomodoros |

### A.4 Analítica
- URL: https://app.notion.com/p/3f83e6776c678115881ccd759e8372d6
- Icono 📊. Portada `analitica.png`.
- Propósito: ver el progreso calculado.

Bloques en orden:

1. **Callout 📊 (gris):** "Todo se calcula solo: avance por sesiones vistas, nota ponderada por el peso de cada evaluación y tarjetas por estado de dominio."
2. **Vista "🎓 Programas"** (`3f83e6776c6781e4ac7af332d9901d46`)
   - Tipo tabla, base Programas. Sin filtro.
   - Orden: Orden ascendente.
   - Propiedades: Programa, Ciclo, N° cursos, Avance, Promedio, Tarjetas hoy.
3. **Pestañas:**

| Pestaña | Vista (ID) | Base | Tipo | Filtro | Agrupación / orden | Propiedades |
|---|---|---|---|---|---|---|
| 📘 Cursos | "📘 Cursos" (`3f83e6776c6781b6a814f68a9ae38c4c`) | Cursos | tabla | — | agrupa por Programa (relación, oculta vacíos); Estado asc. | Curso, Estado, Avance, Nota actual, Sesiones vistas, Sesiones totales, Tarjetas hoy |
| 📝 Notas y pesos | "📝 Notas y pesos" (`3f83e6776c67811b9d1ceb41628b7298`) | Evaluaciones | tabla | — | Fecha asc. | Evaluación, Curso, Fecha, Peso, Nota, Aporte, Estado, Faltan |
| 🃏 Dominio de tarjetas | "🃏 Dominio de tarjetas" (`3f83e6776c6781688befe2260f6a474b`) | Tarjetas | tablero agrupado por Estado | — | — | Pregunta, Caja, Curso |
| 🔥 Historial de estudio | "🔥 Historial de estudio" (`3f83e6776c678167b711fb7cb8b252db`) | Hábitos | tabla | — | Fecha desc. | Día, Minutos de estudio, las 5 casillas, Qué aprendí hoy (**sin Puntaje**) |

### A.5 Revisión semanal
- URL: https://app.notion.com/p/3f83e6776c67811d8461d07848e98cca
- Icono 🗓️. Portada `campus.png`.
- Propósito: el ritual de 15 minutos de cada viernes.

Bloques en orden:

1. **Callout 🗓️ (morado):** "Cada viernes, 15 minutos. Recorre esta página de arriba a abajo. Al final, dile a Claude: 'Hice mi revisión semanal' y él arma tu semana."
2. **Columnas 32 % / 68 %.**

**Columna izquierda**
- H3 "☑️ Checklist del viernes", con 6 to-dos sin marcar:
  1. Vacía la Bandeja: marca lo que ya no sirve o díselo a Claude.
  2. Revisa tus clases. ¿Todas procesadas? Marca tu Confianza (🟢🟡🔴).
  3. Mira tus evaluaciones. Anota las notas que ya te dieron.
  4. Elige la semana. Pasa a 📅 Esta semana solo lo que sí vas a hacer.
  5. Repasa las tarjetas difíciles en @Repaso.
  6. Dile a Claude: "Hice mi revisión semanal".
- Callout 💡 (gris): "Claude desmarca esta lista cada lunes."

**Columna derecha: pestañas**

| Pestaña | Vista (ID) | Base | Tipo | Filtro | Orden | Propiedades |
|---|---|---|---|---|---|---|
| 📥 Bandeja | "📥 Bandeja sin procesar" (`3f83e6776c678151bdd9ef75e2ec192a`) | Bandeja | tabla | Procesado no es verdadero | Creado asc. | Item, Tipo, Nota, Procesado |
| 📚 Clases | "📚 Clases de esta semana" (`3f83e6776c67818e89d9d36aa12b55ac`) | Clases | tabla | Fecha ≥ hace una semana y ≤ dentro de una semana | Fecha asc. | Clase, Fecha, Estado, Confianza, N° tarjetas |
| 📝 Evaluaciones | "📝 Evaluaciones que vienen" (`3f83e6776c6781dc8294c4bb9abb07b2`) | Evaluaciones | tabla | Estado = ⏳ Pendiente | Fecha asc. | Evaluación, Curso, Fecha, Peso, Faltan |
| ✅ Próxima semana | "✅ Para la próxima semana" (`3f83e6776c6781fcb153f92b779e4594`) | Tareas | tabla | Estado ≠ ✅ Hecho y Fecha límite ≤ dentro de una semana | Fecha límite asc. | Tarea, Estado, Prioridad, Fecha límite, Pomodoros |

### A.6 Biblioteca
- URL: https://app.notion.com/p/3f63e6776c678112ada8c8f4352c5a84
- Icono 📚. Sin portada.
- Propósito: guardar las bases madre.

Bloques en orden:

1. **Texto:** "Aquí viven las bases de datos del sistema. No necesitas entrar aquí a diario: todo se ve desde la página principal."
2. **15 bases de página completa** (no inline), en este orden. Cada una tiene **una sola vista, "Default view"**: tabla sin filtro ni orden, con todas las propiedades visibles.

| # | Base | ID de la base |
|---|---|---|
| 1 | 🎓 Cursos | `6011e0aa42c24181b41dd4e7d1293da8` |
| 2 | 🎯 Proyectos | `3bd41f62d73140e09ab49e3373381848` |
| 3 | 📚 Clases | `5c25883959984461bbda91df74e8c6c5` |
| 4 | 🧠 Conceptos | `f9da8027ac3e404ea8299773dda918f0` |
| 5 | 🔗 Recursos | `ec6b9ecec51a4b56921f53f41023a5e6` |
| 6 | ✅ Tareas | `aca9daf8da60406faee5e8ab2a5931d2` |
| 7 | 🔥 Hábitos | `cf6873af7cef4250960abb74f5f74ee1` |
| 8 | 🎓 Programas | `1da003800b4042dcbd3b9e68a16ea750` |
| 9 | 🧩 Módulos | `b4859550ab5845508499e29c66f0028b` |
| 10 | 🃏 Tarjetas | `2e21525e8ea04a92b7b19a35b908d425` |
| 11 | 📝 Evaluaciones | `b22b54f307c84bb59f8183ed29e563a2` |
| 12 | 📚 Lecturas | `3bf15225f758438fa39c652e4ea53b83` |
| 13 | 📥 Bandeja de captura | `003b7eae242a403ab5c95f0ef80c3f2e` |
| 14 | 📜 Normas | `506ad6370842441f8fb21b90c9bf41e1` |
| 15 | § Artículos | `97decaba522e414b855ced1a780d0036` |

### A.7 Guía de uso
- URL: https://app.notion.com/p/3f93e6776c6781b3a621f7b281b68b28
- Icono 📖. Sin portada. Última edición: 14 oct 2026.
- Propósito: es el manual actual.

Bloques en orden:

1. **Callout 🎯 (azul):** "La idea en una línea: tú solo estudias. Claude graba, ordena, resume, crea tarjetas y programa repasos. Tú abres Campus, haces lo de la columna del día y listo."
2. **H2 "📄 Guía completa en PDF"**: el texto "9 páginas con la maqueta de tu pantalla y los pasos exactos" y el archivo PDF `Guia-de-uso-Campus.pdf`. No se revisó el contenido del PDF.
3. **H2 "1. Primera vez (2 minutos)"**, con to-dos:
   - "••• → Ancho completo", y repetirlo en Repaso, Tareas, Analítica y Revisión semanal.
   - Opcional: hacer que el panel de arriba llene su marco arrastrando el borde inferior.
   - En claude.ai, ir a Rutinas → "Campus: clases, repaso y hábitos (diario)" y agregar los conectores Fireflies y Notion.
4. **H2 "2. Tu rutina diaria (20–30 min)"**: 4 columnas con un callout cada una.
   - 1️⃣ Mira el panel: días que faltan para la próxima entrega.
   - 2️⃣ ⭐ Hoy: máximo 3 tareas; abrir la Rana, leer la Siguiente acción y darle ▶ al pomodoro.
   - 3️⃣ 🔁 Repaso de hoy: responder en voz alta, desplegar 👀 Ver respuesta y elegir en Responder.
   - 4️⃣ 🔥 Hábitos: marcar las casillas antes de dormir.
5. **H2 "3. Qué hay en cada parte de Campus"**: tabla Zona / Qué es / Qué haces con estas zonas:
   - Panel oscuro.
   - Directorio.
   - 📥 Bandeja: escribir; Claude ubica cada cosa.
   - ⭐ Hoy: al terminar, poner Estado = ✅ Hecho.
   - 📅 Esta semana: lo que vence en 7 días; elegir qué pasa a ⭐ Hoy.
   - 🎓 Mis cursos: tocar un curso para ver unidades, clases y tarjetas.
   - 🔁 Repaso de hoy: ✅🤔❌.
   - 📝 Evaluaciones: con días y peso; revisar el semáforo 🔴🟠🟢.
   - 📚 Lecturas: "actualizar páginas leídas".
6. **H2 "4. Cómo funciona el repaso"**: las cajas 1–5. Sabía sube, Dudé se queda y No sabía vuelve a la caja 1. Los intervalos son 1/3/7/16/35 días, y caja 5 + sabes = 🏁 Dominada. Dice: "La tarjeta se reprograma en el momento. Cada mañana Claude ordena las cajas y limpia la columna Responder."
7. **H2 "5. Cuando tienes una clase"**:
   1. Grabar con Fireflies y anotar ideas.
   2. Al día siguiente la clase aparece procesada, con preguntas clave, notas, resumen en 5 líneas, transcripción con 🎙️ minutos y tarjetas.
   3. Marcar Confianza y escribir 3 líneas en "Explícalo a un cliente".
8. **H2 "6. Cuando tienes una entrega o examen"**: "abre la evaluación desde 📝 Evaluaciones = Modo entrega" (qué debe tener, plan día por día y enlaces). Si se pierde un día: "reprograma mi plan de [entrega]".
9. **H2 "7. Los viernes (15 min)"**: remite a Revisión semanal.
10. **H2 "8. Frases para Claude"**:
    - "Procesa mis clases nuevas"
    - "¿Qué hago hoy?"
    - "Divide esta tarea: […]"
    - "Hazme un simulacro de [curso]"
    - "Agrega esta norma: [ley y artículo]"
    - "Hice mi revisión semanal"
11. **H2 "9. Dónde está cada cosa"**:
    - Repaso: todo el mazo, nuevas, difíciles y lo que viene.
    - Tareas.
    - Analítica.
    - Programas (hubs).
    - "🎓 Tu tesis @Mi tesis": pregunta, hipótesis, estado por objetivo, documentos de Drive y normas (LFI, RFI, LGS).
    - 🔗 Recursos: carpetas de Drive, SPIJ y SMV.
    - Biblioteca.
    - 🗄️ Más vistas.
12. **Callout 🔘 (gris):** explica que Notion tiene botones en el plan gratis pero que Claude no puede crearlos, y que Carlos puede crearlos con `/botón`, por ejemplo "Agregar página a → 📚 Clases".

### A.8 Hubs de programa
Los 5 hubs son filas de la base **🎓 Programas**. Por el page-layout de Programas, al abrir un hub se ven arriba las propiedades fijadas: Ciclo, N° cursos, Promedio, Avance, Carpeta Drive y Campus virtual. Debajo va el contenido de la página.

#### A.8.1 Maestría en Derecho Bancario y Financiero — PUCP
- URL: https://app.notion.com/p/3f83e6776c6781d7a547ddb643141f39
- Icono 🎓. Portada `maestria.png`.
- Propiedades: Ciclo "2026-2", Orden 1, Cursos = SI2 + SI1. Tiene Campus virtual (campusvirtual.pucp.edu.pe) y Carpeta Drive.

Bloques en orden:

1. **4 columnas al 25 % con un callout cada una.** Son menciones, no botones.
   - ➕ (azul) "Nueva sesión · @📚 Clases"
   - 📝 (morado) "Nueva evaluación · @📝 Evaluaciones"
   - 📚 (café) "Nueva lectura · @📚 Lecturas"
   - 🧪 (rojo) "Modo entrega · @2.ª entrega", que enlaza a `3f83e6776c6781b8b123d3bcc374155e`
2. **Pestañas:**

| Pestaña | Vista (ID) | Base | Tipo | Filtro | Agrupación / orden | Propiedades |
|---|---|---|---|---|---|---|
| 📘 Cursos | "📘 Cursos" (`3f83e6776c6781238e2dc8676f67aa4c`) | Cursos | tabla | Programa contiene hub Maestría | Estado asc. | Curso, Profesor, Horario, Avance, Nota actual, Tarjetas hoy, Estado |
| 📚 Sesiones | "📚 Sesiones por unidad" (`3f83e6776c6781bba6bbf3ac33b97e25`) | Clases | tabla | Curso contiene SI2 **o** SI1 (IDs fijos) | agrupa por Módulo (oculta vacíos); Fecha asc. | Clase, Fecha, Estado, Confianza, N° tarjetas, Fireflies |
| 🃏 Tarjetas | "🃏 Tarjetas" (`3f83e6776c67810bab51ee5e0937d3d6`) | Tarjetas | tabla | Curso contiene SI2 o SI1 | Próximo repaso asc. | Pregunta, Responder, Caja, Próximo repaso, Estado |
| 🧠 Conceptos | "🧠 Conceptos" (`3f83e6776c6781579f79da9d7899a0d5`) | Conceptos | tabla | Cursos contiene SI2 o SI1 | — | Concepto, Tipo, Definición, Normas |
| 📜 Normas | "📜 Normas" (`3f83e6776c6781a2920ce3bb608ae199`) | Normas | tabla | Cursos contiene SI2 o SI1 | Para la tesis desc. | Norma, Número, Estado, Para la tesis, Resumen, Link oficial |

3. **Columnas 55 % / 45 %.**
   - Izquierda:
     - Vista **"📝 Evaluaciones del ciclo"** (`3f83e6776c67818193a1f85fce605ea7`). Tabla de Evaluaciones; filtro Curso contiene SI2 o SI1; orden Fecha asc.; propiedades Evaluación, Curso, Fecha, Peso, Nota, Aporte, Faltan.
     - Callout ⚖️ (amarillo): "Ojo con los pesos del Sílabo del Seminario 2: la tabla dice 15/15/15/15/40, pero la fórmula dice 0.15·1EE + 0.25·2EE + 0.30·E + 0.30·3EE. Pregunta al profesor cuál vale."
   - Derecha:
     - Vista **"🗓️ Cronograma"** (`3f83e6776c67813d822be8f902e5f0bb`). Calendario de Clases por Fecha; filtro Curso contiene SI2 o SI1; propiedades Clase, Estado.
4. **Vista "📚 Lecturas"** (`3f83e6776c678151aa0be29611ca85a9`)
   - Tabla de Lecturas.
   - Filtro: Curso contiene SI2 o SI1.
   - Orden: Estado descendente.
   - Propiedades: Lectura, Estado, Obligatoria, Avance, Link.

#### A.8.2 Derecho Societario
- URL: https://app.notion.com/p/3f83e6776c6781548365e844ecc16af3
- Icono ⚖️. Portada `societario.png`.
- Propiedades: Ciclo "2026", Orden 2, 1 curso (`3f63…a0b57e`). Sin Campus virtual ni Drive.

Bloques en orden:

1. **Columnas 55 / 45:**
   - **"📚 Sesiones"** (`3f83e6776c6781bca51cdc8f10adb091`): tabla de Clases; filtro Curso contiene `3f63…a0b57e` (ID fijo); orden Fecha asc.; propiedades Clase, Fecha, Estado, Confianza, N° tarjetas.
   - **"✅ Tareas"** (`3f83e6776c67814ea1e8d4db6bc2a043`): tabla de Tareas; filtro Curso contiene ese curso **y** Estado ≠ ✅ Hecho; orden Fecha límite asc.; propiedades Tarea, Estado, Prioridad, Fecha límite, Siguiente acción.
2. **"📘 Cursos"** (`3f83e6776c6781c5a5f2fa9a80df1a9d`): tabla de Cursos; filtro Programa contiene hub Societario; propiedades Curso, Profesor, Horario, Avance, Nota actual, Estado.
3. **Callout 🧩 (gris):** "Cuando tengas el sílabo o el temario, pásaselo a Claude: crea los módulos, las sesiones con fecha y las evaluaciones con su peso."

#### A.8.3 Fórmula 100K
- URL: https://app.notion.com/p/3f83e6776c67813aba1ae6b990999b1a
- Icono 📱. Portada `formula100k.png`.
- Propiedades: Ciclo "2026", Orden 3, 2 cursos (`3f63…c3b753`, `3f63…8c8d91`).

Bloques en orden:

1. **Columnas 55 / 45:**
   - **"📚 Sesiones"** (`3f83e6776c678121a0fac728671855e1`): tabla de Clases; filtro Curso contiene c3b753 o 8c8d91 (IDs fijos); orden Fecha asc.; propiedades Clase, Fecha, Estado, Confianza, N° tarjetas.
   - **"✅ Tareas"** (`3f83e6776c6781669c7fc2d77569315b`): tabla de Tareas; filtro Curso contiene c3b753 o 8c8d91, **sin** filtro de Estado; orden Fecha límite asc.; propiedades Tarea, Estado, Prioridad, Fecha límite, Siguiente acción.
2. **"📘 Cursos"** (`3f83e6776c67811898c1f85e1745880e`): filtro Programa contiene hub 100K; propiedades Curso, Profesor, Horario, Avance, Estado.
3. **Callout 🧩 (gris):** "Cada clase de Fórmula 100K que grabe Fireflies entra sola aquí, con resumen y tarjetas."

#### A.8.4 Inglés
- URL: https://app.notion.com/p/3f83e6776c6781188057eef10cb5197b
- Icono 🇬🇧. Portada `ingles.png`.
- Propiedades: Ciclo "Por iniciar", Orden 4, Carpeta Drive, 1 curso (`3f63…45915e`).

Bloques en orden:

1. **"📘 Cursos"** (`3f83e6776c6781e4af2fc4d98fe31bfe`): filtro Programa contiene hub Inglés; propiedades Curso, Profesor, Horario, Avance, Estado.
2. **Callout 🎯 (rojo):** "Meta: cumplir el requisito de inglés para poder sustentar la tesis. Hábito diario: 🇬🇧 Inglés 15 min."
3. **Columnas 55 / 45:**
   - **"📚 Sesiones"** (`3f83e6776c678194897ae84edab86caa`): filtro Curso contiene 45915e; orden Fecha asc.; propiedades Clase, Fecha, Estado, Confianza, N° tarjetas.
   - **"✅ Tareas"** (`3f83e6776c678174ab3eff2a20027443`): filtro Curso contiene 45915e, sin filtro de Estado; orden Fecha límite asc.; propiedades Tarea, Estado, Prioridad, Fecha límite, Siguiente acción.

#### A.8.5 Bolsa de Valores
- URL: https://app.notion.com/p/3f83e6776c6781079882ed8f85fec0dc
- Icono 📈. Portada `bolsa.png`.
- Propiedades: Ciclo "Por iniciar", Orden 5, 1 curso (`3f63…ea8d1f`).

Bloques en orden:

1. **Columnas 55 / 45:**
   - **"📚 Sesiones"** (`3f83e6776c6781ca90a9d1a38efc7650`): filtro Curso contiene ea8d1f; orden Fecha asc.; propiedades Clase, Fecha, Estado, Confianza, N° tarjetas.
   - **"✅ Tareas"** (`3f83e6776c67811db803f8eff8b2a438`): filtro Curso contiene ea8d1f, sin filtro de Estado; orden Fecha límite asc.; propiedades Tarea, Estado, Prioridad, Fecha límite, Siguiente acción.
2. **"📘 Cursos"** (`3f83e6776c67818fb001e3cbacef53e9`): filtro Programa contiene hub Bolsa; propiedades Curso, Profesor, Horario, Avance, Estado.
3. **Callout 🧩 (gris):** "Pendiente: confirmar si la grabación del 8 oct (intermediación bursátil) es de este programa. Está en la Bandeja."

### A.9 Modo entrega: "🧪 2.ª entrega escrita — correcciones + introducción + conclusiones"
- URL: https://app.notion.com/p/3f83e6776c6781b8b123d3bcc374155e
- Es una fila de la base **📝 Evaluaciones**. Portada `examen.png`.
- Propiedades: Curso SI2; Estado ⏳ Pendiente; Peso 15 %; Fecha 2026-10-18; Tipo 📝 Entrega; 8 tareas relacionadas. Notas: "Peso según la tabla del sílabo; la fórmula del sílabo le da 25 %. Confirmar con el profesor."
- Por el page-layout de Evaluaciones, arriba se ven fijadas Faltan, Fecha, Peso, Estado, Nota y Curso.
- Propósito: es la página de trabajo para esa entrega.

Bloques en orden:

1. **4 columnas al 25 % con un callout cada una:**
   - ⏳ (rojo) "Entrega": @2026-10-18 · 11:59 p. m.
   - ⚖️ (amarillo) "Peso": 15 % (tabla) o 25 % (fórmula del sílabo).
   - 🍅 (azul) "Trabajo": 15 pomodoros en 6 días.
   - 🎯 (verde) "Meta": 18–20 = pase directo a jurados.
2. **Columnas 38 % / 62 %.**
   - Izquierda:
     - H3 "📚 Qué debe tener (según el sílabo)", con 7 to-dos sin marcar: correcciones del cap. 1, del cap. 2 y del cap. 3; Introducción; Conclusiones; Citas APA; IA solo de apoyo.
     - Callout 🤖 (gris): "Antes de enviar, dile a Claude: 'Revisa mi 2.ª entrega contra el sílabo'…"
     - H3 "🔗 A la mano", con enlaces a:
       - Tesis v1.7 (versión de trabajo) y la respuesta al dictamen.
       - 1.ª entrega en PDF.
       - "15 observaciones de los jurados a tu tesis", que es una mención a la clase de ejemplo.
       - "Tu tesis en un vistazo", que es una mención a Mi tesis.
       - Sílabo del Seminario 2 (Drive).
       - "Clase donde lo explicaron", que es una mención a la clase `3f63…c1800f`.
   - Derecha:
     - H3 "🗓️ Plan inverso (un bloque por día)".
     - Vista **"🗓️ Plan inverso"** (`3f83e6776c67817e8fd2c7fb74b747ad`): tabla de Tareas; filtro Evaluación contiene **esta** evaluación (ID fijo); orden Fecha límite asc.; propiedades Tarea, Estado, Fecha límite, Pomodoros, Siguiente acción.
     - Callout 🐸 (verde): "Cada día, pasa la tarea del día a ⭐ Hoy y empieza con un pomodoro. Si un día no se pudo, dile a Claude 'reprograma mi plan de la 2.ª entrega'."

### A.10 Mi tesis: "🎓 Tesis — Maestría en Derecho Bancario y Financiero"
- URL: https://app.notion.com/p/3f63e6776c6781d3aaf3f248ba727f73
- Es una fila de la base **🎯 Proyectos**. Sin portada.
- Propiedades: Curso SI2; Estado 🟢 Activo; Fecha límite 2026-11-22; 11 tareas. Meta: "Tema: la asamblea general de partícipes en los fondos de inversión de oferta pública en el Perú… Versión 1.7 del 28 sep 2026. Meta del ciclo: documento APTO para jurados con la entrega final (22 nov 2026)."
- Propósito: resumen de la tesis en una página.

Bloques en orden:

1. **Callout 🎓 (azul):** el título de la tesis, "La asamblea general de partícipes en los fondos de inversión de oferta pública en el Perú: el trasplante de la junta general de accionistas frente a las actividades principales del negocio del fondo", con "Versión 1.7 · 28 sep 2026 · Fuente: resumen ejecutivo en Drive".
2. **Columnas 50 / 50.**
   - Izquierda:
     - H3 "❓ Pregunta principal".
     - H3 "💡 Hipótesis": Diagnóstico, Propuesta y Rival (Black, 1990).
   - Derecha:
     - H3 "📊 Estado por objetivo": una tabla estática con columnas Objetivo / Dónde / Estado.
       - OE1 ✅
       - OE2 ✅
       - OE3 empírico ⏳
       - OE3 comparado ⏳
       - OE3 contraste fondo mutuo ⏳
       - OE4 🟡 Preliminar
     - H3 "🧩 Las seis actividades principales": la lista de las 6 actividades.
3. **Columnas 50 / 50.**
   - Izquierda:
     - H3 "📂 Tus documentos (Drive)": enlaces a la tesis v1.7, la respuesta al dictamen, el resumen ejecutivo, el plan de investigación, la batería de preguntas, las preguntas a expertos, la guía de extensión, el informe SMV, la "1.ª entrega (14 sep)" y una app de estudio, más 4 carpetas.
   - Derecha:
     - H3 "📜 Normas de la tesis": 5 menciones a normas (IDs `3f93…`).
     - H3 "🗓️ Próximas entregas": la mención a la 2.ª entrega · 2026-10-18 y el texto plano "Entrega final · 2026-11-22", sin mención.
4. **Callout 🗂️ (gris):** "Corrección (14 oct): el 13 oct cargué por error normas sobre deducibilidad de pérdidas por fraude (LIR, SBS, Ley 30096). Ese tema era de la exposición de Carolina Fujita, no tuyo: tu tesis siempre fue sobre fondos de inversión… Esas normas siguen en 📜 Normas como referencia, con 'Para la tesis' desmarcado."

La página no tiene ninguna vista de base inline.

### A.11 Clase de ejemplo: "Seminario 1 · Exposición final — Tu tesis: fondos de inversión y figuras societarias"
- URL: https://app.notion.com/p/3f63e6776c67813ab410d9e70623a451
- Es una fila de **📚 Clases**, del curso SI1, sesión 8, 2026-07-02, Estado ✅ Procesada.
- Por el page-layout de Clases, arriba se ven fijadas Curso, Fecha, Estado, Confianza, N° tarjetas y Fireflies.

Solo se describe la estructura. El cuerpo es un bloque de **5 pestañas**:

1. **📄 Clase:**
   - Callout ❓ "Preguntas clave".
   - H3 ✍️ "Notas".
   - Callout 🧾 "Resumen en 5 líneas".
   - Columnas: H3 🗣️ "Explícalo a un cliente", que solo tiene un placeholder sin llenar, y H3 🔗 "Conectado con", con menciones a conceptos y normas.
   - H3 🎯 "Para tu 2.ª entrega (18 de octubre)": un callout 💡, 15 to-dos con marcas 🎙️ de minuto y una "Nota de Claude".
2. **🃏 Tarjetas:** un texto y la vista inline **"🃏 Tarjetas de esta clase"** (`3f93e6776c6781d99b62e432ce8df44a`). Es una tabla de Tarjetas con filtro Clase contiene esta clase (ID fijo), sin orden; propiedades Pregunta, Responder, Caja, Próximo repaso, Tipo.
3. **🎙️ Transcripción:** resumen en viñetas con marcas de tiempo.
4. **❓ Dudas para el profe:** 2 to-dos.
5. **🔗 Fuentes:** enlace a Fireflies, una mención a la página de notas de Fireflies y el sílabo.

### A.12 Curso de ejemplo: "🔬 Seminario de Investigación 2 · 1DBF12"
- URL: https://app.notion.com/p/3f63e6776c67811d8bf6ce828237318e
- Es una fila de **🎓 Cursos**. Portada `maestria.png`.
- **El cuerpo de la página está vacío.** Todo lo que se ve al abrir un curso viene del **page-layout de Cursos** (ver B.1):
  - La portada.
  - Las propiedades fijadas Programa, Estado, Profesor, Horario, Avance, Nota actual y Carpeta Drive.
  - **9 módulos de vistas de relación**, en este orden: Módulos, Clases, Evaluaciones, Tarjetas, Lecturas, Conceptos, Normas, Tareas y Recursos.
  - El editor, que está vacío.
  - Los comentarios.
- Valores de las propiedades:
  - Estado 🟢 En curso.
  - Profesor "Bruno Debenedetti Luján".
  - Horario "Jueves quincenal, 7:00 p.m. (Zoom) · 20 ago, 3 y 17 set, 1, 15 y 29 oct, 12 y 26 nov".
  - Sesiones totales 8.
  - Área 🎓 Maestría PUCP.
  - Programa = hub Maestría.
  - Proyectos = Mi tesis.
  - Aula virtual vacía.
  - Portada `card_morado.png`.
- Relaciones: 8 Clases, 20 Conceptos, 3 Evaluaciones, 12 Lecturas, 3 Módulos, 12 Normas, 8 Recursos, 11 Tareas y 14 Tarjetas.

---

## B) Bases de datos (data sources)

Leyenda de quién llena cada campo:
- **[Auto]**: lo calcula Notion (fórmula, rollup o fecha del sistema).
- **[Carlos]**: según la Guía, Repaso o Revisión semanal, lo llena Carlos.
- **[Claude]**: según esos mismos textos, lo crea o actualiza Claude.
- **[Manual s/i]**: es un campo manual y ningún texto dice quién lo llena.

En todos los casos, lo que no es [Auto] es un valor manual dentro de Notion.

Cuando un texto habla de la ficha en general, la atribución a cada campo es **inferida**. Por ejemplo, la Guía §5 dice que "la clase aparece procesada" y que se crean las tarjetas, y de ahí se infiere [Claude] para los campos de Clases y Tarjetas.

### B.1 🎓 Cursos
`collection://ac6fdb59-7ddf-43c1-a2a6-0bd6fed31cd8` · base `6011e0aa42c24181b41dd4e7d1293da8`

| Propiedad | Tipo | Opciones / detalle | Quién |
|---|---|---|---|
| Curso | title | | Claude/Carlos |
| Programa | relation → Programas | | Manual s/i |
| Área | select | 🎓 Maestría PUCP, ⚖️ Derecho Societario, 📱 Fórmula 100K, 🇬🇧 Inglés, 📈 Bolsa de Valores | Manual s/i |
| Estado | select | 🟢 En curso, ⏳ Pendiente, ✅ Terminado | Manual s/i |
| Profesor | text | | Manual s/i |
| Horario | text | | Manual s/i |
| Sesiones totales | number | | Manual s/i |
| Aula virtual | url | | Manual s/i |
| Carpeta Drive | url | | Manual s/i |
| Portada | file | imagen usada como portada en las galerías de "Mis cursos" | Manual s/i |
| Módulos, Clases, Evaluaciones, Tarjetas, Lecturas, Conceptos, Normas, Tareas, Recursos, Proyectos | relation | cada una es la contraparte de la relación Curso o Cursos de su base | se llenan desde la otra base |
| Sesiones vistas | rollup | suma de Clases.Vista | Auto |
| Tarjetas hoy | rollup | suma de Tarjetas.Hoy | Auto |
| Σ aporte | rollup | suma de Evaluaciones.Aporte | Auto |
| Σ peso | rollup | suma de Evaluaciones.Peso calificado | Auto |
| Avance | formula | inferido: Sesiones vistas / Sesiones totales ("avance por sesiones vistas") | Auto |
| Nota actual | formula | inferido: Σ aporte / Σ peso ("nota ponderada por el peso") | Auto |
| n hoy | formula | inferido: Tarjetas hoy como número, para el rollup de Programas | Auto |
| n vistas | formula | inferido: Sesiones vistas como número, para el rollup de Programas | Auto |

**Page-layout** (ancho completo):
- Portada.
- Título con las propiedades fijadas Programa, Estado, Profesor, Horario, Avance, Nota actual y Carpeta Drive.
- Módulos de vistas de relación: Módulos, Clases, Evaluaciones, Tarjetas, Lecturas, Conceptos, Normas, Tareas, Recursos.
- Editor.
- Comentarios.
- Barra lateral: Área, Sesiones totales, Sesiones vistas, Tarjetas hoy, Aula virtual, Portada, Proyectos y las relaciones. Están **ocultas** Σ aporte, Σ peso, n vistas y n hoy.

### B.2 🎓 Programas (los hubs son filas de esta base)
`collection://ab7c4064-5289-4ce6-b197-9060a175516a` · base `1da003800b4042dcbd3b9e68a16ea750`

| Propiedad | Tipo | Detalle | Quién |
|---|---|---|---|
| Programa | title | | Manual |
| Ciclo | text | "2026-2", "2026", "Por iniciar" | Manual s/i |
| Orden | number | 1–5 | Manual s/i |
| Campus virtual | url | | Manual s/i |
| Carpeta Drive | url | | Manual s/i |
| Cursos | relation → Cursos | | Manual s/i |
| N° cursos | rollup | conteo de Cursos | Auto |
| Promedio | rollup | promedio de Cursos.Nota actual | Auto |
| Tarjetas hoy | rollup | suma de Cursos.n hoy | Auto |
| Σ totales | rollup | suma de Cursos.Sesiones totales | Auto |
| Σ vistas | rollup | suma de Cursos.n vistas | Auto |
| Avance | formula | inferido: Σ vistas / Σ totales | Auto |

**Page-layout:** portada; título con las propiedades fijadas Ciclo, N° cursos, Promedio, Avance, Carpeta Drive y Campus virtual; editor (el contenido del hub); comentarios; barra lateral; ancho completo.

### B.3 📚 Clases
`collection://e5f02f9f-d1da-4975-a671-5b90d50c8cb2` · base `5c25883959984461bbda91df74e8c6c5`

| Propiedad | Tipo | Opciones / detalle | Quién |
|---|---|---|---|
| Clase | title | | Claude (desde Fireflies, según la Guía) |
| Curso | relation → Cursos | | Claude |
| Módulo | relation → Módulos | | Claude |
| Sesión | number | | Claude |
| Fecha | date | | Claude |
| Hora | **text** | p. ej. "7:00 p. m." | Claude |
| Estado | select | 📥 Por procesar, ✅ Procesada, 🔁 En repaso, 🏁 Dominada, 🗓️ Programada | Claude |
| Confianza | select | 🟢 Alta, 🟡 Media, 🔴 Baja | **Carlos** ("Marca tu Confianza") |
| Dificultad | select | 😊 Fácil, 🙂 Bien, 😓 Difícil · descripción: "¿Cómo te fue en el último repaso?" | Manual s/i |
| Repasos | number | descripción: "Cuántas veces la repasaste" | Manual s/i |
| Último repaso | date | | Manual s/i |
| Palabras clave | multi_select | TikTok, SEO, Contenido, Retención, Anuncios, Tesis, Metodología, Evaluación, IA y plagio, Examen de grado, Test de proporcionalidad, GAFI / lavado, Inclusión financiera, Derecho comparado | Claude |
| Fireflies | url | | Claude |
| Grabación | url | | Manual s/i |
| Materiales | url | descripción: "Link a diapositivas o carpeta de Drive" | Manual s/i |
| Conceptos, Normas, Artículos, Tarjetas, Tareas, Recursos | relation | | Claude |
| Programa | rollup | vía Curso → **Cursos.Área** (select), no la relación Programas | Auto |
| N° tarjetas | formula | inferido: conteo de la relación Tarjetas | Auto |
| Vista | formula | inferido: 1/0 según si la clase ya se vio; alimenta Cursos.Sesiones vistas | Auto |
| Próximo repaso | formula | inferido: fecha del siguiente repaso de la clase | Auto |
| Toca repasar | formula | devuelve el texto "🔁 Sí" (se usa en el filtro de "🔁 Repasar hoy") | Auto |

**Page-layout:**
- Portada.
- Título con las propiedades fijadas Curso, Fecha, Estado, Confianza, N° tarjetas y Fireflies.
- Editor.
- Comentarios.
- Barra lateral: Palabras clave, Programa, Módulo, Sesión, Hora, Grabación, Materiales, Conceptos, Normas, Artículos, Tarjetas, Tareas, Recursos, Próximo repaso, Repasos, Último repaso, Dificultad. Están **ocultas** Toca repasar y Vista.
- Ancho completo.

### B.4 🃏 Tarjetas
`collection://9e7c7e82-ca73-488a-a678-3a3f1a795ebb` · base `2e21525e8ea04a92b7b19a35b908d425`

| Propiedad | Tipo | Opciones / detalle | Quién |
|---|---|---|---|
| Pregunta | title | | Claude |
| Respuesta | text | se ve en el toggle "👀 Ver respuesta" de la página | Claude |
| Tipo | select | Definición, Plazo o fecha, Excepción, Comparación, Caso, Dato, Regla | Claude |
| Curso | relation → Cursos | | Claude |
| Clase | relation → Clases | | Claude |
| Conceptos | relation → Conceptos | | Claude |
| Responder | select | ✅ Sabía, 🤔 Dudé, ❌ No sabía | **Carlos**; Claude la "limpia cada mañana" |
| Caja | **number** | 1–5 | **Claude** ("Cada mañana Claude ordena las cajas") |
| Estado | select | 🆕 Nueva, 📈 Aprendiendo, 🏁 Dominada | Manual s/i (inferido: Claude) |
| Fallos | number | | Manual s/i (inferido: Claude) |
| Último repaso | date | | Manual s/i (inferido: Claude) |
| Creada | created_time | | Auto |
| Editada | last_edited_time | | Auto |
| Próximo repaso | formula | inferido: Último repaso + intervalo de la Caja (1/3/7/16/35 días) | Auto |
| Toca hoy | formula | devuelve el texto "🔁 Sí" cuando toca repasar | Auto |
| Hoy | formula | inferido: 1/0 para que Cursos.Tarjetas hoy pueda sumar | Auto |

Sin page-layout personalizado.

### B.5 📝 Evaluaciones
`collection://c0fbd9ac-df4d-4ee2-91dc-ac0836aaa761` · base `b22b54f307c84bb59f8183ed29e563a2`

| Propiedad | Tipo | Opciones / detalle | Quién |
|---|---|---|---|
| Evaluación | title | | Claude (desde el sílabo, según el hub Societario) |
| Curso | relation → Cursos | | Claude |
| Tipo | select | 📝 Entrega, 🧪 Examen, 🎤 Exposición, 📋 Control | Claude |
| Fecha | date | | Claude |
| Peso | number (porcentaje) | | Claude |
| Estado | select | ⏳ Pendiente, 📤 Entregada, ✅ Calificada | Manual s/i |
| Nota | number | | **Carlos** ("Anota las notas que ya te dieron") |
| Notas | text | | Claude (p. ej. la duda sobre los pesos) |
| Tareas | relation → Tareas | | Claude |
| Faltan | formula | inferido: días que faltan hasta la Fecha, con el semáforo 🔴🟠🟢 que menciona la Guía | Auto |
| Aporte | formula | inferido: Nota × Peso; alimenta Σ aporte | Auto |
| Peso calificado | formula | inferido: el Peso solo si ya hay Nota; alimenta Σ peso | Auto |

**Page-layout:** portada; título con las propiedades fijadas Faltan, Fecha, Peso, Estado, Nota y Curso; editor (aquí está el "Modo entrega"); comentarios; barra lateral; ancho completo.

Filas de ejemplo vistas:
- "1.ª entrega escrita — capítulos 1 a 3": 📤 Entregada, 15 %, 2026-09-13.
- "2.ª entrega escrita…": 15 %, 2026-10-18, 8 tareas.
- "Entrega final — trabajo de investigación completo": 40 %, 2026-11-22.

### B.6 ✅ Tareas
`collection://43f01296-73da-4cf4-b4f9-c2a0d9ee3fb4` · base `aca9daf8da60406faee5e8ab2a5931d2`

| Propiedad | Tipo | Opciones / detalle | Quién |
|---|---|---|---|
| Tarea | title | | Claude/Carlos |
| Estado | select | 📥 Bandeja, 📅 Esta semana, ⭐ Hoy, 🔨 Haciendo, ⛔ Bloqueado, ✅ Hecho | **Carlos** (pasa tareas a Hoy y las marca ✅ Hecho) |
| Prioridad | select | 🐸 Rana (la más difícil), 🔴 Alta, ⚪ Normal | Manual s/i |
| Tipo | select | 📝 Tarea, 📖 Lectura, 🧪 Examen, 📦 Trabajo final, 📥 Procesar clase, 🔁 Repaso | Manual s/i |
| Fecha límite | date | | Claude ("plan inverso", "reprograma mi plan") |
| Pomodoros | number | descripción: "Bloques de 25 min estimados. Si es más de 3, pide a Claude que la divida" | Claude/Carlos |
| Siguiente acción | text | descripción: "El primer paso concreto y físico. Ej: abrir el PDF y leer 5 páginas" | Claude/Carlos |
| Curso | relation → Cursos | | |
| Clase | relation → Clases | | |
| Evaluación | relation → Evaluaciones | | |
| Proyecto | relation → Proyectos | | |
| Alerta | formula | inferido: aviso por cercanía o vencimiento de la Fecha límite | Auto |
| Hecha | formula | inferido: verdadero si Estado = ✅ Hecho | Auto |

Sin page-layout personalizado.

### B.7 🔥 Hábitos
`collection://56b859db-7d5f-4600-89c3-7ad8ce302e92` · base `cf6873af7cef4250960abb74f5f74ee1`

| Propiedad | Tipo | Quién |
|---|---|---|
| Día | title (p. ej. "Mié 14 oct") | Claude (inferido; la rutina diaria se llama "clases, repaso y hábitos") |
| Fecha | date | Claude (inferido) |
| 📖 Estudié 25 min | checkbox | **Carlos** ("marca casillas antes de dormir") |
| 🔁 Hice mi repaso | checkbox | **Carlos** |
| 📥 Procesé mis clases | checkbox | **Carlos** |
| 🇬🇧 Inglés 15 min | checkbox | **Carlos** |
| 📵 Estudié sin celular | checkbox | **Carlos** |
| Minutos de estudio | number | Manual s/i |
| Qué aprendí hoy | text | Manual s/i |
| Puntaje | formula. Inferido: puntos por las casillas marcadas. | Auto |

Sin page-layout personalizado.

### B.8 📚 Lecturas
`collection://511397ba-ecb4-47f0-8e2d-0fcd61f04329` · base `3bf15225f758438fa39c652e4ea53b83`

| Propiedad | Tipo | Opciones | Quién |
|---|---|---|---|
| Lectura | title | | Claude/Carlos |
| Autor | text | | |
| Curso | relation → Cursos | | |
| Estado | select | ⏳ Pendiente, 📖 Leyendo, ✅ Terminada | Manual s/i |
| Obligatoria | checkbox | | |
| Link | url | | |
| Portada | file | | |
| Páginas leídas | number | | **Carlos** ("actualizar páginas leídas") |
| Páginas totales | number | | Manual s/i |
| Avance | formula. Inferido: Páginas leídas / Páginas totales. | | Auto |

Sin page-layout personalizado.

### B.9 📥 Bandeja de captura
`collection://47c3185d-e256-425e-b51e-e776c1db458c` · base `003b7eae242a403ab5c95f0ef80c3f2e`

| Propiedad | Tipo | Opciones | Quién |
|---|---|---|---|
| Item | title | | **Carlos** (escribe) o Claude |
| Tipo | select | 🎙️ Grabación, 🎥 Video, 🔗 Link, 💡 Idea, 📄 Archivo | |
| Link | url | | |
| Nota | text | | |
| Procesado | checkbox | | Claude ("Claude ubica") o Carlos |
| Creado | created_time | | Auto |

No tiene fórmulas ni page-layout personalizado.

### B.10 🎯 Proyectos
`collection://68a100b4-0b77-4182-9fe0-095d2f2d3075` · base `3bd41f62d73140e09ab49e3373381848`

Propiedades:
- Proyecto · title
- Curso · relation → Cursos
- Estado · select: 🟢 Activo, ⏸️ Pausado, 💡 Idea, ✅ Terminado
- Fecha límite · date
- Meta · text, con descripción "¿Qué significa terminarlo?"
- Tareas · relation → Tareas

No tiene fórmulas, rollups ni page-layout personalizado. Única fila vista: Mi tesis.

### B.11 🧠 Conceptos
`collection://9d2a53d0-ea0b-41c5-9ffe-250fb6cacadc` · base `f9da8027ac3e404ea8299773dda918f0`

Propiedades:
- Concepto · title
- Definición · text, con descripción "En tus palabras, en 1-2 líneas"
- Tipo · select: 💡 Concepto, ⚖️ Principio, 🏛️ Institución, 📜 Norma, 🧮 Fórmula, 🛠️ Herramienta
- Dominio · select: 🆕 Nuevo, 🔁 Aprendiendo, ✅ Lo domino. Es manual: ningún texto dice quién lo actualiza.
- Relaciones: Cursos, Clases, Normas, Artículos, Tarjetas

No tiene fórmulas. Lo llena Claude según "Procesa mis clases".

### B.12 📜 Normas
`collection://15d9156a-fc74-4d96-9f79-00314c9c58db` · base `506ad6370842441f8fb21b90c9bf41e1`

Propiedades:
- Norma · title
- Número · text
- Tipo · select: Ley, Decreto Legislativo, Decreto Supremo, Resolución SBS, Resolución SUNAT, Código, Estándar internacional, Resolución SMV
- Estado · select: 🟢 Vigente, 🟡 Modificada, 🔴 Derogada
- Fecha · date
- Link oficial · url
- Resumen · text
- Para la tesis · checkbox
- Relaciones: Cursos, Clases, Conceptos, Artículos

No tiene fórmulas. Lo llena Claude ("Agrega esta norma").

### B.13 § Artículos
`collection://2656e082-d612-4091-a13f-d418713141f0` · base `97decaba522e414b855ced1a780d0036`

Propiedades:
- Artículo · title
- Texto · text
- En simple · text
- Para la tesis · checkbox
- Verificado en SPIJ · checkbox
- Relaciones: Norma → Normas, Clases, Conceptos. **No tiene relación con Curso.**

No tiene fórmulas. Según el recurso "SPIJ" de Recursos, Carlos debe pegar el texto literal de cada artículo y marcar "Verificado en SPIJ".

### B.14 🔗 Recursos
`collection://a0f54e70-8396-4bd9-88fa-2b349fac4b37` · base `ec6b9ecec51a4b56921f53f41023a5e6`

Propiedades:
- Recurso · title
- Tipo · select: ▶️ YouTube, 🎥 Grabación, 📄 PDF / Lectura, 📁 Carpeta Drive, 📊 Diapositivas, ⚖️ Norma, 🌐 Web
- Estado · select: 👀 Por ver, ✅ Visto, 📌 Referencia
- Link · url
- Nota · text
- Relaciones: Curso, Clase

No tiene fórmulas.

### B.15 🧩 Módulos
`collection://8dd858c0-cd20-438e-bb4c-f89b0bd5b017` · base `b4859550ab5845508499e29c66f0028b`

Propiedades:
- Módulo · title
- Orden · number
- Descripción · text
- Relaciones: Curso, Clases

No tiene fórmulas. Ejemplos: "SI1 · Unidad 1", "SI1 · Unidad 2", "SI2 · Unidad 3 — Propuesta final…". Lo crea Claude a partir del sílabo.

---

## C) Cosas raras o rotas (solo se listan; no se corrigió nada)

### C.1 Restos del tema "fraude / LIR", que no es la tesis
1. **Siguen colgados del curso actual SI2.** La Norma "TUO de la Ley del Impuesto a la Renta" y la Norma "Res. SBS 11356-2008", más la Ley 30096 a la que apunta el artículo de fraude informático, tienen **Cursos = SI2**. Por eso aparecen mezcladas en:
   - la pestaña 📜 Normas del hub Maestría;
   - el módulo Normas de la página del curso;
   - las vistas 📜 Normas, 🧠 Conceptos y 📚 Lecturas del hub, que filtran por SI2/SI1.

   El callout de Mi tesis dice que se dejaron "como referencia". Solo se desmarcó "Para la tesis".
2. **Artículos redactados como si fueran la tesis.** "Art. 8 Ley 30096 — Fraude informático" dice: "Te sirve para encajar el fraude bancario en el 'delito' que pide el art. 37 inc. d)". "Art. 37 inc. i) LIR" dice: "Sirve para comparar: ¿el fraude se trata como incobrable o como pérdida por delito?". También existe "Art. 37 LIR — Gastos deducibles". Todos tienen Para la tesis = NO, Verificado en SPIJ = NO y un Texto que es "[Paráfrasis — pegar el texto literal desde SPIJ]". El TUO LIR tiene 4 artículos relacionados.
3. **Lecturas de referencia como pendientes.** "TUO LIR — arts. 37 y 44 (referencia, no es tu tesis)" y "Res. SBS 11356-2008 — provisiones (referencia, no es tu tesis)" están en ⏳ Pendiente y relacionadas con SI2. Por eso **aparecen en "📚 Lecturas en curso" de la portada** y en "📚 Lecturas" del hub.
4. **Conceptos.** 6 conceptos relacionados con SI2 están vinculados a esas normas (TUO LIR, Res. SBS) o al Art. 8 Ley 30096, y salen en la pestaña 🧠 Conceptos del hub. No vi sus nombres.
5. **Relación inconsistente.** La norma TUO LIR tiene Clases = la clase de ejemplo (SI1, 2 jul, "exposición de Carolina Fujita"), pero Cursos = **SI2**.
6. **Contenido de terceros (no está roto; es para revisar).** Hay una tarjeta "Recomendación 32 del GAFI: ¿qué problema tiene el Perú según la exposición de Adrián Mamani?" y la norma "Recomendaciones del GAFI", de la clase S02 de SI2, como "ejemplo de examen de grado". También existe la etiqueta "GAFI / lavado" en Palabras clave.

### C.2 Textos que se contradicen o están desactualizados
7. **Pesos de la nota.** Las tres partes no cuadran:
   - Tabla del sílabo: 15/15/15/15/40.
   - Fórmula del sílabo: 0.15/0.25/0.30/0.30.
   - Lo cargado: SI2 tiene 3 evaluaciones relacionadas, y las que vi (1.ª, 2.ª y final) suman 15 + 15 + 40 = **70 %**.

   La 2.ª entrega dice "15 % (tabla) o 25 % (fórmula)" y sigue sin confirmar. Nota actual y Promedio dependen de esto.
8. **"La tarjeta se reprograma sola / en el momento"** (callout de Repaso y Guía §4). Pero Caja es un **número manual**, y el mismo texto dice "Cada mañana Claude ordena las cajas y limpia la columna Responder". La reprogramación depende de Claude.
9. **Modo entrega solo existe para la 2.ª entrega.** La Guía §6 lo presenta como algo general ("abre la evaluación… es tu Modo entrega"), pero las demás evaluaciones vistas no tienen contenido. Además, el hub Maestría lo enlaza fijo con "🧪 Modo entrega · @2.ª entrega", que quedará viejo después del 18 oct. El callout "15 pomodoros en 6 días" es texto fijo.
10. **Lecturas.** La Guía §3 dice "📚 Lecturas: actualizar páginas leídas", pero ninguna vista muestra Páginas leídas ni Páginas totales, y las lecturas de ejemplo no tienen páginas cargadas, así que Avance no puede calcularse.
11. **Fecha de la 1.ª entrega.** Mi tesis dice "1.ª entrega (14 sep)", pero la evaluación tiene Fecha 2026-09-13.
12. **Mi tesis.** La línea "Entrega final · 2026-11-22" es texto plano, no una mención. El "Estado por objetivo" es una tabla estática que hay que mantener a mano, y la página no tiene vistas de tareas ni de evaluaciones.
13. **Callout del hub Bolsa.** Dice "confirmar si la grabación del 8 oct… Está en la Bandeja". No es verificable sin consultar la base; puede estar desactualizado.
14. **Nombres que no coinciden.** La tarea se llama "Tercera entrega: trabajo de investigación completo (40 %)" y está en Estado 📥 Bandeja, mientras que la evaluación se llama "Entrega final — trabajo de investigación completo".
15. **Regla de los pomodoros.** La regla dice "si pasa de 3, divídela", pero la tarea de la 2.ª entrega tiene 6 pomodoros.

### C.3 Vistas con filtros o lógica dudosa
16. **Dos vistas se llaman "📅 Esta semana" con lógicas distintas:**
    - La de la portada filtra por rango de fechas: Fecha límite entre hoy y +7 días, y no Hecho.
    - La de Más vistas → "📆 Semana (lista)" filtra Estado = 📅 Esta semana.

    El paso 4 de la Revisión semanal ("pasa a 📅 Esta semana") se refiere al Estado. La tabla de la portada no depende de ese Estado.
17. **Las tareas vencidas desaparecen de la portada.** "📅 Esta semana" exige Fecha límite ≥ hoy, y "⭐ Hoy" solo muestra los Estados Hoy y Haciendo. Una tarea vencida y no hecha solo se ve en Kanban, en Entregas o en "Para la próxima semana".
18. **"📚 Clases de esta semana"** (Revisión semanal) cubre de −7 a +7 días, es decir, dos semanas.
19. **"📝 Evaluaciones que vienen"** (Revisión semanal) muestra solo las Pendientes. El paso 3 del checklist pide "anota las notas que ya te dieron", pero las evaluaciones en 📤 Entregada, que esperan nota, no aparecen. Por ejemplo, la 1.ª entrega.
20. **"📚 Lecturas en curso"** (portada) filtra Estado ≠ Terminada, así que incluye las Pendientes, entre ellas las dos de LIR/SBS.
21. **"🗓️ Clases de hoy"** ordena por Hora, que es **texto**. El orden es alfabético ("10:00" aparece antes que "7:00").
22. **"🎓 Cursos por programa"** (Más vistas) agrupa por el select **Área**, no por la relación Programa. Además, el rollup Clases.Programa muestra Cursos.Área. Hay dos clasificaciones paralelas (Área y Programa) que hay que mantener iguales a mano.
23. **Filtros con IDs fijos.** Todas las vistas de los hubs filtran por los IDs de cursos concretos: Sesiones, Tarjetas, Conceptos, Normas, Evaluaciones, Cronograma, Lecturas y Tareas. Un curso nuevo de ese programa no aparecería. Las únicas excepciones son las vistas 📘 Cursos y las galerías de la portada, que filtran por Programa. Lo mismo pasa con el "Plan inverso" de Modo entrega y con "Tarjetas de esta clase", que filtran por un ID fijo.
24. **Tareas en los hubs.** Las vistas "✅ Tareas" de 100K, Inglés y Bolsa **no excluyen las Hechas**. La de Societario sí las excluye.
25. **"📝 Evaluaciones del ciclo"** (Maestría) incluye SI1, que es del ciclo 2026-1.
26. **Hábitos.** El "🔥 Historial de estudio" de Analítica no muestra Puntaje. El "🔥 Historial de hábitos" de Más vistas sí lo muestra, pero no muestra "Qué aprendí hoy".
27. **Programas.Promedio** promedia la Nota actual de todos los cursos del programa. Posiblemente cuenten los cursos sin nota; no se pudo verificar porque no se ven los valores de las fórmulas.

### C.4 Propiedades sin uso visible
Se considera sin uso lo que no aparece en ninguna vista inventariada, fuera de las "Default view" de Biblioteca y de los módulos del page-layout:

28. **Tareas.Hecha** (fórmula): ningún filtro la usa; todos filtran por Estado. Tampoco se muestran Tareas.Tipo, Tareas.Clase ni Tareas.Proyecto.
29. **Clases:** no se muestran Próximo repaso, Sesión, Grabación, Materiales, Repasos ni Último repaso. Las clases tienen un **segundo sistema de repaso paralelo** al de las tarjetas (Toca repasar, Dificultad, Repasos), que solo aparece en "🔁 Repasar clases" de Más vistas y que la Guía no explica. La clase de ejemplo tiene Repasos 0 y Último repaso vacío.
30. **Tarjetas:** no se muestran Respuesta (se ve dentro de la página), Último repaso ni Conceptos.
31. **Lecturas:** no se muestran Autor, Portada, Páginas leídas ni Páginas totales.
32. **Evaluaciones:** no se muestran Tipo, Notas, Tareas ni Peso calificado (este es un auxiliar).
33. **Bandeja:** no se muestra Link.
34. **Conceptos.Dominio** no se muestra en el hub y no se actualiza solo. Además usa opciones distintas a las de Tarjetas.Estado: "Nuevo / Aprendiendo / Lo domino" frente a "Nueva / Aprendiendo / Dominada". Todos los ejemplos están en 🆕 Nuevo.
35. **Bases sin vistas propias** fuera de Biblioteca:
    - Artículos: no tiene relación Curso, así que tampoco sale en la página del curso.
    - Proyectos: tiene una sola fila, la tesis.
    - Recursos y Módulos: solo aparecen en los módulos de la página del curso; Módulos además se usa para agrupar en "Sesiones por unidad".
36. **Cursos.Aula virtual** está vacía en SI2.

### C.5 Duplicados y nombres confusos
37. **Iconos repetidos:**
    - 📚 se usa para Clases y para Lecturas, y también para la Biblioteca.
    - 🎓 se usa para Cursos, Programas, hub Maestría, Mi tesis y la pestaña "Mis cursos".
38. **Dos conceptos de "bandeja":** el Estado "📥 Bandeja" de Tareas y la base "📥 Bandeja de captura".
39. **Vistas repetidas entre páginas con pequeñas diferencias:**
    - Kanban en Más vistas y en Tareas.
    - Calendario en Más vistas y en Tareas.
    - Historial de hábitos en Más vistas y en Analítica.
    - Repaso de hoy en la portada y en Repaso.

    Algunos nombres también cambian: "Kanban" frente a "🗂️ Kanban", y "Por procesar" sin emoji.
40. **Portadas repetidas:** Tareas y Revisión semanal usan la misma portada `campus.png` que la portada principal.

### C.6 Datos vacíos o pendientes
41. **Bandeja sin procesar:** "Seminario 2 · S03 (17 set) — sin grabación" y "Seminario 2 · S04 (1 oct) — sin grabación". La nota pide apuntes o la grabación del campus virtual.
42. **Hábitos:** las filas de ejemplo (Dom 11, Mar 13 y Mié 14 oct) tienen todas las casillas sin marcar y sin Minutos.
43. **Clase de ejemplo:** la sección "🗣️ Explícalo a un cliente" está sin llenar, aunque la Guía §5 pide 3 líneas.
44. **Tarjetas de ejemplo:** tienen Último repaso 2026-10-12, pero fueron creadas el 2026-10-13. La fecha de repaso es anterior a la creación; probablemente es una fecha base.
45. **Curso SI2:** el cuerpo de la página está vacío. No es un error: todo viene del page-layout.

### C.7 No verificable con lectura
46. **El panel `campus.html`** es un archivo incrustado. No se puede saber si sus datos (próximo hito, días para la entrega, próximas 2 semanas) se actualizan solos o son estáticos.
47. **El PDF "Guia-de-uso-Campus.pdf"** (9 páginas) no se revisó por dentro. Puede no coincidir con la estructura actual.
48. **El código de las fórmulas** (Próximo repaso, Toca hoy, Faltan, Puntaje y las demás) no es accesible por fetch, y sus resultados tampoco se ven.
