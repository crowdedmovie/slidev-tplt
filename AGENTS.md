# Agent instructions — Slidev template

## Purpose
Maintain a reusable Slidev presentation template. Prefer native Slidev capabilities and small, reusable Vue components over bespoke frameworks.

## Commits
- Commit directly to `main` when authorized and branch rules permit.
- Every new commit MUST end with this exact trailer, separated from the subject/body by a blank line:
  `Co-authored-by: Codex <noreply@openai.com>`
- Never amend or rewrite unrelated history to apply this convention.
- Keep commits focused and descriptive.

## Presentation quality
- Favor concise, readable slides with good contrast and ample negative space.
- Use `v-click` / `v-clicks` for progressive disclosure where it improves the explanation.
- Use Slidev slide transitions and `v-motion` sparingly and intentionally.
- Use `v-mark` for prepared emphasis and integrated drawings for live annotation.
- Use Shiki Magic Move for evolving code; Monaco Runner only for meaningful runnable demos.
- Use Mermaid for whole, self-contained diagrams.

## Layout and visual editing
- Use normal layouts / grid / flex for headings and flowing text.
- Use `<v-drag>` for independent visual objects (complete diagrams, illustrations, callouts, code panels, logos).
- Store and preserve draggable coordinates in the slide's `dragPos` frontmatter.
- Do NOT reset, overwrite, or normalize existing `dragPos` entries during unrelated edits.
- Do not break internal Mermaid layout into independently draggable nodes unless explicitly requested.
- Prefer reusable components for repeated designs and editable visuals.

## Verification
- Check Slidev compilation when modifying the presentation.
- Check animation click steps, presentation navigation, dragged positions and diagram rendering.
- Document any limitations or manual steps in README.
