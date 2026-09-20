# Local-DE-Coach · Public Releases

Public download point for **DLLS — Deutsch Local Language Shadowing**.

**DLLS** is a local-first English/German shadowing trainer: pick a sentence on
YouTube, shadow it, get an instant pronunciation score (forced alignment +
GOP on your own PC). Your microphone audio **never leaves the machine and is
never transcribed**. RAM-guarded so the PC never freezes.

## Arch Linux — install & use

```bash
# system deps (once)
sudo pacman -S --needed ffmpeg espeak-ng yt-dlp uv

# install (pacman-native — builds from the release zip below)
git clone https://github.com/Local-DE-Coach/public.git
cd public
makepkg -si

# run the whole app
dlls
```

`dlls` boots the local backend + a btop-style terminal monitor — and
**Ctrl+C closes the app AND stops the backend**. First run provisions the
python env automatically (1–3 min with `uv`).

Then press **`e`** inside the app to connect the browser extension
(→ `chrome://extensions` → Developer mode → *Load unpacked* → the stable
folder the app shows you). Open a YouTube video — the **S** button turns
green when captions are ready → click it → practice sentence by sentence.

**No root?** Prefer a user install? Download the release zip below and run
`./install.sh` — full instructions in the zip's `README-ARCH.md`.

| Release | Asset | For |
|---|---|---|
| [`v0.6.0-arch`](https://github.com/Local-DE-Coach/public/releases/tag/v0.6.0-arch) | `shadowing-engine-0.6.0-archlinux.zip` | Arch Linux — CPU-only, tabbed TUI, one-key browser setup |

Upstream source & full docs: <https://github.com/Local-DE-Coach/Shadowing_Engine>
