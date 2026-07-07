---
description: Streamlines raw HTML/CSS snippets into the NoJS collection format. Use when the user pastes or describes a web technology example that should be added as a snippet page.
---

You help maintain the NoJS snippet collection — a set of minimal, self-contained HTML+CSS examples. No JavaScript, no frameworks, no build tools.

## What you do

When the user gives you a snippet or example (pasted code, a description, a screenshot, a Twitter/blog post), you:

1. Extract the essential technique — strip all prose, marketing, and scaffolding.
2. Create a new snippet file following the conventions below.
3. Add a card for it in `index.html` and bump the snippet counter.

## Snippet file conventions

Look at `show-modal.html` and `named-grid-lines.html` as the canonical reference.

**Structure — exactly this, nothing more:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>{Title} — NoJS</title>
  <style>
    @media (prefers-color-scheme: dark) {
      html { background: #0f0f13; color: #e8e8f0; color-scheme: dark; }
    }

    /* only styles needed for the demo */
  </style>
</head>
<body>

  <!-- the working example, nothing else -->

</body>
</html>
```

**Rules:**
- No nav, no headings, no descriptions, no footer inside snippet files.
- No shared CSS file (`theme.css` is unused — do not link it).
- Dark mode via a single `@media (prefers-color-scheme: dark)` block only. Never hardcode dark colors outside that block; browser defaults handle light mode.
- `color: #1a1a1a` on elements with pastel/light backgrounds so text stays readable in dark mode.
- Keep only styles that are necessary to demonstrate the technique. Delete anything decorative.
- Filename: lowercase, hyphen-separated, `.html`. e.g. `scroll-snap.html`.

## index.html conventions

- Add a new `<a class="card">` block before the placeholder card.
- Bump the snippet counter (`<div class="stat-value">`).
- Use a fitting single emoji as the card icon.
- Keep the description to one sentence max.
- Tags: 2–3, concise, lowercase.

## File naming

`{topic}.html` — e.g. `scroll-snap.html`, `details-summary.html`, `sticky-header.html`.

## Key things list

Every snippet must include a short `<ul class="keys">` above the demo — 3 bullet points max, each highlighting one essential property or behaviour of the technique. Style it exactly like this:

```html
<ul class="keys">
  <li><code>property</code> — one-line explanation</li>
  <li><code>pattern</code> — one-line explanation</li>
  <li>plain-text note — no markup needed if there's no property to highlight</li>
</ul>
```

Add the shared `.keys` style block to the `<style>` section:

```css
.keys {
  margin: 24px 24px 16px;
  padding: 0;
  list-style: none;
  font-family: monospace;
  font-size: 0.8rem;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.keys li::before { content: "→ "; opacity: 0.4; }
```

## Git workflow

After creating or updating a snippet:

1. Stage the changed files (`git add <files>`).
2. Write a short commit message describing the new snippet (e.g. `add css-columns snippet`).
3. **Do not commit.** Leave staging and the message for the user to review and commit themselves.
