# Instructions - WEB-014: Metro: Last Departure (Animated Gaming Landing Page)

These instructions tell you exactly what to build, in what order, and how it will be checked. Follow them precisely every item here maps directly to an item in the project's Acceptance Checklist. If something here is ambiguous, default to the stricter/more literal reading.

---

## 1. What you are building

A single-page, animated, responsive landing page for "Metro: Last Departure" a single-player survival-exploration game (zombie outbreak on a metro line). This is a static front-end page only. No backend, login, database, multiplayer, or live data of any kind.

"Online" in this project means the game is browser-accessible/downloadable via a gaming platform it does **not** mean multiplayer or community features. Do not add leaderboards, live player counts, rankings, or any social/community elements.

---

## 2. Page structure - build in this exact order

Build all 8 sections below, in this exact order. Do not add sections, remove sections, or reorder them.

1. Hero
2. Gameplay Features
3. Interactive Metro Map
4. Survivor Roster (Unlockable Character Classes)
5. Story Teaser (Intercepted Transmission)
6. Survival Mechanics
7. Endings Preview
8. CTA Footer

---

## 3. Section-by-section build instructions

### 3.1 Hero

Build in this element order, top to bottom:

1. Status bar / line-ID label with a pulsing indicator dot communicating "containment breach" status
2. Glitch-effect title: "METRO: LAST DEPARTURE"
   - Periodic RGB-split / clip-path glitch effect must be intermittent, not a constant/looping distortion
3. Game description line (directly below the title):
   > "A routine metro journey becomes a fight for survival after a mysterious outbreak contaminates the transit network."
   - Secondary text weight/size, smaller than the title supporting copy, must not compete visually with the title
   - Keep to 2 lines max on desktop
4. Primary CTA button: "Board The Train" pulsing animation
5. Scroll cue with animated indicator (e.g., animated arrow or bar)

Background: subtle moving tunnel-line pattern + ambient gradient glows (use the approved color palette only see Section 5).

### 3.2 Gameplay Features

4-card grid, in this orde

1. Explore The Metro Network
2. Survive The Outbreak
3. Solve Environmental Puzzles
4. Uncover The Conspiracy

Hover state on each card: left accent bar reveal + card lift animation.

### 3.3 Interactive Metro Map

Build an SVG-based map showing **one single connected route** not separate/disconnected markers. The four stations must sit along this route in this exact narrative order:

```
Central Station → Research Lab → Underground Tunnels → Final Departure Terminal
```

Requirements:

- A visible line/path connects all four stations in sequence (left-to-right or start-to-end)
- An animated "active flow" effect (dashed line animation) travels along the **entire** connected route not just isolated segments
- Hover or keyboard-focus on a station: glows the station node and reveals a tooltip with station-specific lore/status text
- Station danger coding:
  - Central Station neutral (green glow on hover/focus)
  - Research Lab danger (red glow on hover/focus)
  - Underground Tunnels danger (red glow on hover/focus)
  - Final Departure Terminaleutral (green glow on hover/focus)
- Must be fully keyboard-accessible: each station is tab-focusable, and the tooltip appears on focus (not just mouse hover)

Optional: section intro copy may be adjusted to reinforce the "journey" framing, e.g. "Follow the route hover or focus a station for a status report."

### 3.4 Survivor Roster (Unlockable Character Classes)

4 flip-cards, in this order:

1. Engineer
2. Medic
3. Security Guard
4. Hacker

Each card:

- **Front face:** class name, class number, points-to-unlock value
- **Back face** (revealed on hover/focus): ability description
- 3D flip animation on the Y-axis

Important framing note: these are unlockable classes that **one single player** progresses through and switches between over the course of the game. Do not write or imply any multiplayer-role framing (e.g., "your teammate's class," "squad," "co-op").

### 3.5 Story Teaser (Intercepted Transmission)

Terminal/log-style text block:

- Lines reveal sequentially on scroll (each line fades in with a delay not all at once)
- Color-coded by line type:
  - Normal log lines: green
  - Warning lines: red
  - System/dim lines: dim gray
- Blinking cursor after the final line

### 3.6 Survival Mechanics

4-item grid/list, in this order:

1.  Health System
2.  Infection Detection
3.  Resource Collection
4.  Metro Exploration

Each item: icon, short title, 1–2 line description. Subtle hover/reveal animation per item.

### 3.7 Endings Preview

4-tile grid, in this order:

1. Escape Ending
2. Sacrifice Ending
3. Conspiracy Ending
4. Bad Ending

Each tile's title/text is **blurred by default** and sharpens on hover. No spoiler text should be readable without interaction.

### 3.8 CTA Footer

- Large heading: "Can You Reach The Last Departure?"
- Single primary CTA button: "Play Now" pulsing animation
- No secondary buttons, no additional links beyond what's needed for a static page (e.g., basic footer text is fine, but no community/social links).

---

## 4. Animation requirements (apply across all sections)

- Every major section uses scroll-triggered reveal on first viewport entry: fade in + slight upward translate
- All interactive elements (cards, map stations, buttons) have hover **and** focus micro-interactions focus states must mirror hover states for accessibility
- `prefers-reduced-motion` must be respected: when set, all animations are disabled or significantly reduced (no glitch loops, no flip animations, no scroll-reveal motion content should simply be visible)
- No animation may cause layout shift or block text readability at any point

---

## 5. Visual specs - color palette (do not deviate)

| Purpose            | Color name       | Hex       |
| ------------------ | ---------------- | --------- |
| Background         | Near-black       | `#0A0C0D` |
| Panel background   | Dark gray        | `#111416` |
| Borders / dividers | Line gray        | `#1D2226` |
| Text primary       | Off-white        | `#D8E0DE` |
| Text dim/secondary | Muted gray-green | `#6F7A78` |
| Accent (signal)    | Signal green     | `#39FF8F` |
| Accent (hazard)    | Hazard red       | `#FF3B3B` |
| Accent (amber)     | Amber            | `#FFB238` |

Rules:

1. No purple, blue, or pink anywhere on the page.
2. Glows/shadows are allowed and expected for hover states keep them subtle, not oversaturated/neon-blown-out.
3. No light or white backgrounds anywhere.

---

## 6. Typography (do not deviate)

| Usage            | Font                                                          | Notes                             |
| ---------------- | ------------------------------------------------------------- | --------------------------------- |
| Headings/Display | Arial Narrow (or equivalent condensed sans), weight 900       | Uppercase, tight letter-spacing   |
| Body             | Courier New / monospace                                       | "System terminal" feel throughout |
| Eyebrows/Labels  | Same monospace, smaller size, letter-spacing 3–5px, uppercase |                                   |

Not allowed: decorative/script fonts, rounded friendly sans-serifs, plain default Helvetica/Arial for headings.

---

## 7. Technical requirements

- **Stack:** Vanilla HTML/CSS/JS, or React + Tailwind CSS your choice
- **Responsive:** Must work correctly down to 320px width. Metro map and feature grids reflow to single-column on mobile.
- **Browser support:** Latest Chrome, Edge, Firefox, Safari
- **Performance:** No heavy external libraries. Prefer CSS/SVG animation over JS animation libraries. A free library (GSAP free tier, AOS) is allowed only if it visibly improves polish not required.
- **Code quality:** Clean, commented, single-purpose files

### Not allowed

- Paid plugins or premium UI kits
- Backend, server, or database of any kind
- Authentication, user accounts
- Any multiplayer/community features: leaderboards, live player counts, rankings, social feeds
- Stock photography or AI-generated character art (use icons/emoji/SVG only)

---

## 8. Deliverables checklist

| #   | Item                    | Format                                               | Notes                              |
| --- | ----------------------- | ---------------------------------------------------- | ---------------------------------- |
| 1   | Landing page source     | `.html`, `.css`, `.js` (or `.jsx` + Tailwind config) | All 8 sections, fully functional   |
| 2   | Mobile-responsive build | Same files                                           | Verified at 320px                  |
| 3   | README.md               | `.md`                                                | Setup + local preview instructions |

### File naming

Format: `[PREFIX]_[item-name]_[version]_[YYYY-MM-DD].[ext]`
Example: `METRO_landing-page_v1_2026-06-14.html`

- kebab-case, no spaces, no alternate naming structures

### Folder structure

```
MetroLastDeparture_Landing/
  index.html
  styles.css (if separated)
  script.js (if separated)
  README.md
```

---

## 9. Scope boundaries

### Do

- Build all 8 sections, fully animated, in the specified order
- Match the dark metro/infection visual identity exactly (palette + typography above)
- Make the metro map and character cards fully keyboard-accessible
- Write placeholder copy in the established clinical/ominous tone where needed

### Do not

- Add sections beyond the 8 specified, or reorder them
- Change the color palette or typography system
- Add multiplayer, leaderboard, live player count, or any social/community feature
- Build backend, login, or database functionality
- Use stock photos or AI-generated character art

---

## 10. Pre-submission checklist (self-check before delivery)

- [ ] All 8 sections present, in the exact specified order
- [ ] Hero includes status bar, glitch title, game description line (between title and CTA), pulsing CTA, scroll cue
- [ ] Glitch hero animation is intermittent and loops correctly
- [ ] Metro map shows ONE connected route with stations in order: Central Station → Research Lab → Underground Tunnels → Final Departure Terminal
- [ ] Active-flow animation travels along the full route
- [ ] Map stations: correct danger/neutral color coding, hoverable AND keyboard-focusable, tooltips appear on both
- [ ] Character class cards (Engineer, Medic, Security Guard, Hacker) flip on hover/focus with correct front/back content
- [ ] Story teaser text reveals sequentially on scroll with correct color-coding and ending cursor blink
- [ ] Survival Mechanics section shows all 4 items with icons + descriptions
- [ ] Endings tiles (Escape, Sacrifice, Conspiracy, Bad) are blurred by default, sharpen on hover
- [ ] CTA Footer has the specified heading and single "Play Now" button only
- [ ] `prefers-reduced-motion` correctly disables/reduces all animations
- [ ] Fully responsive at 320px, 768px, and 1440px
- [ ] No console errors, no broken assets
- [ ] No multiplayer/community elements anywhere on the page
- [ ] Files follow naming convention and folder structure in Section 8

---

## 11. Final goal

When done, the page should feel like the front door to a tense, atmospheric single-player survival game system-glitch-driven, interactive, exploration-focused. A visitor should understand the premise (rerouted train, outbreak, conspiracy) within the first viewport, see the metro line as one continuous journey, understand the unlockable character classes and survival systems, know multiple endings exist without spoilers, and feel pulled toward "Play Now."
