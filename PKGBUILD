# Maintainer: Johan Larsson <johan@jolars.co>
pkgname=tomat-bin
pkgver=2.12.0
pkgrel=1
pkgdesc="A Pomodoro timer for status bars"
arch=('x86_64' 'aarch64')
url="https://github.com/jolars/tomat"
license=('MIT')
depends=('alsa-lib' 'gcc-libs')
provides=('tomat')
conflicts=('tomat')
options=(!strip !debug)
source_x86_64=("tomat-$pkgver-x86_64-unknown-linux-gnu.tar.gz::$url/releases/download/v$pkgver/tomat-x86_64-unknown-linux-gnu.tar.gz")
source_aarch64=("tomat-$pkgver-aarch64-unknown-linux-gnu.tar.gz::$url/releases/download/v$pkgver/tomat-aarch64-unknown-linux-gnu.tar.gz")
sha256sums_x86_64=('5be78df653ae315ad99505bdd82045a207632044258b9c3d62389591321a5048')
sha256sums_aarch64=('5a5de81a0cb47bff58adcc270746208799a21be1b6237b61f4152a8612145f7a')

package() {
    # Binary
    install -Dm755 tomat "$pkgdir/usr/bin/tomat"

    # Man pages
    install -Dm644 man/*.1 -t "$pkgdir/usr/share/man/man1/"

    # Shell completions
    install -Dm644 completions/tomat.bash "$pkgdir/usr/share/bash-completion/completions/tomat"
    install -Dm644 completions/tomat.fish "$pkgdir/usr/share/fish/vendor_completions.d/tomat.fish"
    install -Dm644 completions/_tomat "$pkgdir/usr/share/zsh/site-functions/_tomat"

    # Systemd user service
    install -Dm644 tomat.service "$pkgdir/usr/lib/systemd/user/tomat.service"

    # License
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
