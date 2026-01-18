# Maintainer: Johan Larsson <johan@jolars.co>
pkgname=tomat
pkgver=2.8.0
pkgrel=1
pkgdesc="A Pomodoro timer with daemon support for waybar and other status bars"
arch=('x86_64' 'aarch64')
url="https://github.com/jolars/tomat"
license=('MIT')
depends=('alsa-lib')
makedepends=('rust' 'cargo')
source=("$pkgname-$pkgver.tar.gz::$url/archive/v$pkgver.tar.gz")
sha256sums=('2a3fb507ccb06655aa6c0ceecf8c384055c17c0b887026ca33a3110647e344ce')

prepare() {
    cd "$pkgname-$pkgver"
    cargo fetch --locked --target "$(rustc -vV | sed -n 's/host: //p')"
}

build() {
    cd "$pkgname-$pkgver"
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cargo build --frozen --release --all-features
}

check() {
    cd "$pkgname-$pkgver"
    export RUSTUP_TOOLCHAIN=stable
    cargo test --frozen --all-features
}

package() {
    cd "$pkgname-$pkgver"
    install -Dm755 "target/release/$pkgname" "$pkgdir/usr/bin/$pkgname"
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
}
