# Birthday OS — Nebula Romance Theme

A themed birthday simulator that mimics a retro operating system boot experience. Features a full boot sequence, installation wizard, desktop environment with popup alerts, cascading gallery windows, a glitch effect, and a grand finale greeting screen before auto-restarting.

## Files

| File | Description |
|------|-------------|
| `index.html` | Main application — single-page HTML with embedded Tailwind CSS and JavaScript |
| `config.json` | Externalized configuration (name, age, sequences, gallery, email) |
| `README.md` | This documentation |

## Config.json Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Birthday person's name (displayed in greeting, certificate) |
| `age` | number | Current age (displayed in version upgrade and certificate) |
| `installationSteps` | string[] | List of fake "packages" shown during the installation wizard progress bar |
| `bootSequence` | string[] | Terminal lines typed out during the boot screen |
| `gallery` | object[] | Array of gallery items — each has `id` (number), `type` ("text" \| "image" \| "video"), and `content` (string: message text or media URL) |
| `email` | object | EmailJS integration settings (for future use) |
| `email.publicKey` | string | EmailJS public key |
| `email.serviceId` | string | EmailJS service ID |
| `email.templateId` | string | EmailJS template ID |
| `email.toEmail` | string | Recipient email address |

## User Flow

1. **Boot** — Terminal-style text typed line by line (boot sequence messages)
2. **Installation** — Fake progress bar installing themed "packages"
3. **Desktop + Hug Alert** — Desktop loads with wallpaper, taskbar, and a popup asking to confirm unlimited hugs
4. **Gallery Cascade** — After confirming hugs, gallery windows appear scattered across the screen with images, videos, and text messages
5. **Glitch** — Once all gallery items are dismissed, a glitch/flash effect triggers
6. **Grand Finale** — Full-screen "Happy Birthday" greeting with name and age
7. **Auto-restart** — Page reloads after 10 seconds, looping the experience

## Features

- Fully responsive single-file HTML (Tailwind CSS via CDN)
- Glassmorphism UI with neon glow effects (pink/lilac/mint palette)
- Draggable installation window
- Confetti animation on hug confirmation
- Cascading gallery with click-to-focus and dismiss behavior
- Printable "Certified Legend" certificate popup
- System clock in taskbar
- Audio toggle (UI only)
- External config with inline fallback for offline/local use
- EmailJS fields ready for future notification integration

## Deployment

1. Edit `config.json` with the recipient's name, age, and personalized messages/media URLs.
2. Serve the folder with any static file server:
   ```bash
   # Python
   python -m http.server 8000

   # Node (npx)
   npx serve .

   # VS Code Live Server extension also works
   ```
3. Open `index.html` in a browser. The page fetches `config.json` at load time; if unavailable, it falls back to inline defaults.
4. (Optional) For EmailJS integration, fill in the `email` fields in `config.json` and add the EmailJS SDK + send logic to `index.html`.
