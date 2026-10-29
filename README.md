# slidev-tplt

Reusable [Slidev](https://sli.dev/) presentation template with progressive reveals, a draggable visual card, Mermaid and live drawings.

## Quick start

Requires Node.js and npm.

```bash
npm install
npm run dev
```

Open the local Slidev page, edit `slides.md`, and see your changes immediately.

## Commands

- `npm run dev` — start the presentation editor.
- `npm run build` — generate a static presentation.
- `npm run export` — export slides (may require additional browser dependencies).

## Included examples

- **Progressive reveal** using `v-click`.
- **Draggable card** using `<v-drag pos="caption">` and `dragPos` in slide frontmatter.
- **Mermaid flowchart** rendered as one diagram.
- **Live annotations**, with drawings persistence configured.
- **Slide transitions** through the `transition` frontmatter option.

In development mode, double-click a draggable element to adjust its position, size, and rotation. These edits are written back to the source. Preserve `dragPos` entries when revising the slide content.

For animations, markup, diagram choices and Git commit attribution, see [AGENTS.md](AGENTS.md).

## Workflow

1. Ask a coding agent to generate content and visual components.
2. Edit object positions directly in the running Slidev presentation.
3. Review `slides.md` changes and commit them.
4. Keep structured Mermaid diagrams as one movable object when visual repositioning is needed.

This is an initial foundation, not a complete component library. More examples can be added as the presentation system evolves.
