# Maintainer: Local-DE-Coach <https://github.com/Local-DE-Coach>
# DLLS — Deutsch Local Language Shadowing
# btop-style app: `dlls` boots the local scoring backend + terminal monitor;
# Ctrl+C stops everything. YouTube sidepanel extension bundled (extension/).
pkgname=shadowing-engine
pkgver=0.6.0
pkgrel=1
pkgdesc="DLLS — Deutsch Local Language Shadowing · one-command local shadowing trainer (forced alignment + GOP, learner audio never leaves the PC)"
arch=(any)
url="https://github.com/Local-DE-Coach/Shadowing_Engine"
license=(MIT)
depends=(python ffmpeg espeak-ng yt-dlp)
optdepends=(
  'uv: fast first-run python env provisioning (strongly recommended)'
  'chromium: browser with zero-click extension loading (--load-extension)'
  'google-chrome: use the /setup wizard path on branded builds'
)
install=
source=("$pkgname-$pkgver.zip::https://github.com/Local-DE-Coach/public/releases/download/v$pkgver-arch/$pkgname-$pkgver-archlinux.zip")
sha256sums=('81d16a20da8fe391ad099349f2d04ccc8fc83d67aafcf1d805826b1994de3cff')  # shadowing-engine-0.6.0-archlinux.zip

package() {
  cd "$srcdir/$pkgname-$pkgver"

  # app payload → /opt/shadowing-engine (read-only; runtime data lives in
  # ~/.local/share/dlls — the dlls launcher + tui.py resolve this themselves)
  install -d "$pkgdir/opt/$pkgname"
  cp -a app extension scripts bin pyproject.toml uv.lock .env.example README-ARCH.md \
    "$pkgdir/opt/$pkgname/"

  # permissions: root reads, everyone reads; bin/dlls + scripts executable
  find "$pkgdir/opt/$pkgname" -type d -exec chmod 755 {} +
  find "$pkgdir/opt/$pkgname" -type f -exec chmod 644 {} +
  chmod 755 "$pkgdir/opt/$pkgname/bin/dlls" "$pkgdir/opt/$pkgname/scripts/tui.py"

  # the single user command
  install -d "$pkgdir/usr/bin"
  ln -s "/opt/$pkgname/bin/dlls" "$pkgdir/usr/bin/dlls"

  # docs
  install -Dm644 README-ARCH.md "$pkgdir/usr/share/doc/$pkgname/README-ARCH.md"
}
