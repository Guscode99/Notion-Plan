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
   - 🗣️ "Explícalo con tus palabras".
   - 📝 Apuntes del usuario y capturas.
   - 🧾 Resumen.
   - 🔗 Fuentes.
4. Crear o enlazar los conceptos en 🧠 Conceptos.
5. Crear en ✅ Tareas las tareas y entregas que dejó el profesor, con su fecha límite.
6. Marcar el hábito "📥 Procesé mis clases" del día.

Ejemplo: "Clase 01 — TikTok: perfil, SEO y contenido que retiene" (Fórmula 100K, 15 ago 2026).

## Pendiente

- Subdivisiones reales de la Maestría PUCP y de Derecho Societario (las dará el usuario).
- Migrar las grabaciones de Fireflies (página "Notas" de Gus Life's) y los apuntes sueltos a 📚 Clases.
- Archivar los sistemas viejos: Gus Life's, trackers de hábitos duplicados, plantillas.
- Carpetas en Drive por curso.
- Rutinas automáticas de Claude: procesar clases nuevas cada noche y cerrar la semana los viernes.
