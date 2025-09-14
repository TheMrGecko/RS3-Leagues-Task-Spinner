# DoubleShines Task Tracker (RS3 Spinner)

A single-page web app to spin and pick a RuneScape 3 task from a curated list, track the current task, and visualize completion progress.

Hosted as a static site. A tiny Tailwind build step generates `assets/tailwind.css` for production (no CDN at runtime).

## Features

- Spinner with easing animation and subtle audio ticks/flourish
- Manage tasks (add, remove, search, shuffle, sort)
- Persist tasks and current task in localStorage (per browser)
- Completion viewer grid with filter/sort
- Confetti and chime on completion

## Quick start

- Open `index.html` in a modern browser (Chrome/Edge/Firefox/Safari).
- The app stores data locally in your browser via localStorage.

## Public hosting

- Build Tailwind once to produce `assets/tailwind.css`:

  ```powershell
  npm install
  npm run build:css
  ```

- Host the folder on any static host (GitHub Pages, Netlify, Vercel, S3, etc.).
- Ensure the image path is case-correct: `DSSIT.png` (navbar logo).
- No server-side components required.

## Modifying the app

This project is intentionally framework-free and easy to tweak:

- HTML structure and styles live in `index.html`.
- Tailwind CSS is loaded via CDN; custom styles are in the `<style>` block.
- Tailwind CSS is built locally via CLI; the compiled file is `assets/tailwind.css`. Source entry is `src/styles/tailwind.css`.
- All JavaScript is inline in `index.html` near the bottom of the file.

Common changes:

- Edit the default task list:
  - Search for `const defaultTasks = [` in `index.html` and modify the array.
  - Duplicates are supported intentionally; completion logic accounts for frequency.
- Change the spin duration default:
  - Search for `id="spinDuration"` and adjust the `value` attribute.
- Tweak colors/glow:
  - Edit the CSS `:root` variables, especially `--glow-color`.
- Disable/enable sounds:
  - Wrap calls to `startSpinSound()` and `createSuccessChime()` with your own flag, or comment them out.

## Behavior guarantees

The app uses only client-side storage. Clearing site data or using a private window will reset tasks.

## Code style & formatting

This repo includes Prettier for formatting. To format consistently:

- Install Prettier in your editor and enable "Format on Save".
- Use the included `.prettierrc` and `.prettierignore`.

Optional: If you add ESLint, prefer rules that do not change runtime behavior (stylistic only).

## Building CSS during development

To watch and rebuild Tailwind on changes:

```powershell
npm run dev:css
```

## Development tips

- Avoid changing the `ITEM_HEIGHT` constant or the matching CSS `--item-height` unless you update both together.
- The spinner uses a small set of "virtual" rows for performance; updating the data triggers a full repaint.

## Accessibility

- Buttons have descriptive text and clear focus/hover states.
- Modal windows can be closed by clicking the dimmed overlay (viewer) or the provided button.

## Usage & attribution

Friendly note about reusing this project:

- Personal use: absolutely okay. Clone it, tweak it, and host it for yourself or your friends.
- Credit: please keep the "Made by Gecko" footer or add a small credit/link back. It helps a lot.
- Commercial use: not permitted without written permission. If you have a cool idea, reach out first.

Thanks for being respectful and sharing the love!

Made by Gecko
