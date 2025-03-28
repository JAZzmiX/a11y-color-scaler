# a11y-color-scaler 🎨♿️

A lightweight SCSS utility that automatically adjusts text color for better contrast against any background — while preserving your brand palette.

- ✅ WCAG 2.1 compliant
- ✅ SCSS-only (no JS)
- ✅ Design-system friendly
- ✅ Works with any color palette

---

## 🚀 Installation

You can use **a11y-color-scaler** in two ways:

### 📦 Option 1: Install via npm

```bash
npm install a11y-color-scaler
```

Then import it in your SCSS:

```scss
@use 'a11y-color-scaler' as *;
```

---

### 📁 Option 2: Manual copy

Copy `_contrast.scss` into your SCSS project and import it using:

```scss
@use 'path/to/_contrast.scss' as *;
```

---

## 🧪 Live Demo

Try it live: [CodePen Demo](https://stackblitz.com/edit/vitejs-vite-f8zqdlmw?file=src%2Fstyle.scss)

---

## 🔧 Usage

```scss
$text: #83b2b2;
$bg: #d4ffff;

.block {
	background-color: $bg;
	color: adjust-contrast-color($text, $bg);
}
```

The function will automatically adjust the text color to ensure it meets the WCAG contrast ratio threshold (4.5:1 by default) by gradually darkening or lightening it.

---

## 📐 Accessibility thresholds

This utility follows official WCAG 2.1 contrast guidelines:

| Text type       | Minimum contrast |
| --------------- | ---------------- |
| Regular text    | 4.5:1            |
| Large/bold text | 3:1              |

You can control the threshold via the optional third parameter:

```scss
// Default (4.5:1)
color: adjust-contrast-color($text, $bg);

// For large or bold text (3:1)
color: adjust-contrast-color($text, $bg, 3);
```

---

## 🛠 Function Signature

```scss
adjust-contrast-color(
  $text-color,
  $bg-color,
  $threshold: 4.5,
  $step: 3%,
  $max-steps: 10
)
```

### Parameters

| Name          | Type   | Default | Description                                |
| ------------- | ------ | ------- | ------------------------------------------ |
| `$text-color` | Color  | –       | Initial color you want to use              |
| `$bg-color`   | Color  | –       | Background color to check contrast against |
| `$threshold`  | Number | `4.5`   | Desired contrast ratio                     |
| `$step`       | %      | `3%`    | Adjustment step for each iteration         |
| `$max-steps`  | Number | `10`    | Max iterations to prevent infinite loops   |

---

## 📊 Based on WCAG 2.1

- Uses official luminance and contrast ratio formulas
- Respects color balance and keeps as close to original as possible
- Formula based on: [WCAG 2.1 contrast ratio definition](https://www.w3.org/TR/WCAG21/#contrast-minimum)
- Test your color combos: [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)

---

## 🆚 How is this different from other contrast tools?

While other tools like [a11y-color-contrast](https://www.npmjs.com/package/a11y-color-contrast) only **validate** whether a color pair meets accessibility standards (WCAG),  
**a11y-color-scaler** actively **adjusts** the text color to meet those standards — without breaking your design.

| Tool                  | Type       | Purpose                            |
| --------------------- | ---------- | ---------------------------------- |
| `a11y-color-contrast` | JS Library | Checks contrast between colors     |
| `a11y-color-scaler`   | SCSS Tool  | Dynamically adjusts color for WCAG |

This means you can focus on design, and let the utility do the contrast correction for you.

---

## 📄 License

MIT – free for personal and commercial use.

---

## 🙌 Author

Created by Serhii Ivcheko ([@JAZzmiX](https://github.com/JAZzmiX))

Inspired by real needs in design system development.
