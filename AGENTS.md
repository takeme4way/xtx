# AGENTS.md

Personal practice repo for a web-design course ("高级网页设计"). Static HTML demos only — no build, package manager, tests, or lint.

## Structure

- `index.html` — course index page; the only meaningful entry point. All other HTML files are standalone per-topic demos.
- Numbered files (`1-1.html` … `10-4.html`) follow the course topic order (selectors, box model, flexbox, transitions, animation). Some filenames are Chinese; all HTML is UTF-8 with `lang="zh-cn"`.
- `img1/` — images referenced by the HTML files.
- `css.css` — shared styles (small; most demos use inline `<style>`).
- `HelloJava.java` — scratch file for a JDK check, not part of the site. Ignore it.

## Conventions

- All CSS class names, id names, and JS variables must start with `xin`.
- Before executing any prompt, append the prompt (timestamp, model name, prompt text) to `xin_prompt.md` — never overwrite it.
- Every newly created HTML file must be added to the link list in `index.html`.

## Working here

- Preview by opening files directly in a browser (`start <file>` on Windows). No dev server or install step exists.
- When editing, match the existing style: Chinese comments/UI text, inline `<style>` per file, no external JS or CSS frameworks.
- Do not introduce build tooling or restructure files unless asked — `index.html` links to the current filenames.
