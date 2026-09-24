# 🎀 Ribbon Estimator

A modern, single‑file web tool for calculating how much **ribbon** (in meters and rolls) is required to print sticker rolls — based on sticker size and total quantity.

Built with vanilla HTML, CSS, and JavaScript. No build step, no dependencies. Just open and use.

---

## 📸 Preview

- **Left card** — Sticker size reference table (populated from a JSON array).
- **Right card** — Dynamic ribbon calculator with add/remove rows and live totals.
- **Result** — Total ribbon length in meters and rolls (with 3‑decimal precision).

---

## ✨ Features

### Ribbon Calculator

- **Dynamic rows** — Add as many sticker types as you need with the `+ Add another sticker` button.
- **Dropdown sticker picker** — Choose a predefined sticker from the JSON list, or pick `✏️ Custom…` to enter your own length manually.
- **Auto reset on selection** — Selecting a predefined sticker sets the reference quantity (`pcs`) to `1` automatically.
- **Live totals** — Every input triggers an instant recalculation. No submit button needed.
- **Precise roll output** — Rolls are shown with **3 decimal places** (e.g. `5.667 rolls`) instead of rounding up.
- **Delete rows** — Remove any row (except the last remaining one) with the `✕` button.

### Sticker Size Info Card

- Compact side panel that shows sticker letters, names, and lengths.
- **Populated from a JSON array** so you can add or edit sticker types in one place.

### UI / UX

- **Glassmorphism design** — Soft blur, rounded corners, and layered shadows.
- **Responsive layout** — Side‑by‑side cards on desktop, stacked vertically on tablet and mobile.
- **Print/ink icon** — Custom inline SVG printer icon as the app logo.
- **No row wrapping** — The calculator rows stay on a single line on desktop for a clean look.

---

## 🧮 How the Calculation Works

Each row uses a simple ratio:
