```markdown
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
```

total_length_cm = (reference_cm / reference_pcs) × total_pcs

```

Then the totals are summed and converted:

```

total_meters = total_cm / 100
total_rolls = total_meters / 300 (300 m per roll)

```

**Example:**

| Input | Value |
|---|---|
| Reference pcs | 1 |
| Reference cm | 15.6 |
| Total pcs | 13,000 |

```

length per pc = 15.6 / 1 = 15.6 cm
total length = 15.6 × 13,000 = 202,800 cm
total meters = 202,800 / 100 = 2,028 m
total rolls = 2,028 / 300 = 6.760 rolls

````

---

## 🚀 Getting Started

1. **Download** the HTML file (e.g. `index.html`).
2. **Open** it in any modern browser — Chrome, Firefox, Safari, or Edge.
3. That's it. No installation, no server, no dependencies.

> Optional: Host it on GitHub Pages, Netlify, or Vercel for a shareable link.

---

## 🛠 Customization

### Edit sticker size data

Locate the `stickerInfo` array near the top of the `<script>` block:

```javascript
const stickerInfo = [
  { letter: "A", name: "Carton",  length: "15.6 cm",   cm: 15.6 },
  { letter: "B", name: "VIN",     length: "0.9375 cm", cm: 0.9375 },
  { letter: "C", name: "Hangtag", length: "1.47 cm",   cm: 1.47 },
  { letter: "D", name: "MRP",     length: "3.9667 cm", cm: 3.9667 }
];
````

- **`letter`** → badge letter shown in the info table and dropdown.
- **`name`** → sticker name.
- **`length`** → display text in the info table.
- **`cm`** → numeric value used in calculations and the dropdown.

Both the info table and the dropdown update automatically.

### Change ribbon roll length

```javascript
const METERS_PER_ROLL = 300;
```

### Change the default reference quantity

Find this line inside `createRow`:

```javascript
const refPcs = defaults.refPcs ?? 1;
```

Change `1` to any number you want as the default.

### Adjust the layout width

In the `.layout` rule:

```css
.layout {
  max-width: 1500px;
}
```

And the info card width:

```css
.info-card {
  flex: 0 0 340px;
  max-width: 340px;
}
```

---

## 📱 Responsive Breakpoints

| Breakpoint | Behavior                                            |
| ---------- | --------------------------------------------------- |
| `> 1050px` | Side‑by‑side cards (info left, calculator right)    |
| `≤ 1050px` | Stacked layout — info card on top, calculator below |
| `≤ 700px`  | Compact paddings, rows wrap, results center         |
| `≤ 480px`  | Smaller inputs, tighter spacing                     |

---

## 🧩 Project Structure

Everything lives in a **single HTML file**:

```
ribbon-estimator/
└── index.html      ← all HTML, CSS, and JS
└── README.md       ← this file
```

Inside `index.html`:

```
<head>  → all styles (<style> block)
<body>  → layout wrapper
          ├── info card (left)
          └── calculator card (right)
<script> → stickerInfo JSON, row builder, calculation logic
```

---

## 🧠 Key Functions

| Function              | Purpose                                                                    |
| --------------------- | -------------------------------------------------------------------------- |
| `renderInfoTable()`   | Renders the left sticker size table from `stickerInfo`.                    |
| `buildOptions()`      | Generates the `<option>` list for the cm dropdown.                         |
| `createRow(defaults)` | Creates a new calculator row with inputs, result badge, and delete button. |
| `getRowCm(row)`       | Reads the cm value from either the dropdown or the custom input.           |
| `updateAll()`         | Recalculates every row and updates the grand total.                        |
| `init()`              | Boots the app: renders the info table and adds the first row.              |

---

## ✅ Browser Support

| Browser         | Supported |
| --------------- | --------- |
| Chrome / Edge   | ✅        |
| Firefox         | ✅        |
| Safari          | ✅        |
| Mobile browsers | ✅        |

Uses `backdrop-filter`, `flexbox`, and `CSS custom properties` — all widely supported.

---

## 🧾 License

Free to use for personal or commercial projects. No attribution required.

---

## 💡 Ideas for Future Improvements

- Export results to **PDF** or **CSV**.
- Add a **1% waste toggle** (currently the user adds it manually to quantities).
- Save/load presets with `localStorage`.
- Support **multiple currencies** or ribbon suppliers.
- Dark mode toggle.

---

**Made with 🎀 + 🖨️ + ❤️**

```

### How to use it

1. Save the file as `README.md` next to your `index.html`.
2. If you push the project to GitHub, the README will render automatically on the repo page.
3. Edit the **Preview**, **Ideas for Future Improvements**, and **License** sections to match your actual project name and preferences.
```
