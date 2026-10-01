---
name: Mia by Tanishq · Sign In / Sign Up
description: A light, one-question-at-a-time concierge for phone-first sign in, sign up and granular consent.
colors:
  rose-primary: "#D14A61"
  rose-pressed: "#C4435A"
  rose-ink: "#B23A50"
  blush-50: "#FCF1F3"
  blush-100: "#F7DDE3"
  blush-200: "#EFBFCA"
  mauve-text: "#4A4447"
  mauve-muted: "#6E676B"
  mauve-faint: "#8F888C"
  hairline: "#E6E1E3"
  hairline-strong: "#CFC8CB"
  pearl: "#F7F5F6"
  white: "#FFFFFF"
  error: "#B42318"
  error-wash: "#FEF3F2"
  success: "#2F7A57"
typography:
  headline:
    fontFamily: "Newsreader, Iowan Old Style, Georgia, serif"
    fontSize: "clamp(26px, 6.4vw, 30px)"
    fontWeight: 400
    lineHeight: 1.15
    letterSpacing: "-0.01em"
  body:
    fontFamily: "Figtree, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: 1.5
  body-sub:
    fontFamily: "Figtree, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "15px"
    fontWeight: 400
    lineHeight: 1.5
  label:
    fontFamily: "Figtree, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "14px"
    fontWeight: 600
    lineHeight: 1.4
  caption:
    fontFamily: "Figtree, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "13px"
    fontWeight: 400
    lineHeight: 1.5
  input:
    fontFamily: "Figtree, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "17px"
    fontWeight: 400
  otp-digit:
    fontFamily: "Figtree, system-ui, -apple-system, Segoe UI, Roboto, sans-serif"
    fontSize: "24px"
    fontWeight: 500
    lineHeight: 1
    fontFeature: "tnum"
rounded:
  check: "6px"
  field: "14px"
  dialog: "22px"
  pill: "999px"
spacing:
  xs: "4px"
  sm: "8px"
  md: "12px"
  lg: "16px"
  xl: "20px"
  2xl: "28px"
  tap: "48px"
components:
  button-primary:
    backgroundColor: "{colors.rose-primary}"
    textColor: "{colors.white}"
    rounded: "{rounded.pill}"
    padding: "0 24px"
    height: "48px"
    typography: "{typography.label}"
  button-primary-hover:
    backgroundColor: "{colors.rose-pressed}"
    textColor: "{colors.white}"
  button-primary-disabled:
    backgroundColor: "{colors.hairline}"
    textColor: "{colors.mauve-muted}"
  button-ghost:
    backgroundColor: "{colors.white}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.pill}"
    padding: "0 24px"
    height: "48px"
  button-ghost-hover:
    textColor: "{colors.rose-ink}"
  button-text:
    textColor: "{colors.rose-ink}"
    padding: "0 8px"
    height: "44px"
  input-field:
    backgroundColor: "{colors.white}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.field}"
    padding: "0 16px"
    height: "52px"
    typography: "{typography.input}"
  otp-slot:
    backgroundColor: "{colors.white}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.field}"
    height: "58px"
    typography: "{typography.otp-digit}"
  answer-chip:
    backgroundColor: "{colors.pearl}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.pill}"
    padding: "4px 8px 4px 12px"
    height: "36px"
  channel-pill:
    backgroundColor: "{colors.white}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.pill}"
    padding: "0 14px 0 10px"
    height: "44px"
  channel-pill-selected:
    backgroundColor: "{colors.blush-50}"
    textColor: "{colors.rose-ink}"
  choice-card:
    backgroundColor: "{colors.white}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.field}"
    padding: "16px"
  choice-card-selected:
    backgroundColor: "{colors.blush-50}"
  alert-error:
    backgroundColor: "{colors.error-wash}"
    textColor: "{colors.error}"
    rounded: "{rounded.field}"
    padding: "12px 14px"
  alert-info:
    backgroundColor: "{colors.blush-50}"
    textColor: "{colors.mauve-text}"
    rounded: "{rounded.field}"
    padding: "12px 14px"
  dialog:
    backgroundColor: "{colors.white}"
    rounded: "{rounded.dialog}"
    width: "480px"
---

# Design System: Mia by Tanishq · Sign In / Sign Up

## Overview

**Creative North Star: "The Quiet Concierge"**

The system behaves like a good jewellery-counter assistant: it asks one thing at a time, in a warm serif voice, remembers what you already said, and never raises its voice. Every screen is a single question set in Newsreader, answered in plain Figtree fields, and closed by one pill-shaped rose action pinned to the foot of the dialog. Answers do not vanish; they collapse into small pearl chips above the next question, each with its own edit control, so the conversation stays visible and reversible.

The world is entirely light. Surfaces are white, structure is drawn with warm mauve-grey hairlines, and the only colour with a voice is Mia rose (#D14A61) and its blush washes. Depth comes from soft, warm-grey shadows and a light mauve scrim, never from dark panels. Density is generous but not airy: 52px fields, 48px actions, 28px dialog gutters on desktop, 20px on the phone sheet.

Motion is a single idea used in three places: the new step rises in, the phone sheet slides up, and the success tick draws itself. Everything else is a 120–150ms colour or border change. Reduced motion collapses all of it to instant.

**Key Characteristics:**
- One question per screen, serif prompt, sans everything else.
- Answered steps persist as editable pill chips (the "trail").
- Light-only palette: white, warm mauve-greys, one rose accent with blush tints.
- Pill actions, 14px fields, 22px dialog corners.
- Centered 480px dialog on desktop; bottom sheet under 600px; sticky footer CTA.
- One motion vocabulary (rise, slide, draw) on a shared ease-out curve.

## Colors

A light, warm-neutral palette carried by a single rose accent; there is no second hue and no dark surface anywhere.

### Primary
- **Mia Rose** (#D14A61): the brand colour. Fills the primary pill button, ticked checkboxes, the selected radio dot, focus outlines and focus-ring borders, the OTP caret, and the success tick. Used as a fill or a stroke, never as body-size text on white.
- **Rose Pressed** (#C4435A): hover state of the primary button only.
- **Rose Ink** (#B23A50): the text-safe rose. All links, text buttons ("Resend", "Stay on this page", "Edit"), the chip edit glyph, selected channel-pill text and legal links. Exists because Mia Rose on white sits at about 4.3:1.
- **Blush 50** (#FCF1F3): selected wash for channel pills and choice cards, info alert background, the success-mark disc, the preferences icon disc.
- **Blush 100** (#F7DDE3): the 3px focus halo around fields, the country select and the active OTP slot.
- **Blush 200** (#EFBFCA): hover border on an unselected choice card.

### Neutral
- **Mauve Text** (#4A4447): primary text, prompts, field values. The darkest value in the system; nothing goes deeper.
- **Mauve Muted** (#6E676B): secondary copy (sub-prompts, hints, chip labels, legal, timers), icon-button glyphs. Its RGB (110,103,107) is also the base of every shadow and the scrim.
- **Mauve Faint** (#8F888C): placeholders, disabled link text and field hover borders only. Not for readable copy.
- **Hairline** (#E6E1E3): chip borders, section dividers, the raised-footer rule, menu borders, disabled button fill.
- **Hairline Strong** (#CFC8CB): resting border for inputs, OTP slots, checkboxes, radios, pills, choice cards and ghost buttons.
- **Pearl** (#F7F5F6): answer-chip fill, icon-button hover, disabled OTP slots, menu-item hover.
- **White** (#FFFFFF): every surface: page, dialog, fields, cards.

### Status
- **Error** (#B42318) on **Error Wash** (#FEF3F2): invalid field borders, inline error messages, error alerts, focus halo on an invalid field.
- **Success** (#2F7A57): the answered-chip tick and the "saved" state line. Small marks only.

### Named Rules
**The No Dark Surfaces Rule.** No background, panel, scrim or overlay may be darker than Pearl. Overlays use rgba(110,103,107,.32), never black. Mauve Text (#4A4447) is the darkest value that may appear, and only as text.

**The Two Roses Rule.** Mia Rose fills and strokes; Rose Ink speaks. Any rose text at 16px or below, and every link, uses Rose Ink. Hover may brighten Rose Ink to Mia Rose.

**The One Accent Rule.** Rose and its blush tints are the only hue. Selection, focus and confirmation are all expressed in rose; do not introduce a second accent for any state except error red and the small success green.

## Typography

**Display Font:** Newsreader (with Iowan Old Style, Georgia, serif)
**Body Font:** Figtree (with system-ui, -apple-system, Segoe UI, Roboto, sans-serif)

**Character:** A soft editorial serif asks the question; a friendly humanist sans handles every answer, label and control. The serif appears once per screen and nowhere else in the flow, which is what makes it read as the concierge's voice.

### Hierarchy
- **Headline / Prompt** (Newsreader 400, clamp(26px, 6.4vw, 30px), 1.15, -0.01em, balanced wrap): the single question on each step and the success title. Exactly one per screen, and it receives focus on step change.
- **Body** (Figtree 400, 16px, 1.5): default text and button labels (buttons at 600).
- **Sub** (Figtree 400, 15px, Mauve Muted): the one line under the prompt; inline `strong` values switch to Mauve Text 600 and never wrap.
- **Input** (Figtree 400, 17px): field values; the phone number adds 0.04em tracking and tabular figures.
- **OTP Digit** (Figtree 500, 24px, tabular figures): one digit per slot.
- **Label** (Figtree 600, 14px): field labels, consent group title, choice-card titles (at body size), chip values. Optional markers are 13px 400 Mauve Muted.
- **Caption** (Figtree 400, 13–14px, Mauve Muted): hints, errors (14px), consent notes, legal (13px centred), save state.

### Named Rules
**The One Serif Rule.** Newsreader is reserved for the step prompt and the brand wordmark. Labels, buttons, chips, legal and every form element are Figtree.

**The Tabular Numbers Rule.** Phone numbers, OTP digits and countdown timers always set `font-variant-numeric: tabular-nums` so digits never jitter.

## Layout

The auth surface is a single-column dialog in three bands: a slim head (back, wordmark, close in 44px icon buttons), a scrolling body (trail of answered chips, then the current stage), and a sticky footer holding the primary action and, where relevant, the legal line.

- **Desktop / tablet (≥600px):** centered dialog, width min(480px, 100vw − 32px), max-height min(760px, 100dvh − 48px), 28px side gutters.
- **Phone (<600px):** full-width bottom sheet with only the top corners rounded, 20px gutters, footer padded by the safe-area inset. On short phones (≤640px tall) the sheet goes full height with square corners.
- **Footer:** a transparent top border that turns Hairline once the body scrolls under it.
- **Rhythm:** a 4px base stepping 4 / 8 / 12 / 16 / 20–22 / 28. Fields sit 16px apart; the sub-prompt leaves 22px before the first field; the trail leaves 18px before the prompt.
- **Grouping:** first/last name share a two-column row with a 12px gap that stacks below 380px. Channel pills wrap in an 8px flex row, indented 36px under their parent consent.
- **Targets:** primary and ghost buttons are 48px tall; every other interactive control is at least 44px.

## Elevation & Depth

Depth is ambient and warm: surfaces are flat white at rest, and only floating layers (dialog, menus) carry shadows, all tinted from Mauve Muted rather than black. Focus is shown by a flat 3px blush halo, not a shadow lift. Inline dividers are drawn with an inset 1px hairline shadow so they cost no layout.

### Shadow Vocabulary
- **Dialog float** (`box-shadow: 0 24px 64px rgba(110, 103, 107, .22)`): the auth dialog only.
- **Menu float** (`box-shadow: 0 12px 32px rgba(110, 103, 107, .16)`): the account dropdown and similar popovers.
- **Scrim** (`background: rgba(110, 103, 107, .32)`): behind the dialog; fades in over 200ms.
- **Focus halo** (`box-shadow: 0 0 0 3px #F7DDE3`, error: `0 0 0 3px #FEF3F2`): fields, select, active OTP slot.

### Named Rules
**The Warm Shadow Rule.** Every shadow and scrim is built from rgba(110,103,107,…). Black or cool-grey shadows are off-system.

**The Flat At Rest Rule.** Cards, fields, chips and pills never carry a drop shadow; selection is shown with a rose border and blush wash.

## Shapes

Soft, rounded, jewellery-box geometry. Four radii carry the whole system: fully round pills (999px) for every action, answer chip and channel toggle; 14px for fields, OTP slots, choice cards, alerts, menus and preference panels; 22px for the dialog (top corners only on the phone sheet); 6px for checkboxes (5px at the 18px pill size). Circles (50%) are reserved for icon buttons, radio buttons, the chip edit control and the icon discs. Borders are always 1px (1.5px on checkbox and radio frames); nothing uses a heavy stroke.

## Components

### Buttons
Calm, full-width and unmistakable: one rose pill per screen.
- **Shape:** fully rounded pill (999px), 48px tall, 24px horizontal padding, full width in the dialog.
- **Primary:** Mia Rose fill, white Figtree 600 16px label with 0.01em tracking. Hover moves to Rose Pressed; press scales to 0.99. Busy state swaps in an 18px ring spinner and blocks pointer events.
- **Disabled:** Hairline fill with Mauve Muted text.
- **Ghost:** white fill, Hairline Strong border, Mauve Text label; hover turns the border Mia Rose and the label Rose Ink. Used for low-stakes completion ("Done").
- **Text:** no fill, Rose Ink 600, 44px tall; hover brightens to Mia Rose and underlines. Inline link-buttons ("Resend", "Change") are underlined at rest with a 3px offset.
- **Icon button:** 44px circle, Mauve Muted glyph, Pearl wash on hover.
- **Focus:** 2px Mia Rose outline, 2px offset, on every control.

### Chips (the Trail)
The signature of the flow: each answered step becomes a chip above the next question.
- **Style:** Pearl fill, Hairline border, 999px radius, 36px tall, 14px text: a Mauve Muted label, a Mauve Text 600 value (ellipsised), a 16px Success tick.
- **Edit:** a 28px white circle holding a Rose Ink pencil, blush on hover; reopens that step.
- **Motion:** each new chip rises in (8px, 220ms).

### Channel Pills
- **Style:** white 44px pill, Hairline Strong border, 14px 500 label with an 18px embedded checkbox.
- **Selected:** Mia Rose border, Blush 50 wash, Rose Ink label, rose-filled checkbox with a white tick.

### Choice Cards
- **Corner Style:** 14px.
- **Background:** white; selected becomes Blush 50 with a Mia Rose border; hover borders Blush 200.
- **Border:** 1px Hairline Strong at rest.
- **Internal Padding:** 16px, with a 20px custom radio in a 22px column and a 14px gap. Title Figtree 600, description 14px Mauve Muted.

### Inputs / Fields
- **Style:** white, 1px Hairline Strong border, 14px radius, 52px tall, 16px padding, 17px text, Mauve Faint placeholder. Labels sit 6px above in Label style, with optional markers right-aligned.
- **Hover:** border deepens to Mauve Faint.
- **Focus:** border Mia Rose plus a 3px Blush 100 halo; no outline.
- **Error:** border Error red, halo Error Wash, a 14px error message with a 16px icon beneath. The user's input is kept.
- **Phone:** a 52px country select (same skin, custom chevron) beside the number field, 8px apart.
- **OTP:** six 58px slots on a 6-column grid (6–10px gap) over one hidden `one-time-code` input. The active slot takes the focus treatment and a blinking 2px rose caret; invalid turns all slots red; locked slots go Pearl with Mauve Faint digits. A tabular countdown and resend link sit 10px below.

### Checkboxes (Consent)
- **Style:** 22px square, 6px radius, 1.5px Hairline Strong frame, on a 24px + 1fr grid with a 12px gap and 14.5px/1.5 copy.
- **Checked:** Mia Rose fill and border with a white stroked tick. Unticked by default, always.
- **Group:** a consent block opens with an inset hairline rule and a 14px 600 title. For returning users it collapses into a 14px-radius **Preferences panel**: 36px blush icon disc, title, one-line summary, and a Rose Ink "Edit" toggle whose chevron rotates 180°. A 13px save-state line reports saved (Success) or failed (Error).

### Alerts
- **Error:** Error Wash fill, Error text, 14px radius, 12px/14px padding, 14px text, leading icon.
- **Info:** Blush 50 fill, Mauve Text copy, Rose Ink icon.

### Dialog
- **Style:** white, 22px radius, Dialog float shadow over the mauve scrim. Opens with a 260ms pop (fade + 2% lift + 0.985 scale) on desktop and a 300ms slide-up on the phone sheet.
- **Head:** back and close icon buttons flank a small wordmark (serif italic "mia" 24px in Mia Rose, "BY TANISHQ" 10px tracked caps in Mauve Muted).
- **Success state:** a 56px Blush 50 disc whose rose tick draws itself over 500ms, a serif prompt, a primary "Continue shopping" pill and a text-button escape.

### Navigation (host storefront)
- **Account button:** a 40px white pill with a Hairline Strong border and 14px 600 label; hover turns rose. Its dropdown is a white 14px-radius menu with the Menu float shadow and 8px-radius Pearl-hover rows.

## Do's and Don'ts

### Do:
- **Do** ask exactly one question per step, set in the Newsreader prompt, and move focus to it on every step change.
- **Do** collapse every answered step into an editable Pearl chip in the trail above the current question.
- **Do** keep a single Mia Rose (#D14A61) pill as the primary action, pinned in the sticky dialog footer.
- **Do** use Rose Ink (#B23A50) for every link and any rose text at or below 16px.
- **Do** build every shadow and scrim from rgba(110, 103, 107, …).
- **Do** show focus as a 2px Mia Rose outline on controls, or a Mia Rose border plus a 3px Blush 100 halo on fields.
- **Do** keep touch targets at 44px minimum and primary actions at 48px.
- **Do** limit motion to the step rise-in (260ms), sheet slide-up (300ms) and success tick draw (500ms) on cubic-bezier(.2, .8, .2, 1), and collapse all of it under `prefers-reduced-motion`.
- **Do** switch to a bottom sheet below 600px and respect the safe-area inset in the footer.

### Don't:
- **Don't** use any dark colour: no dark backgrounds, dark surfaces, black scrims or black shadows. Nothing darker than Mauve Text (#4A4447), and that only as text.
- **Don't** set body-size text in Mia Rose on white; it misses AA.
- **Don't** introduce a second accent hue for selection or emphasis.
- **Don't** use Newsreader for labels, buttons, chips or legal copy.
- **Don't** use square or small-radius buttons; actions are always 999px pills.
- **Don't** put drop shadows on fields, chips, pills or cards.
- **Don't** pre-tick any consent checkbox or make consent a condition of the primary action.
- **Don't** use Mauve Faint (#8F888C) for readable copy; it is for placeholders and disabled states only.
