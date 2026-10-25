# Custom Dartsnut PixelDart Games

Collection of custom games and local WebSocket/MCP installers for the **Dartsnut PixelDart** board (`172.16.102.254`).

---

## Games

### 1. Dousea Darts (`douseadarts/`)
Custom **Basement Arcade 2.0** edition of `x01` darts (`301`, `501`, `701`, `901`, `1101`, `1501`) designed to match the Basement Arcade dashboard:
- **Neon CRT Palette:** Deep arcade cabinet violet/obsidian backdrop with CRT scanlines, Neon Pink (`#ff2bd6`) for Player 1, Electric Cyan (`#00f0ff`) for Player 2, Marquee Gold (`#ffe600`) inner bull & chasing bulb borders, and Laser Green (`#39ff14`) outer bull.
- **Attract Mode (`STARTUP`):** Chasing marquee bulb frame, animated pixel Space Invaders, flickering `DOUSEA DARTS` title, active rules pill (`501 · SINGLE OUT / P1 VS P2`), and `BASEMENT ARCADE` badge on the `64×32` bottom display.
- **Retro Arcade Dart Impact Animations:** 8-bit target lock-on reticle, dual concentric neon shockwaves, 22 square pixel sparks with arcade gravity, pulsing sector highlight, and floating callout popups (`T-60!`, `D-40!`, `DBULL 50!`, `+20`) that arc into the scoreboard slot.
- **Turn-Switch CRT Laser Wipe:** 1.35-second horizontal CRT laser curtain transition between turns (`GET READY / PLAYER 1 (or 2)` + checkout alert when `<= 170`).
- **Full `x01` Options (`B` Menu):** Configurable game variant, Single/Double In, Single/Double Out, 25/50 or 50/50 Bull, BGM/SFX toggles, and CPU AI opponent (Levels 1–18).

#### Install / Restore on the Dartsnut Board
```bash
node douseadarts/deploy_douseadarts.js 172.16.102.254
```

What `deploy_douseadarts.js` does automatically:
1. Creates `/home/rpi/dartsnut_rpi/apps/douseadarts/` and uploads all game files, `conf.json`, and `.dartsnut_backend.json`.
2. Copies `Micro5.ttf` and `sound/*.mp3` from `01dartgame`.
3. Generates the `128×128` preview image in `~/.dartsnut/preview_cache/douseadarts.png`.
4. Builds and stamps `.venv` via the board's native `ensure_app_venv("douseadarts")`.
5. Applies a safeguard in `/home/rpi/dartsnut_rpi/runtime/remote_device_config.py` so Cloud Sync skips deleting local custom games (`download_url == ""`), and restarts `dartsnut_python.service` if `remote_device_config.py` was newly patched.
