# GPU Evolution: From Fixed-Function Pipelines to Massively Parallel AI Accelerators

**Virtual Exhibit — CSARCH2 | Term 3 AY 2025-2026 | De La Salle University - Manila**

---

## Group Information

| # | Full Name | GitHub Handle |
|---|-----------|---------------|
| 1 | Maria Fides Bancoro | @m-fides |
| 2 | Marc Jared Sean Ercia | @MarcErcia |
| 3 | Theodore Rodolfo III Garcia | @theoithinkk |
| 4 | Theon Schuyler Garcia | @SchuylerGYo |
| 5 | Nathaniel Singh | @Redaw-t |

---

## Project Overview

*GPU Evolution: From Fixed-Function Pipelines to Massively Parallel AI Accelerators* is an immersive, interactive virtual museum exhibit tracing the architectural journey of the graphics processing unit — from its origins as dedicated display hardware to its modern role as the computational engine powering artificial intelligence.

Visitors are guided through five landmark eras in GPU development: Fixed-Function Hardware, Programmable Shaders, Unified Shader Architecture, GPGPU & CUDA, and the AI Accelerator Era. Each era is framed around a compelling narrative arc: the limitations that drove innovation, the architectural breakthroughs that followed, and the ripple effects felt across graphics rendering, scientific computing, and machine learning. Rather than presenting history as a sequence of specifications, the exhibit tells the story of how relentless demands for programmability, parallelism, and efficiency continuously reshaped the way GPUs were designed and built.

The exhibit integrates three core interactive experiences: a **3D GPU Viewer** allows visitors to inspect era-defining hardware models up close; an **Interactive Timeline** places architectural milestones side by side for direct specification comparisons; and a **Trivia Quiz** reinforces learning in an engaging, low-stakes format.

---

## Five Eras of GPU Evolution

| Era | Period | Key Milestone |
|-----|--------|---------------|
| Fixed-Function Hardware | 1990s | Dedicated graphics pipelines; no programmability. E.g., 3dfx Voodoo, NVIDIA RIVA TNT. |
| Programmable Shaders | Early 2000s | Vertex & pixel shaders introduced. DirectX 8/9 era. E.g., NVIDIA GeForce 3. |
| Unified Shader Architecture | 2006–2010 | Single programmable core handles all shader types. E.g., NVIDIA Tesla (G80), AMD Radeon HD 2000. |
| GPGPU & CUDA Era | 2010s | General-purpose GPU computing. CUDA/OpenCL ecosystems. E.g., NVIDIA Kepler, Maxwell. |
| AI Accelerator Era | 2020s–now | Tensor cores, ray tracing, transformer-optimized silicon. E.g., NVIDIA Hopper H100, AMD RDNA 3. |

---

## Tech Stack

| Layer | Technology | Notes |
|-------|------------|-------|
| Runtime | Node.js 26 | Required per project specs; LTS stability. |
| Framework | Astro 6 | Static-site generation with island architecture; forked from provided template. |
| Content | `.mdx` files | MDX (Markdown + JSX) for rich, component-embedded content pages. |
| Interactive UI | React 18 (`.jsx`) | All interactive components built as React islands embedded in `.mdx`. |
| 3D Rendering | Three.js / React Three Fiber | Powers the 3D GPU Viewer; GLTF/GLB model format with Draco compression. |
| Shader Preview | WebGL / WebGPU | Powers the Shader Code Live Preview component; runs entirely in-browser. |
| Styling | Tailwind CSS v4 | Utility-first CSS; follows the central museum template style guide. |
| Icons | Lucide React | Consistent icon system for UI controls, era tags, and tooltip pins. |
| Version Control | Git / GitHub | Repository forked from template; all docs, plans, and feedback tracked via commits. |
| Hosting | GitHub Pages | Static output deployed via `astro build`; automated via GitHub Actions on push to `main`. |
| Responsive | CSS Grid / Flexbox | Mobile-first breakpoints; timeline scrolls horizontally on desktop, vertically on mobile. |

### Mobile Responsiveness

All components are built mobile-first:

- **GPU Architecture Trivia Quiz:** Question cards stack vertically and fill the screen width on mobile (`<640px`). Answer buttons expand to full width for easy tap targets (`min-height: 48px`). Score card collapses to a single centered summary panel.
- **3D GPU Viewer:** Canvas resizes to full viewport width on mobile. Era navigator buttons move to a bottom drawer to avoid covering the model. Tooltip panels anchor to the bottom of the screen. Touch gestures replace mouse controls: one-finger drag to orbit, pinch to zoom, two-finger drag to pan.
- **GPU Spec Timeline Explorer:** Horizontal scroll on desktop (`≥768px`); switches to a vertical stacked card layout on mobile. Expanded spec cards go full-width. Era filter buttons collapse into a horizontally scrollable pill row.

---

## Interactive Components

| # | Component | Type | Summary |
|---|-----------|------|---------|
| 1 | GPU Architecture Trivia Quiz | Quiz | Knowledge check covering all five eras. Era-tagged questions; incorrect responses reveal a short explanation. |
| 2 | 3D GPU Viewer | 3D Model | Inspect era-defining GPU cards up close. Rotate, zoom, and pan freely; X-Ray view exposes internal components with annotated tooltips. |
| 3 | GPU Spec Timeline Explorer | Interactive Timeline | Horizontal scrollable timeline spanning all five eras. Clickable nodes expand spec cards (transistor count, VRAM, memory bus, TDP, notable features). Supports side-by-side comparative view. |

### GPU Architecture Trivia Quiz

**Purpose:** Test user understanding after browsing the exhibit.

- **Era-tagged questions** — each question is labeled with its GPU era.
- **Multiple choice** — 4 options per question; wrong answers surface a short explanation.
- **Score card** — per-era breakdown to motivate revisiting weak spots.
- **Randomized question pool** — 30 questions (6 per era); each session presents 15 randomly selected questions (3 per era minimum guaranteed), shuffled on every load. Answer options are also randomized per question.

### 3D GPU Viewer

**Purpose:** Provide an immersive, hands-on look at the hardware that defined each architectural generation.

- **Orbit controls** — click and drag to rotate, scroll to zoom, right-click to pan.
- **Era navigator** — cycle through 5 era-defining GPU cards: 3dfx Voodoo2 (Fixed-Function), NVIDIA GeForce3 Ti 500 (Programmable Shaders), NVIDIA GeForce 8800 GTX (Unified Shader), NVIDIA GTX 680 Kepler (GPGPU & CUDA), NVIDIA RTX 4090 (AI Accelerator).
- **X-Ray view** — toggle to make the outer layer semi-transparent and reveal internal components.
- **Component tooltips** — accessible via X-Ray view; click pins to read descriptions of the GPU die, VRAM, power connectors, and more.

### GPU Spec Timeline Explorer

**Purpose:** Visually trace the progression of GPU hardware specifications across all five eras.

- **Era nodes** — each landmark GPU is a clickable node that expands a full spec card (transistor count, VRAM, memory bus width, TDP, notable architectural features).
- **Era filter buttons** — focus on a single era by dimming all others.
- **Spec card animations** — 500ms cubic-bezier ease-out entrance; smooth collapse on dismiss.
- **Comparative view** — select two nodes simultaneously to display spec cards side by side.
- **Responsive layout** — horizontal scroll on desktop (`≥768px`), vertical stacked cards on mobile (`<640px`).

---

## Style Guide

### Design Philosophy

The exhibit uses a high-contrast dark palette to evoke the aesthetic of digital displays and hardware monitoring interfaces, reinforcing the GPU's dual identity as both a precision engineering component and a creative tool for visual media. Grid systems, monospace typography for technical data, and repeating parallel motifs deliberately mirror the parallel architecture of the hardware being discussed. All color and spacing decisions below are finalized and serve as the source of truth for all component implementations.

### Style Tokens

| Element | Value | Usage |
|---------|-------|-------|
| Primary Color | `#00E5FF` / cyan-400 | Era highlights, active states, key callouts |
| Secondary Color | `#7B61FF` / violet-500 | AI era accent, interactive hover, quiz feedback |
| Background | `#0A0A0F` | Page-level background |
| Surface Cards | `#141420` | Era cards, quiz panels, viewer container |
| Primary Text | `#F0F0F5` | Body copy, headings, labels |
| Secondary Text | `#8888A0` | Metadata, dates, captions, disabled states |
| Typography (Headings) | Space Grotesk 500/700 | Era titles, section headers, component names |
| Typography (Body) | Inter 400/500, 16px / 1.7 | Exhibit copy, descriptions, quiz questions |
| Typography (Technical Data) | JetBrains Mono 400, 13px | Shader code, spec numbers, CUDA examples, table values |
| Border Radius | `sm: 4px` / `md: 8px` / `lg: 16px` | sm → tags/chips; md → cards, inputs; lg → major panels |
| Grid System | 12-col, 24px gutter, 40px margin | Timeline: full-width scroll; components: 6-col or 12-col spans |
| Spacing Scale | 4 · 8 · 16 · 24 · 40 · 64 px | 4px intra-element; 16–24px intra-card; 40–64px between sections |
| Shadows | `0 0 0 1px rgba(0,229,255,0.12)` | Subtle cyan glow-border on cards |
| Animation Duration | fast: 150ms / standard: 300ms / entrance: 500ms | hover feedback / transitions / era card reveal |
| Animation Easing | `cubic-bezier(0.16, 1, 0.3, 1)` | Snappy ease-out for all transitions |
| Component Borders | `1px solid rgba(255,255,255,0.08)` | Default card borders; inactive timeline nodes |
| Interactive Feedback | Cyan glow + `scale(1.02)` | Hover states; correct answer → green glow; wrong → red flash |
| Timeline Accent | Gray → Cyan gradient | Past eras desaturate; active era glows cyan |
| Responsive Breakpoints | mobile: `<640px` / tablet: `640–1024px` / desktop: `≥1024px` | Matches Tailwind sm/md/lg |

### Accessibility

The exhibit targets WCAG 2.1 AA compliance throughout. The following requirements are binding for all component implementations:

- **Contrast Ratios:** Primary text (`#F0F0F5`) on background (`#0A0A0F`) yields 16.9:1, well above the 4.5:1 AA minimum. Secondary text (`#8888A0`) on background achieves 5.1:1.
- **Focus States:** All interactive elements have a visible `2px solid #00E5FF` focus ring with 2px offset, replacing the browser default.
- **ARIA Labels:** All icon-only buttons carry descriptive `aria-label` attributes. The 3D viewer canvas exposes `role="application"` with a text alternative summarizing the currently displayed GPU card.
- **Reduced Motion:** All animations respect `prefers-reduced-motion: reduce` — entrance animations and transitions are disabled, replaced with instant state changes.
- **Keyboard Navigation:** The timeline, quiz, and era navigator are fully operable via keyboard. The 3D viewer supports arrow-key orbit and `+`/`-` zoom as alternatives to mouse controls.
