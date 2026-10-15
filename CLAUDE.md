# Campus: sistema de estudio de Carlos en Notion

Lee esto antes de hacer cualquier cosa. Después lee `00-lo-que-quiere-carlos.txt` y `03-sistema-gus-os.md`.

## Quién es y cómo trabajar con él
- Carlos Huarcaya ("Gus"). Abogado y maestrista en Derecho Bancario y Financiero (PUCP). Tiene TDA.
- Su tesis trata sobre la asamblea general de partícipes en los fondos de inversión de oferta pública. Normas: LFI, RFI y LGS. El tema de fraude y LIR **no** es suyo.
- Ya aprobó todo. No le pidas permiso paso a paso ni le hagas seguir tutoriales.
- Háblale en español simple, con poco texto y directo. Si puedes, usa visuales en lugar de párrafos.
- No le gustan los puntos, premios, niveles ni el "modo rescate".
- No inventes datos.
- No borres ni toques Gus Life's, sus "Notas" de Fireflies ni sus trackers viejos.

## Por qué este proyecto ahora es local
La sesión en la nube no llegaba al navegador de Carlos. Desde una sesión en su computadora, con la extensión de Chrome conectada y Notion abierto, se pueden terminar estas tareas:
1. **Ancho completo:** activarlo en Campus, Repaso, Tareas, Analítica, Revisión semanal y Guía de uso.
2. **Botones (`/botón`) en el Directorio:**
   - ➕ Nueva clase (📚 Clases, Estado = 📥 Por procesar);
   - 📥 Capturar (📥 Bandeja de captura);
   - 🃏 Nueva tarjeta (🃏 Tarjetas, Caja = 1, Estado = 🆕 Nueva).
3. **Tarea programada diaria:** agregar los conectores Fireflies y Notion a «Campus: clases, repaso y hábitos (diario)» en claude.ai, en Routines. Hoy no tiene conectores y no hace nada.

## Qué hay en esta carpeta
| Archivo | Qué es |
|---|---|
| `00-lo-que-quiere-carlos.txt` | Requisitos de Carlos. Consúltalo antes de proponer algo. |
| `03-sistema-gus-os.md` | Mapa del sistema: IDs de Notion, bases, fórmulas y registro de cambios. |
| `reports/inventario-campus-2026-10-14.md` | Recorrido de cada página, vista y base de Campus. |
| `07-guia-interactiva-campus.html` | Manual interactivo, publicado en https://claude.ai/artifact/KM9ig871cYhZ3gubVY5XoN |
| `08-campus-en-un-arbol.pdf` | Resumen de una página: el sistema como árbol. |
| `06-guia-de-uso-campus.pdf` | Guía en PDF de 9 páginas. |
| `widgets/campus.html` | Panel de la portada. Las fechas están en `CICLO` y `EVENTOS`. Si cambian, edita el archivo y vuelve a subirlo. |
| `assets/covers/` | Portadas de las páginas. |

## IDs que más se usan
- **Campus:** `3f63e6776c67819f9f67ee4441a520da`
- **Páginas:**
  - Guía de uso: `3f93e6776c6781b3a621f7b281b68b28`
  - Mi tesis: `3f63e6776c6781d3aaf3f248ba727f73`
  - Modo entrega (2.ª entrega): `3f83e6776c6781b8b123d3bcc374155e`
  - Repaso: `3f83e6776c678187b609fd3df7564e68`
  - Tareas: `3f83e6776c6781f082dfeb33204198a2`
  - Analítica: `3f83e6776c678115881ccd759e8372d6`
  - Revisión semanal: `3f83e6776c67811d8461d07848e98cca`
- **Tarea programada diaria:** `trig_018iKsbFzUUZxSrjsG42MVkN`, a las 6:46 a. m. de Lima.
- **Data sources:** están en la tabla de `03-sistema-gus-os.md`.

## Reglas técnicas aprendidas
- **query-data-sources:** el workspace llegó a su límite de uso. Usa `notion-search` con `data_source_url` y `fetch`.
- **Bloques `<embed>`, `<pdf>` y menciones:** `update_content` no los encuentra. Para cambiarlos, usa `replace_content` con el contenido exacto de la página y verifica con `fetch`.
- **Archivos:** se adjuntan con una URL de raw.githubusercontent de este repositorio.
- **Tarjetas:** cada caja vuelve en 1, 3, 7, 16 o 35 días. La caja nueva la guarda Claude: lee `Responder`, ajusta Caja, Último repaso y Fallos, y limpia `Responder`.
- **Al terminar un cambio:** anótalo en `03-sistema-gus-os.md`.
