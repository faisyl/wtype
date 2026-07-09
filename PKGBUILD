# Maintainer: Faisal <faisal@kaosx.us>

pkgname=wtype-git
_pkgname=wtype
pkgver=0.4
pkgrel=1
pkgdesc="xdotool type for wayland (git)"
arch=('x86_64')
url="https://github.com/faisyl/wtype"
license=('MIT')
depends=(
    'glibc'
    'wayland'
    'libxkbcommon'
)
makedepends=(
    'git'
    'meson'
    'ninja'
    'wayland'
)
provides=("${_pkgname}")
conflicts=("${_pkgname}")
source=("${_pkgname}::git+${url}.git")
sha256sums=('SKIP')

pkgver() {
    cd "${srcdir}/${_pkgname}"
    git describe --long --tags --always | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    cd "${srcdir}/${_pkgname}"
    meson setup . build \
        --prefix=/usr \
        --buildtype=release \
        --default-library=static
    ninja -C build
}

check() {
    cd "${srcdir}/${_pkgname}"
}

package() {
    cd "${srcdir}/${_pkgname}"
    DESTDIR="${pkgdir}" ninja -C build install

    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}