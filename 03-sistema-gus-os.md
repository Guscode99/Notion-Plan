# Gus OS — Estudio: mapa del sistema construido

> Construido el 11 oct 2026. Alcance: solo estudio.
> Página principal (privada): https://app.notion.com/p/3f63e6776c67819f9f67ee4441a520da

## Estructura

```
🧠 Gus OS — Estudio          ← página que se abre cada día
│  1. ⭐ Mis tareas de hoy     (Tareas: Estado ∈ {Hoy, Haciendo})
│  2. 🔁 Repasar hoy           (Clases: Toca repasar = "🔁 Sí")
│  3. 📥 Clases por procesar   (Clases: Estado = Por procesar)
│  4. 🔥 Hábitos de hoy        (Hábitos: Fecha = hoy)
│  5. 🗂️ Tablero Kanban        (Tareas agrupadas por Estado)
│  6. 🎓 Mis cursos            (Cursos agrupados por Programa)
│  📖 Guía de uso (desplegable)
└── 🗄️ Bases de datos
```

## Bases de datos (IDs de data source)

| Base | Data source | Propiedades clave |
|---|---|---|
| 🎓 Cursos | `ac6fdb59-7ddf-43c1-a2a6-0bd6fed31cd8` | Programa (Maestría PUCP, Derecho Societario, Fórmula 100K, Inglés, Bolsa de Valores), Estado, Horario, Aula virtual, Carpeta Drive |
| 📚 Clases | `e5f02f9f-d1da-4975-a671-5b90d50c8cb2` | Curso, Fecha, Sesión, Estado, Palabras clave, Grabación, Fireflies, Materiales, Repasos, Último repaso, Dificultad, Próximo repaso (fórmula), Toca repasar (fórmula), Programa (rollup), Conceptos, Recursos, Tareas |
| 🧠 Conceptos | `9d2a53d0-ea0b-41c5-9ffe-250fb6cacadc` | Definición, Tipo, Cursos, Clases, Dominio |
| 🔗 Recursos | `a0f54e70-8396-4bd9-88fa-2b349fac4b37` | Tipo, Link, Curso, Clase, Estado, Nota |
| ✅ Tareas | `43f01296-73da-4cf4-b4f9-c2a0d9ee3fb4` | Estado (Bandeja → Esta semana → Hoy → Haciendo → Bloqueado → Hecho), Prioridad (🐸 Rana / Alta / Normal), Tipo, Fecha límite, Siguiente acción, Pomodoros, Curso, Clase, Proyecto, Alerta (fórmula) |
| 🎯 Proyectos | `68a100b4-0b77-4182-9fe0-095d2f2d3075` | Curso, Estado, Fecha límite, Meta, Tareas |
| 🔥 Hábitos | `56b859db-7d5f-4600-89c3-7ad8ce302e92` | Fecha, 📖 Estudié 25 min, 🔁 Hice mi repaso, 📥 Procesé mis clases, 🇬🇧 Inglés 15 min, 📵 Estudié sin celular, Minutos de estudio, Qué aprendí hoy, Puntaje (0–100) |

## Repaso espaciado

- Clase nueva → primer repaso el día siguiente a `Fecha`.
- Al repasar: sumar 1 a `Repasos`, poner `Último repaso` = hoy y elegir `Dificultad`. El estado pasa a `🔁 En repaso`.
- Intervalo base según `Repasos`: ≤1 → 3 días, 2 → 7, 3 → 14, 4 → 30, ≥5 → 60.
- `😓 Difícil` → 1 día · `😊 Fácil` → intervalo × 2.
- `🏁 Dominada` sale de la cola.

## Cómo procesar una clase (procedimiento para Claude)

1. Buscar la transcripción en Fireflies o en la página "Notas" de Notion y los apuntes del usuario.
2. Crear la fila en 📚 Clases con: curso, fecha, sesión, estado `✅ Procesada`, palabras clave, link de Fireflies o de la grabación, y `Repasos` = 0.
3. Contenido de la página (formato Cornell):
   - Callout de cómo repasar.
   - ❓ 5–10 preguntas de repaso, cada una en un desplegable con la respuesta oculta.
   - 🎯 Para tu tesis o tu entrega (solo si hay algo accionable; lo que no dijo el profesor se marca como sugerencia de Claude).
   - 📝 Apuntes completos: los apuntes del usuario tal cual, lo que faltó marcado con ➕ y cada punto con un enlace 🎙️ al minuto exacto de Fireflies (`https://app.fireflies.ai/view/{id}?t={segundos}`).
   - 🧾 Resumen.
   - 🔗 Fuentes.
4. Crear o enlazar los conceptos en 🧠 Conceptos.
5. Crear en ✅ Tareas las tareas y entregas que dejó el profesor, con su fecha límite.
6. Marcar el hábito "📥 Procesé mis clases" del día.

Ejemplos: "Seminario 2 · S01 — Introducción al curso y capítulo 3" y "Seminario 2 · S02 — Simulacro de examen de grado".

## Pendiente

- Subdivisiones reales de la Maestría PUCP y de Derecho Societario (las dará el usuario).
- Migrar las grabaciones de Fireflies (página "Notas" de Gus Life's) y los apuntes sueltos a 📚 Clases.
- Archivar los sistemas viejos: Gus Life's, trackers de hábitos duplicados, plantillas.
- Carpetas en Drive por curso.
- Agregar los conectores Fireflies y Notion a la rutina "Procesar clases de Fireflies" (ver abajo).
- Rutina de cierre semanal de los viernes.
- Construcción completa de la versión A+ cuando se apruebe: tarjetas con botones Sabía / No sabía, evaluaciones con pesos, red de normas y conceptos, pomodoro fijo en la página principal.

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
