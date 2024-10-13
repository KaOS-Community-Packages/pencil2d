pkgname=pencil2d
pkgver=0.7.0
pkgrel=1
pkgdesc="Create traditional hand-drawn animation using both bitmap and vector graphics"
arch=('x86_64')
url="https://www.pencil2d.org/"
license=('GPL2')
depends=('ffmpeg' 'qt5-svg' 'qt5-multimedia' 'qt5-tools')
source=("${pkgname}.zip::https://github.com/pencil2d/pencil/archive/refs/tags/v${pkgver}.zip")
sha256sums=('e0ed4a1b062d713d3556a9211fbdf0e20d8534ca4787dc49248052c97c1b416e')

prepare() {
    cd "${srcdir}/pencil-${pkgver}"
    qmake-qt5 CONFIG+=release CONFIG+=PENCIL2D_RELEASE VERSION=${pkgver}
}

build() {
    cd "${srcdir}/pencil-${pkgver}"
    make
}

package() {
    cd "${srcdir}/pencil-${pkgver}"
    make INSTALL_ROOT="${pkgdir}/usr" install
}
