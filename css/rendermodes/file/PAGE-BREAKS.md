# PDF Page Break Utility Classes

Add these classes directly to any HTML element to control page breaking in PDF output.
All classes are active only in `@media print` (PDF render mode).

---

## Force a page break

### `.page-break-before`
Starts a new page **before** the element.

```html
<section class="page-break-before">
  <!-- always begins on a fresh page -->
</section>
```

**Use for:** chapter starts, major document sections, cover pages for subsections.

---

### `.page-break-after`
Forces a new page **after** the element.

```html
<div class="hero page-break-after">
  <!-- everything after this starts on the next page -->
</div>
```

**Use for:** cover/hero pages, full-page maps or images that should stand alone.

---

## Prevent breaking

### `.page-break-avoid`
Keeps the element **whole** — never split across pages. If it doesn't fit on the current page it moves entirely to the next one.

```html
<div class="doc-card page-break-avoid">
  <!-- card always prints as one unit -->
</div>
```

**Use for:** cards, panels, short content blocks. ⚠️ Avoid on tall elements — they can leave large blank gaps.

---

### `.page-keep-with-next`
Prevents a page break **between this element and the one that follows it**.

```html
<h3 class="page-keep-with-next">Day 1 — Arrival</h3>
<p>Your journey begins...</p>
```

**Use for:** headings, labels, markers — anything that must stay attached to its content below.

---

### `.page-keep-with-previous`
Prevents a page break **between this element and the one that precedes it**.

```html
<p class="page-keep-with-previous">Continued from above...</p>
```

**Use for:** continuation elements, captions, footnotes that must stay with the element above.

---

### `.page-break-avoid-inside`
Avoids breaks **inside** the element but allows natural breaks before and after it. Unlike `no-break-inside`, it explicitly resets before/after to `auto`.

```html
<figure class="page-break-avoid-inside">
  <img src="map.png" />
  <figcaption>Route overview</figcaption>
</figure>
```

**Use for:** figures, image+caption pairs, small self-contained units where you want the content to be intact but don't want to affect surrounding flow.

---

## Reset / undo

### `.page-break-allow`
Resets all break rules to `auto`. Use this on a **child** element to opt it out of `no-break-inside` inherited from a parent.

```html
<div class="page-break-avoid">
  <p>This stays together...</p>
  <div class="page-break-allow">
    <!-- this child can break freely despite the parent rule -->
  </div>
</div>
```

**Use for:** long content nested inside a no-break container, timeline item bodies, expandable sections.

---

## Quick reference

| Class | Effect | Common use |
|---|---|---|
| `.page-break-before` | New page before | Section starts, chapters |
| `.page-break-after` | New page after | Hero/cover pages |
| `.page-break-avoid` | Never split element | Cards, panels, short blocks |
| `.page-keep-with-next` | Stick to next element | Headings, labels, markers |
| `.page-keep-with-previous` | Stick to previous element | Captions, continuations |
| `.page-break-avoid-inside` | No internal break, neutral before/after | Figures, image+caption |
| `.page-break-allow` | Reset all — allow free breaking | Long children inside no-break parents |
