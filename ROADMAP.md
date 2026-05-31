# Roadmap

## Next Technical Steps

1. Replace the proxy canvas 3D renderer with real Three.js when package installation is available.
2. Add a small backend service to scan `reference-library/` folders automatically.
3. Generate thumbnails for local reference images and attach tags.
4. Add real camera-view rendering with lens/FOV simulation.
5. Add keyframes for camera height, target height, lens, light intensity, and subject movement.

## Product Features

1. Reference image tagging: backlight, close-up, low angle, neon, silhouette, product glow.
2. Shot comparison mode: A/B lighting, handheld/stabilized, warm/cool versions.
3. Auto storyboard document export with embedded 2D/3D PNGs.
4. Genre-specific shot template packs.
5. Project save/load through PostgreSQL instead of only JSON.

## AI Features

1. Analyze reference images for composition, color palette, and likely light direction.
2. Expand script breakdown into shot sequences with rationale.
3. Suggest missing coverage: establishing, reaction, insert, transition, safety shot.
4. Translate shot plans into prompts for video/image generation tools.
