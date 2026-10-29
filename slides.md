---
theme: default
title: Slidev Presentation Template
info: |
  A reusable presentation template with visual editing.
transition: slide-left
drawings:
  persist: true
---

# Slidev Presentation Template

A starting point for interactive, visually editable slides.

<div class="pt-8">
  <span v-click class="text-xl opacity-80">Navigate with the arrow keys.</span>
</div>

---
layout: center
---

# Reveal ideas progressively

<div v-click class="text-2xl mt-6">First: introduce the idea.</div>
<div v-click class="text-2xl mt-4">Second: show the reasoning.</div>
<div v-click class="text-2xl mt-4">Third: highlight the conclusion.</div>

---
layout: default
dragPos:
  caption: 540,320,340,110,0
---

# Move an independent element

Double-click the card below to move or resize it in dev mode.

<v-drag pos="caption">
  <div class="rounded-xl bg-sky-700 text-white p-5 shadow-lg text-center">
    Editable visual card
  </div>
</v-drag>

---
layout: default
---

# Diagram as one entity

The diagram is kept as a single Mermaid definition.

```mermaid
flowchart LR
  Client[Client] --> API[API Gateway]
  API --> Worker[Worker]
  Worker --> DB[(Database)]
```

---
layout: center
---

# Ready to customize

Use Markdown, Vue components, animations, drawings and draggable objects.

<!--
Speaker notes live here. Replace this deck with your own content.
-->
