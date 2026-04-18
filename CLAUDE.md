# CLAUDE.md — Frontend Website Rules

## Always Do First
- **Invoke the `frontend-design` skill** before writing any frontend code, every session.

## Reference Images
- If a reference image is provided: match layout, spacing, typography, and color exactly.
- If no reference image: design from scratch with high craft (see guardrails below).
- Screenshot your output, compare against reference, fix mismatches, re-screenshot.

## Local Server
- **Always serve on localhost** — never screenshot a `file:///` URL.
- Start the dev server: `node serve.mjs` (serves the project root at `http://localhost:3000`)
- `serve.mjs` lives in the project root. Start it in the background before taking any screenshots.
- If the server is already running, do not start a second instance.

## Screenshot Workflow
- Puppeteer is installed at `C:/Users/nateh/AppData/Local/Temp/puppeteer-test/`
- **Always screenshot from localhost:**  
  `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary_screenshots/screenshot-N.png`
- Optional label suffix:  
  `node screenshot.mjs http://localhost:3000 label`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary_screenshots/` with the Read tool.
- When comparing, be specific:  
  “heading is 32px but reference shows ~24px”
- Check:
  - spacing/padding  
  - font size/weight/line-height  
  - colors (exact hex)  
  - alignment  

## Output Defaults
- Single `index.html` file, all styles inline, unless user says otherwise
- Tailwind CSS via CDN:
  `<script src="https://cdn.tailwindcss.com"></script>`
- Placeholder images:
  `https://placehold.co/WIDTHxHEIGHT`
- Mobile-first responsive

## Brand Assets
- Always check the `brand_assets/` folder before designing.
- If assets exist, use them. Do not use placeholders where real assets are available.
- If a logo is present, use it.
- If a color palette is defined, use those exact values.

## Anti-Generic Guardrails
- **Colors:** Never use default Tailwind palette (indigo-500, blue-600, etc.)
- **Shadows:** Never use flat `shadow-md`. Use layered, color-tinted shadows.
- **Typography:** Never use the same font for headings and body. Pair fonts.
- **Gradients:** Layer multiple radial gradients. Add grain/texture via SVG noise filter.
- **Animations:** Only animate `transform` and `opacity`. Never `transition-all`.
- **Interactive states:** Every clickable element needs hover, focus-visible, and active states.
- **Images:** Add gradient overlay (`bg-gradient-to-t from-black/60`) and color treatment.
- **Spacing:** Use intentional, consistent spacing tokens — not random Tailwind values.
- **Depth:** Surfaces should have a layering system (base → elevated → floating).

## Hard Rules
- Do not add sections, features, or content not in the reference.
- Do not “improve” a reference design — match it.
- Do not stop after one screenshot pass.
- Do not use `transition-all`.
- Do not use default Tailwind blue/indigo as primary color.