# Notion templates for (1) flashcards / spaced repetition, (2) student Kanban / project management, (3) class / lecture notes (Cornell), as modules for Carlos's graduate-law Notion system

> **How this was researched (read first).** Direct page fetches to notion.com, *.gumroad.com and notionthings.com were **blocked by this environment's network policy** (proxy 403 / DNS failure). All findings below therefore come from search-engine extracts of those pages (WebSearch "extended" mode, which reads the pages), not from opening the templates. Exact property names, formulas and current prices inside each template could **not** be inspected directly. Anything that a search extract did not state explicitly is marked *(unverified)* or moved to Gaps. Research date: 2026-10-11.

### Shortlist at a glance (templates confirmed to exist via search results)

| # | Module | Template (creator) | URL | Price | Core mechanism |
|---|---|---|---|---|---|
| 1 | SRS | **Memory** (pawel, pawel.world) | https://www.notion.com/templates/memory | not confirmed *(likely free; unverified)* | Binary "Got it right?" → pick a longer interval → review date updates, cards re-sort |
| 2 | SRS | **Spaced repetition flashcards / "Create Anki-like flashcards for spaced repetitions in Notion"** (Philipp Stelzel — attribution inferred, see below) | https://www.notion.com/templates/spaced-repetition-flashcards-2 ; https://philippstelzel.gumroad.com/l/spaced-repetitions-flashcards | Gumroad $0+ (pay-what-you-want); gallery page shows conflicting figures | Mimics Anki/SuperMemo; interval grows automatically after each successful repetition; Show/Hide-all-answers button |
| 3 | SRS | **Total Recall – Dynamic Spaced Repetition Learning** (Notion Things) | https://notionthings.gumroad.com/l/totalrecall ; https://notionthings.com/portfolio-item/dynamic-spaced-repetition-flashcard-learning/ | paid (amount not confirmed) | 6-level recall rating mapped to Fibonacci intervals (1→1 day … 6→13 days) |
| 4 | SRS | **Simple Spaced Repetition (buttons)** (The Eudaimon) | https://theeudaimon.gumroad.com/l/SimpleSpacedRepetition ; method: https://theeudaimon.com/a-new-way-to-do-spaced-repetition-in-notion-using-buttons/ | $2+ | Buttons Easy / Difficult / Failed update review date + interval; formula flags "due" |
| 5 | SRS | **Spaced Repetition for Students** (listed on Prototion; creator not confirmed) | https://www.prototion.com/notion-template/Spaced-Repetition-for-Students | not confirmed | One checkbox per review; formula changes next date depending on which box is checked |
| 6 | SRS | **Notion Revision Assistant** (apurplenotion) | https://apurplenotion.gumroad.com/l/revisionassistant-notion | free (7 ratings) | Leitner system + spaced repetition |
| 7 | SRS export | **2anki** (Notion connection) | https://www.notion.com/connections/2anki | free account | Toggle blocks → Q/A cards (+ cloze) → .apkg for Anki |
| 8 | Kanban | **Projects & Tasks** (Notion, official) | (gallery URL not captured; help guide: https://www.notion.com/help/guides/tasks-manageable-steps-sub-tasks-dependencies) | free | Two related DBs (Projects, Tasks); board/table/timeline; sub-items + dependencies via relations |
| 9 | Kanban | **Ultimate Tasks / Ultimate Task and Project Management Template** (Thomas Frank) | https://thomasjfrank.com/templates/task-and-project-notion-template/ | free | Inbox, Today, Next 7 Days, sub-tasks, recurring tasks, Trello-style project boards, timeline |
| 10 | Kanban | **Ultimate Brain** (Thomas Frank) | https://thomasjfrank.com/brain/ | paid (price not verified from primary source) | Tasks + Projects + Notes; one level of sub-tasks by design |
| 11 | Thesis | **Literature Review & Thesis Tracker** (Linda) | https://www.notion.com/templates/literature-review-and-thesis-tracker | not confirmed | Chapter tracking with priority, status, advisor feedback, due dates |
| 12 | Thesis | **Masters Thesis** (nx1t14) | https://www.notion.com/templates/masters-thesis | not confirmed | Progress tracker with adjustable word-count targets |
| 13 | Notes | **Cornell Notes** (creator possibly "cherrypicked designs" — unverified) | https://www.notion.com/templates/cornell-notes | not confirmed | TOC, Important memo, Questions & Cues, Notes, Summary |
| 14 | Notes | **Class Notes** (Cornell-based) | https://www.notion.com/templates/class-notes-550 | not confirmed | Cue / Note-taking / Summary sections, notes DB tagged by course |
| 15 | Notes | **AI Class Notes** (Notion) | https://www.notion.com/templates/ai-class-notes | not confirmed | AI-generated lecture summaries |
| 16 | Notes/course | **Course Tracker** | https://www.notion.com/templates/course-tracker | not confirmed | Syllabus page, learning goals, grade calculator, quick links, lecture info, readings |

---

## 1. What are the most recognized Notion spaced-repetition / flashcard templates and their mechanisms? Which is simplest for an ADHD user?

### Takeaway
Almost every Notion SRS template uses the same skeleton: one flashcard database with a **Date** property ("Next review"/"Date reviewed"), an **interval** (number, select or checkbox series), and a **formula** (`dateAdd(...)`) that computes the next due date and/or flags cards as due. The newer approach is to have **buttons** (Free-plan feature) update the date and interval in one click. The simplest model for an ADHD user is the binary one used by Notion's "Memory" template ("Got it right?") or The Eudaimon's 3-button version. The multi-level rating scales (Total Recall's 6 levels) and the checkbox-per-review designs ask the user to make more decisions.

### Cited Findings

**Notion "Memory" (pawel)**
- Notion gallery template "Memory", credited to **pawel** (linked site pawel.world). It describes itself as the simplest spaced-repetition system in Notion. Its UI asks whether you got the card right; choosing a longer interval updates the review date and the cards re-sort automatically. — [Notion: Memory](https://www.notion.com/templates/memory)
- The page showed a single 5-star rating; its "Last updated" date did not render in the extract. The extract does not show whether the control is a button labeled "Got it right" or another UI element *(unverified)*. — [Notion: Memory](https://www.notion.com/templates/memory)

**"Spaced repetition flashcards" (notion.com/templates/spaced-repetition-flashcards-2), probably by Philipp Stelzel**
- Gallery listing titled "Create Anki-like flashcards for spaced repetitions in Notion", rated **4.8/5 from 38 ratings**; reviewers praise the "next review" calculations as logical; one reviewer added a calendar view to see due cards. — [Notion: Spaced repetition flashcards](https://www.notion.com/templates/spaced-repetition-flashcards-2)
- Philipp Stelzel's Gumroad listing "Spaced Repetition Flashcards for Notion" is priced **$0+** (pay-what-you-want). He says it **mimics the Anki and SuperMemo algorithm**, that its key difference is that **intervals grow automatically after each successful repetition**, and that he does not claim it makes Anki obsolete. The Notion gallery page showed several conflicting price figures ($29.00, Free, $7.00), so the gallery listing's price is unclear. — [Gumroad: Philipp Stelzel](https://philippstelzel.gumroad.com/l/spaced-repetitions-flashcards); [Notion gallery (en-gb)](https://www.notion.com/en-gb/templates/spaced-repetition-flashcards-2)
- Third-party mirror lists it as free. — [Notion Everything](https://www.notioneverything.com/templates/spaced-repetition-flashcards-for-notion)
- His buttons tutorial includes a **Show/Hide All Answers** button for the flashcards. — [Philipp Stelzel: Notion buttons tutorial](https://philipp-stelzel.com/notion-buttons-tutorial/)
- He also has a blog explainer on building the system — [Philipp Stelzel: Creating a Spaced Repetition System in Notion](https://philipp-stelzel.com/spaced-repetition-system-notion/) — and a separate paid "Luhmann's Zettelkasten for Notion 2.0" (listed at USD 29) that includes a spaced-repetition review feature. — [Gumroad: Zettelkasten](https://philippstelzel.gumroad.com/l/zettelkasten)

**Total Recall – Dynamic Spaced Repetition Learning (Notion Things), paid**
- It combines the user's recall rating with a **Fibonacci sequence (1, 1, 2, 3, 5, 8, 13…)** to set the next review. Examples from the listing: [1] incorrect recall → 1 day; [2] Difficult Recall → next review in 2 days … [6] Total Recall → next review in 13 days. — [Notion Things portfolio](https://notionthings.com/portfolio-item/dynamic-spaced-repetition-flashcard-learning/); [Gumroad: totalrecall](https://notionthings.gumroad.com/l/totalrecall)

**The Eudaimon: button-based SRS, $2+**
- In a March 2023 blog post, each "cue card" is a database record whose page body reveals the answer. Under the answer, **buttons rate recall as easy, difficult or failed**. Each click updates the review date, sets the next review date and changes whether the card is due. It needs three properties: **a date, a number (interval), and a formula that flags cards due for review**. — [The Eudaimon blog](https://theeudaimon.com/a-new-way-to-do-spaced-repetition-in-notion-using-buttons/)
- The companion template, "Simple Spaced Repetition Notion template, making use of buttons", is sold at **$2+**. — [Gumroad: The Eudaimon](https://theeudaimon.gumroad.com/l/SimpleSpacedRepetition)

**Formula / checkbox approaches**
- Generic formula pattern: a Date property "Next Review" updated from a difficulty select. In one example, "Hard" returns in 1 day and "Easy" in 4. — [Gridfiti: Notion flashcards](https://gridfiti.com/notion-flashcards/)
- Notionry tutorial: `if` on a difficulty select (easy / medium / hard) adds the corresponding number of days to the review date; with no selection the date stays unchanged. — [Notionry tutorial](https://www.notionry.com/tutorials/spaces-repetition-formulas-in-notion-tutorial)
- Prototion's "Spaced Repetition for Students" uses **one review checkbox per review**; the formula changes automatically depending on which box is checked. — [Prototion](https://www.prototion.com/notion-template/Spaced-Repetition-for-Students)
- Another fixed-interval Notion template uses session checkboxes and nested `dateAdd` calls, adding 1, 3, 7 or 15 days depending on which checkbox is ticked. A Gumroad template uses five repetitions at **3, 7, 14, 30 and 40 days**. The exact template pages were not identified in the extracts. — search extracts citing [realdoji Gumroad](https://realdoji.gumroad.com/l/basicspacedrepetitiontemplate) and [jonbot Gumroad](https://jonbot.gumroad.com/l/spaced-repetition) *(which listing has which interval scheme is unverified)*
- A generic button-plus-formula pattern: a button updates "Date Reviewed" and a "Days Between Repeats" number; the formula is `dateAdd(prop("Date Reviewed"), prop("Days Between Repeats"), "days")`. — the search extract did not clearly name the page; it appeared in results with [The Eudaimon](https://theeudaimon.com/a-new-way-to-do-spaced-repetition-in-notion-using-buttons/) and [21notion](https://21notion.com/en/blog/notion-automation-spaced-repetition) *(exact source page unverified)*

**Automation-based (paid plan) approach**
- 21notion: a "Check-in" **Button + database Automation** that uses function **variables** (`dateAdd` + `toNumber`) to compute the next check-in date. Each check-in is logged as a **sub-item**, and the parent gets the new "Next check-in date" and an updated completion count, without creating new pages each time. — [21notion: Notion Automation Tutorial – Spaced Repetition](https://21notion.com/en/blog/notion-automation-spaced-repetition)
- A recurring-tasks guide shows a button action `This page.Due.dateAdd(This page.Recur Interval, "days")` and notes that pasting formulas into automations didn't work at the time of writing, so they had to be typed in. — [Matthias Frank / Thomas Frank recurring tasks guides](https://thomasjfrank.com/notion-automated-recurring-tasks/) *(the extract did not say which of the two guides contained the note)*

**Leitner and other gallery templates**
- Free "Notion Revision Assistant": flashcards powered by the Leitner system and spaced repetition (7 ratings). — [Gumroad: apurplenotion](https://apurplenotion.gumroad.com/l/revisionassistant-notion)
- A paid "Ultimate Leitner System Template" at $5 with 24 ratings appeared in search results, but its exact URL was not identified (see Gaps).
- Other gallery SRS templates confirmed to exist: "Spaced Repetition Planner" by Aurea Ratio Design (next review date automatically calculated); "Spaced Repitition Flashcard System" by Tom (claims to integrate Anki's SRS); "Spaced Repetition Flash Card Template" by Zheng (custom review frequency per card); "SmartRecall – Simple & Customizable Spaced Repetition Flashcards" by ylhdev. — [Planner](https://www.notion.com/templates/spaced-repetition-planner); [Tom](https://www.notion.com/templates/spaced-repitition-flashcard-system); [Zheng](https://www.notion.com/templates/flash-card); [ylhdev](https://www.notion.com/templates/smartrecall-simple-customizable-spaced-repetition-flashc)
- A free Gumroad flashcard template offers a toggle to reveal the answer plus an archive page for mastered cards. — [Gumroad: danter flashcard template](https://danter.gumroad.com/l/flashcard-template) *(which Gumroad listing has this feature is unverified)*

**Anki export**
- The **2anki** Notion connection converts **toggle blocks into question/answer flashcards** (it also supports cloze deletions). Workflow: sign in at 2anki.net (free account) → Connect Notion → paste a page URL → Convert → download an **.apkg** to import into Anki. A one-off export is a static snapshot; continuous updates rely on the hosted service polling Notion pages every few minutes. — [Notion: 2anki connection](https://www.notion.com/connections/2anki)

**Plan availability (Free vs Plus)**
- **Database buttons are available on all plans**, but **certain button actions are paid-only**. The help page marks Slack notifications as Plus/Business/Enterprise only; a third-party guide also lists Gmail and webhook actions as paid. — [Notion Help: Database buttons](https://www.notion.com/help/database-buttons); [Sparxno: Notion buttons](https://www.sparxno.com/blog/notion-buttons)
- **Database automations are available on paid plans** only. **Button actions can trigger database automations.** — [Notion Help: Database automations](https://www.notion.com/help/database-automations)

### Inferences
- **Simplest for ADHD (recommended mechanism to adopt):** a single "Tarjetas" database with a Date "Próximo repaso", a Number "Intervalo (días)", and **two database-button properties**, "Lo sabía" (e.g., interval × 2 or the next Fibonacci step, Próximo repaso = today + interval) and "No lo sabía" (interval = 1, Próximo repaso = tomorrow). Add one view "Repasar hoy" filtered on Próximo repaso ≤ today. This copies the binary design of Memory and The Eudaimon, runs on the **Free plan** (buttons with edit-property actions; the Slack/Gmail/webhook actions are not needed), and needs no automations. A 3- or 6-level rating scale (Eudaimon, Total Recall) adds a decision on every card. The checkbox-per-review design (Prototion) adds visual clutter and does not adapt to performance.
- No gamification is needed: none of the mechanisms above depend on streaks or points; that is a design choice in each template.
- **Answers in the page body or in a toggle** (Eudaimon / Stelzel pattern) keep the card view uncluttered. Using **toggle blocks** for Q/A also keeps the cards **2anki-compatible**, so Carlos can move to Anki later without rewriting.
- Philipp Stelzel's Gumroad listing and the gallery page "spaced-repetition-flashcards-2" are probably the same template: the titles match ("Anki-like cards for spaced repetitions"), and the Stelzel search returned the gallery page first. This is not confirmed.

### Gaps
- Could not open any template to see exact property names, formula text or button configurations (network policy blocked notion.com and gumroad.com fetches).
- Price of "Memory" and of Total Recall not confirmed; the "spaced-repetition-flashcards-2" gallery price is contradictory ($29 / Free / $7 seen on the page).
- "Ultimate Leitner System Template" ($5, 24 ratings): the creator and exact URL were not identified in search results.
- Whether any 2025–2026 template replaced formula-only logic with button "edit property → formula" actions was not confirmed. Most button-based sources found are 2023–2025.
- No primary source confirmed Leitner-style "boxes" implemented as a select property with automatic promotion; only the free Revision Assistant claims Leitner.

---

## 2. What are the most recognized student Kanban / project templates, and what makes them "well developed"?

### Takeaway
The recognized baseline is a **two-database Projects ↔ Tasks** design (Notion's official "Projects & Tasks" and Thomas Frank's free "Ultimate Tasks") with board, table, timeline and "Today / Next 7 days" views, **sub-tasks via relations/sub-items**, and **dependencies**. For a thesis, several gallery templates track **chapters as database items** with status, due date, advisor feedback and word-count targets. No source showed native **WIP limits** in Notion boards.

### Cited Findings
- **Notion "Projects & Tasks" (official):** third-party reviews describe it as two connected databases, **Projects and Tasks**, with Kanban, table and timeline views. — [Bullet.so 2026 roundup](https://bullet.so/blog/best-notion-templates-for-project-management/); [Sync2Sheets 2026 roundup](https://sync2sheets.com/blog/notion-project-management-templates/)
- Notion's help guide: **sub-tasks and dependencies are built on relation properties**. Sub-items are turned on from the database menu (Sub-items), and **dependencies are drawn by dragging between tasks in Timeline view**, where they are displayed. — [Notion Help: Sub-tasks and dependencies](https://www.notion.com/help/guides/tasks-manageable-steps-sub-tasks-dependencies)
- One third-party guide claims Notion doesn't draw dependency lines automatically, which conflicts with Notion's help page. The guide is likely outdated. — [ONES blog](https://ones.com/blog/setting-up-a-notion-project-and-task-management-template-checklist/) vs [Notion Help](https://www.notion.com/help/guides/tasks-manageable-steps-sub-tasks-dependencies)
- Notion's Kanban blog describes Agile templates that break projects into smaller tasks shown in a **sprint** timeline. The official Projects & Tasks template was not confirmed to include sprints; a separate "Projects, Tasks & Sprints" template is mentioned by one source. — [Notion blog: 6 Kanban board templates](https://www.notion.com/blog/kanban-board-templates)
- **Thomas Frank – Ultimate Tasks (free):** quick capture to an **Inbox**, **Today** and **Next 7 Days** views, **sub-tasks and recurring tasks**, and **Trello-style boards** for larger projects. — [Thomas Frank: Ultimate Task and Project Management Template](https://thomasjfrank.com/templates/task-and-project-notion-template/); [Thomas Frank free templates](https://thomasjfrank.com/templates/)
- His full build tutorial describes a **Project area with kanban boards** and a **Timeline area** built on Notion's Timeline view. — [Thomas Frank: Build a complete task manager](https://thomasjfrank.com/notion-task-manager-full-tutorial/)
- **Ultimate Brain** (paid; includes Ultimate Tasks plus notes, etc.): its docs say it **supports only one level of sub-tasks "due to core Notion limitations"** and avoids Notion's native Sub-items feature. — [Ultimate Brain docs: Tasks database](https://thomasjfrank.com/docs/ultimate-brain/databases/tasks/); [Ultimate Brain](https://thomasjfrank.com/brain/)
- **Thesis / chapter tracking:**
  - "Literature Review & Thesis Tracker" by Linda: chapter tracking with **priority, status, advisor feedback and due dates**, aimed at master's and PhD students. — [Notion gallery](https://www.notion.com/templates/literature-review-and-thesis-tracker)
  - "Masters Thesis" by nx1t14: progress tracker adaptable to bachelor's, master's or PhD work, with **adjustable word-count targets**; reviewers call it well organized and easy to modify. — [Notion gallery](https://www.notion.com/templates/masters-thesis)
  - "Writing Assignment Word Count Tracker": chapter and daily word-count progress (not a full thesis system). — [Notion gallery](https://www.notion.com/templates/writing-assignment-word-count-tracker)
  - "Complete PhD Work Dashboard" (Gumroad, **$10.99**): Kanban board + calendar + Gantt chart, with subpages for thesis writing, coursework and literature summaries. — [Gumroad: phdtemplatedev](https://phdtemplatedev.gumroad.com/l/complete-phd-dashboard)
- **Semester setup:** Notion has an official guide for organizing a semester (courses, assignments). — [Notion Help: Get organized for a new semester](https://www.notion.com/help/guides/get-organized-for-a-new-semester-with-notion)
- **WIP limits:** no Notion-specific source was found. In other tools, WIP limits are often only visual warnings (e.g., Adobe Workfront). — [Adobe Workfront WIP limit](https://experienceleague.adobe.com/ja/docs/workfront/using/agile/kanban/work-in-progress-limit-on-the-kanban-board)

### Inferences
- "Well developed" in these templates means: (a) **Projects ↔ Tasks relation** with rollup progress; (b) **several views over one Tasks DB** (Inbox, Today, Next 7 days, board by status, timeline); (c) **sub-tasks** (one level is enough, following Thomas Frank's reasoning); (d) **dependencies** in timeline view for thesis milestones; (e) **recurring tasks**; (f) **chapter-as-item** tracking for the thesis, with status, due date, supervisor feedback and a word-count target.
- For Carlos's hierarchy (Programa > Curso > Módulo > Clase), the Tasks DB should relate to **Curso** (and optionally **Clase**) rather than being a separate per-course board. A board grouped by Status, sub-grouped or filtered by Curso, gives a per-course Kanban without duplicating databases.
- A **WIP limit** can be approximated without automations: a board view filtered to "In progress" with the column count visible, or a "Today" view limited to a small number of items. This is unverified against current Notion docs and is offered as a design idea only.
- For ADHD, a single "Today" view with few items and Inbox capture (Thomas Frank pattern) matters more than sprints. Sprints add planning overhead.

### Gaps
- Exact property list of Notion's official "Projects & Tasks" template and its gallery URL were not captured (could not open notion.com).
- Ultimate Brain's current price was not verified from a primary source (one third-party snippet said $129; not attributable to a specific page).
- No source documents native WIP limits or column-count caps in Notion boards.
- Prices for the Linda and nx1t14 thesis templates are not confirmed.

---

## 3. What are the most recognized lecture-notes / Cornell templates in Notion?

### Takeaway
Notion's gallery has several Cornell templates. All share the **Cues/Questions – Notes – Summary** layout, and the most useful ones store notes in a **database tagged by course** ("Class Notes", "AI Class Notes", "Course Tracker"). None found combines recordings, transcripts and auto-generated review questions out of the box. Carlos's Fireflies → Claude pipeline would fill that gap by writing into a Cornell-shaped class page.

### Cited Findings
- **"Cornell Notes" (notion.com/templates/cornell-notes):** includes a **Table of Contents, an Important memo, Questions & Cues, Notes and Summary** sections. Its "More by" link points to *cherrypicked designs*, so that is the probable creator *(unverified)*. — [Notion: Cornell Notes](https://www.notion.com/templates/cornell-notes)
- **"Class Notes" (class-notes-550):** a Cornell-based template that organizes notes into **Cue, Note-Taking and Summary** sections; lecture notes are kept in one database with properties for course details. — [Notion: Class Notes](https://www.notion.com/templates/class-notes-550)
- **"AI Class Notes" (by Notion):** uses AI to **generate concise summaries of lectures**. — [Notion: AI Class Notes](https://www.notion.com/templates/ai-class-notes)
- **"Course Tracker":** tracks lecture info, weekly learnings, notes, readings, labs and homework; includes a **syllabus page, learning goals, grade calculator and quick links**. — [Notion: Course Tracker](https://www.notion.com/templates/course-tracker)
- **"College Notes"** also exists in the gallery. — [Notion: College Notes](https://www.notion.com/templates/college-notes)
- Other gallery Cornell templates: **Kavyansh G** (free; each page divided into cues, notes and summary), **StudioB "Aesthetic Cornell Notes"** (Cues, Notes, Summary), **vasco**. — [Kavyansh G](https://www.notion.com/templates/cornell-note-taking-method-704); [StudioB](https://www.notion.com/templates/aesthetic-cornell-notes); [vasco](https://www.notion.com/templates/cornell-note); roundup: [Super.so: 9 best Cornell templates 2026](https://super.so/templates/notion-cornell-notes-templates)
- Gumroad Cornell variants with useful mechanisms:
  - Exsequor (free): **automatically sorts important notes and shows whether they have been reviewed**. — [Gumroad: exsequor](https://exsequor.gumroad.com/l/cornellnotes)
  - Skylarxzy: Cornell dashboard that **includes a flashcard system**. — [Gumroad: skylarxzy](https://skylarxzy.gumroad.com/l/cornell-template-notion-dashboard)
  - Mirsdesk (free): notes can be downloaded as PDF, then cleared for reuse. — [Gumroad: mirsdesk](https://mirsdesk.gumroad.com/l/cornellnotesnotiontemplate)
  - "Premium Class/Course, Assessment/Grade, Lecture and Content Tracker" lets you **track how many times you have reviewed each class-notes page**. — [Gumroad: perfectimprovement](https://perfectimprovement.gumroad.com/l/classcollegetracker)
- Design guidance: keep a narrow left column for **keywords, questions and recall prompts**, a right column for lecture notes, and a summary at the bottom. — [Notion4Teachers: digital Cornell notes](https://www.notion4teachers.com/blog/create-notion-digital-cornell-notes)
- A notes-template guide recommends a dedicated **summary** section plus a **follow-up / action items** section, and keeping to **5–7 properties maximum**. — [Notelyn: Notion note-taking template](https://www.notelyn.com/blog/notion-note-taking-template) *(attribution among the roundup results is unverified)*

### Inferences
- Adopt the **"Class Notes" pattern (Cornell inside a database page)** for Carlos's **Clase** database: properties for Curso/Módulo relation, date, Fireflies recording link, Drive/YouTube links (or a relation to a Recursos DB), Keywords (multi-select or relation to a Conceptos DB), and Estado de notas. The page body gets fixed headings: *Preguntas/Claves* (cue column), *Notas*, *Resumen*, *Preguntas de repaso*. A fixed heading structure gives Claude stable anchors to fill via the API.
- Notion's two-column layout is not reliable to fill programmatically. A **stacked layout** (Cues → Notes → Summary → Questions) is easier for an API-driven system and reads the same on mobile (inference).
- Two useful mechanisms to borrow from the Gumroad variants: the **"reviewed?" flag / review counter** on class pages (Exsequor, perfectimprovement), and **flashcards linked to the notes** (Skylarxzy). Carlos's review questions can become cards in the SRS database, related back to the Clase page.

### Gaps
- Creators and prices of "Cornell Notes", "Class Notes" (class-notes-550) and "College Notes" were not confirmed. "AI Class Notes" is attributed to Notion in the search title.
- Whether "AI Class Notes" requires a Notion AI add-on or plan (versus Free) was not verified.
- No template found integrates meeting-recorder transcripts (Fireflies) or auto-generated review questions; a "Cornell Command Center" ($19, with printable templates) was mentioned in one extract but its URL/creator was not identified.

---

## 4. Which mechanisms can be automated via the API (e.g., Claude creating cards and setting review dates)?

### Takeaway
Through the Notion API, Claude can **create pages (cards, class notes, tasks), write normal properties (dates, numbers, selects, relations) and write page content**. It **cannot press, create or configure buttons**, and **formula values are read-only** (only the expression can be changed at the schema level). The robust split: Claude creates cards with an initial "Próximo repaso" date and relations; Carlos reviews in the Notion UI using buttons (Free plan). Optionally, Claude does the scheduling itself by writing the next date directly, which makes paid automations unnecessary.

### Cited Findings
- **Buttons are not API-operable:** a Button property returns `button: {}`; the API does not expose its actions or let you press it by updating a page. — [Notion API: Page property values](https://developers.notion.com/reference/page-property-values)
- **Buttons cannot be created or changed via schema writes:** the API ignores button settings, does not create a Button property, and does not change an existing one. — [Notion API: Data source properties](https://developers.notion.com/reference/property-object)
- **Button blocks** appear as `type: "unsupported"` with `block_type: "button"` (informational only, no content). — [Notion API: Block](https://developers.notion.com/reference/block)
- **Formulas are read-only** as values; the expression can be changed through *Update a data source*. — [Notion API: Page property values](https://developers.notion.com/reference/page-property-values)
- A formula or rollup can return `type: "unsupported"` when it depends on **too many related pages or nested calculations**; retrying doesn't help, and the fix is to reduce the related pages or simplify. — [Notion API: Page property values](https://developers.notion.com/reference/page-property-values)
- **Database automations are paid-only; buttons are on all plans; button actions can trigger database automations.** — [Notion Help: Database automations](https://www.notion.com/help/database-automations); [Notion Help: Database buttons](https://www.notion.com/help/database-buttons)
- **Anki export:** 2anki converts toggle blocks to Q/A cards and outputs .apkg; the hosted service can poll Notion pages for updates. — [Notion: 2anki connection](https://www.notion.com/connections/2anki)

### Inferences
- **What Claude can automate (via API / Notion MCP):** create Clase pages from Fireflies transcripts; fill the Summary, Keywords and Review-questions sections; create one card per review question in the Tarjetas DB with relations to Clase, Curso and Concepto/Norma; set **Próximo repaso = class date + 1 day** and **Intervalo = 1**; create tasks in the Tasks DB related to Curso. Writing date, number, select and relation properties is standard API behavior *(the extracts above quoted only the formula and button sections of the docs, so per-type write support is from general API knowledge, not from these extracts)*.
- **What must be set up once by hand in the UI:** the button properties ("Lo sabía" / "No lo sabía") and their edit-property formulas, because the API can neither create nor press buttons. Duplicating a template that already has the buttons avoids building them.
- **Design implication:** keep the **scheduling state in plain properties** (Date "Próximo repaso", Number "Intervalo") that buttons update in the UI and Claude can read and write via the API. Avoid putting the next date only inside a formula: Claude can read a formula's output but cannot write it, and a plain date is easier to filter on.
- **Avoid deep rollup/formula chains** across many relations (e.g., counting all cards per Programa via several hops), since the API may return "unsupported" for those values. This matters if Claude reads rollups for dashboards.
- **No Plus plan needed** for the SRS if buttons update the properties directly. Automations (Plus) would only matter for side-effects such as logging each review as a sub-item (the 21notion pattern), which Carlos does not need.
- **Toggle-based Q/A** in card bodies (or a parallel toggle list on each Clase page) keeps a path to Anki via 2anki if Notion-based review ever proves insufficient.

### Gaps
- Whether a database button's "Edit property" action can set a Date to a **formula expression** (e.g., `now() + Intervalo days`) on the **Free** plan was not confirmed by a primary source. The help page confirms buttons work on all plans with only some actions paid (Slack confirmed; Gmail and webhook per a third-party source). Templates such as 21notion and the Thomas Frank recurring-tasks guide show formula-based button/automation edits, but the plan requirement for formula values inside button actions was not stated.
- Notion API rate limits and the current Notion MCP tool behavior for writing relations in bulk were not researched (out of scope).
