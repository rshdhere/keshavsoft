# KeshavSoft Mini-Site – Design Notes

This mini-site is built with Bootstrap 5 and a thin utility layer inspired by shadcn. The background is a patterncraft.fun-like crosshatch re-created using pure CSS gradients.

## Background with patterncraft.fun (inspired)
We render a subtle crosshatch inside a centered page frame so the outer canvas stays plain white.

```css
.page-frame {
  position: relative;
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1rem;
  background-image:
    repeating-linear-gradient(22.5deg, transparent, transparent 2px, rgba(75,85,99,.06) 2px, rgba(75,85,99,.06) 3px, transparent 3px, transparent 8px),
    repeating-linear-gradient(67.5deg, transparent, transparent 2px, rgba(107,114,128,.05) 2px, rgba(107,114,128,.05) 3px, transparent 3px, transparent 8px),
    repeating-linear-gradient(112.5deg, transparent, transparent 2px, rgba(55,65,81,.04) 2px, rgba(55,65,81,.04) 3px, transparent 3px, transparent 8px),
    repeating-linear-gradient(157.5deg, transparent, transparent 2px, rgba(31,41,55,.03) 2px, rgba(31,41,55,.03) 3px, transparent 3px, transparent 8px);
}
.edge-gradient { position:absolute; top:0; bottom:0; width:1px; pointer-events:none;
  background: linear-gradient(180deg, rgba(212,212,216,.5), #e5e7eb 60%, rgba(229,231,235,0));
}
.edge-left { left: 0; }
.edge-right { right: 0; }
```

- Adjust density by changing the 2px/3px/8px stops.
- Widen or narrow the framed area via `.page-frame { max-width: ... }`.

## shadcn-inspired structure and coloring (no Tailwind)
Bootstrap drives layout and components; a few CSS tokens echo shadcn’s neutral, crisp aesthetic.

```css
:root {
  --radius: 12px;
  --border: 1px;
  --border-color: #e5e7eb;
  --card-bg: #fff;
  --text: #0f172a;
  --muted: #64748b;
  --primary: #111827;
}
.card { border: var(--border) solid var(--border-color); border-radius: var(--radius); }
.shadow-soft { box-shadow: 0 1px 2px rgba(15,23,42,.04), 0 8px 24px rgba(15,23,42,.06); }
.btn-ghost { background: transparent; border: var(--border) solid var(--border-color); color: var(--text); }
.navbar-capsule .container { background:#fff; border:1px solid var(--border-color); border-radius:9999px; box-shadow:0 1px 2px rgba(15,23,42,.04),0 8px 24px rgba(15,23,42,.06); }
```

Guidelines borrowed from shadcn’s docs/examples:
- Neutral palette; hierarchy via borders and spacing.
- Soft shadows, rounded shapes, pill navbar.
- Tighter headline tracking; Inter for clean type.
- Build from tokens → utilities → components.

## Components created
Count: 8

1) Capsule Navbar – pill container, responsive collapse
2) Hero Section (video) – left text/actions, right 16:9 `hero.mp4`
3) Feature Card (x3) – icon badge, hover lift, link
4) Demo Modal – plays `hero.mp4` with controls
5) Learnings Card – “Bootstrap learnings” checklist (Home, About)
6) Services Card (x8) – services grid on About
7) Contact Form – validated form + friendly JS UX
8) Page Frame + Edge Gradients – layout wrapper + vertical lines

## Project structure
- `index.html`: capsule navbar, hero with video, features, demo modal, learnings card
- `about.html`: capsule navbar, hero-muted header, mission, learnings card, services grid, sidebar cards
- `contact.html`: capsule navbar, header, validated form

## Customize quickly
- Shape: `--radius`
- Borders: `--border-color` or set `.card { border: 0; }`
- Elevation: tweak `.shadow-soft`
- Frame width: `.page-frame { max-width: ... }`

## Run
Open `index.html` in a browser. All assets via CDN.

## Credits
- Background concept inspired by `patterncraft.fun`.
- Structure and coloring influenced by shadcn.
- Built on Bootstrap 5.
