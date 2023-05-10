# Maintainer: jmcb <joelsgp@protonmail.com>
pkgname=xfer9860-git
pkgver=r10.b869779
pkgrel=1
pkgdesc=" A linux app for sending and recieving data from a casio calculator"
arch=('x86_64')
url="https://github.com/sanjay900/xfer9860"
license=('GPL2')
depends=('libusb')
makedepends=('scons')
checkdepends=()
optdepends=()
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname%-git}::git+https://github.com/sanjay900/xfer9860.git"
        "${pkgname%-git}-$pkgver.patch")
sha256sums=('SKIP'
            '199532c548b0e123b9db9d866c1d0bcdd3af5fbd9b2db498a454ec202a07faa6')

pkgver() {
  cd "$srcdir/${pkgname%-git}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd "$srcdir/${pkgname%-git}"
  patch -p1 -i "$srcdir/${pkgname%-git}-$pkgver.patch"
}

build() {
  cd "$srcdir/${pkgname%-git}"
  scons
}

package() {
  cd "$srcdir/${pkgname%-git}"
  install -D "${pkgname%-git}" "${pkgdir}/usr/bin/${pkgname%-git}"
}
