# Planet Jumping

A single-page, cinematic "planet hopping" experience. Click the portal to fly from Mars to Earth to Venus, with video transitions, a 3D-tilting portal mask, and animated planet facts.

Pure HTML/CSS/JS in one file ([index.html](index.html)). No build step, no dependencies.

## Run

Open `index.html` in a modern browser, or serve the folder:

```bash
npx serve .
# or
python -m http.server 8000
```

An internet connection is required: the videos and images are streamed from a CDN.

## How it works

- **Preloader**: a Mars video plays with a 0–100% counter while the logo flies to the top-left corner.
- **Portal**: a `<canvas>` clips the next planet's video into a rounded-rect mask that tilts in 3D toward the cursor.
- **Travel**: clicking the portal expands the mask to full screen, plays the transition video, then swaps to the next planet and reveals its title and facts.
- **Custom cursor**: dot and orbit that follow the pointer, with an "Enter" label over the portal.

## Planets

| Planet | Next | Notes |
|--------|------|-------|
| Mars   | Earth   | Starting planet |
| Earth  | Venus   | |
| Venus  | Mercury | End of the route (travel disabled) |

The sidebar lists all eight planets, but only Mars, Earth and Venus have content.

## Customize

Edit the `states` object in the `<script>` section of `index.html` to change facts, names, or media URLs. Media URLs are the constants at the top of the script (`MARS_BG`, `TO_EARTH`, etc.).

## Notes

- Responsive down to mobile (the sidebar and nav are hidden on small screens).
- Honors `prefers-reduced-motion` for CSS transitions.
- Uses the SF Pro and Aalto fonts if installed locally, otherwise falls back to Arial.
- The system cursor is hidden (`cursor: none`) in favor of the custom one.
