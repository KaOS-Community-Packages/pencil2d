pkgname=pencil2d
pkgver=0.6.6.0
pkgrel=1
_commit=3b3229e2d95e78aff9fac09cc4d9b0d94e1a7535
pkgdesc="Create traditional hand-drawn animation using both bitmap and vector graphics"
arch=('x86_64')
url="https://www.pencil2d.org/"
license=('GPL')
depends=('ffmpeg' 'qt5-svg' 'qt5-multimedia' 'qt5-tools')
source=("${pkgname}.zip::https://github.com/pencil2d/pencil/archive/${_commit}.zip")
md5sums=('8520dc2404556f9c6944df224728a98a')

prepare() {
    cd "${srcdir}/pencil-${_commit}"
    if [ ! -e /usr/bin/qmake ] && [ -e /usr/lib/qt5/bin/qmake ]; then
        export PATH=$PATH:/usr/lib/qt5/bin
    fi
    qmake CONFIG+=release CONFIG+=GIT CONFIG+=PENCIL2D_RELEASE
}

build() {
    cd "${srcdir}/pencil-${_commit}"
    make
}

package() {
    cd "${srcdir}/pencil-${_commit}"
    make INSTALL_ROOT="${pkgdir}/usr" install
}
