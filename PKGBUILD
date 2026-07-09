# Maintainer: Faisal <faisal@kaosx.us>
# Contributor: Faisal <faisal@kaosx.us>
# Contributor: Daniel <daniel@foo.bar>

pkgname=wtype
pkgver=0.4
pkgrel=1
pkgdesc="xdotool type for wayland"
arch=('x86_64')
url="https://github.com/faisyl/wtype"
license=('MIT')
depends=(
    'glibc'
    'wayland'
    'libxkbcommon'
)
makedepends=(
    'meson'
    'ninja'
    'wayland'
)
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha256sums=('SKIP')

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    meson setup . build \
        --prefix=/usr \
        --buildtype=release \
        --default-library=static
    ninja -C build
}

check() {
    # No test suite upstream
    :
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    DESTDIR="${pkgdir}" ninja -C build install

    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}