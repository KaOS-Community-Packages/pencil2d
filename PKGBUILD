pkgname=pencil2d
pkgver=0.6.5.0
pkgrel=1
_commit=50a0c7c318f38988af85d34e955a5a78d3953474
pkgdesc="Create traditional hand-drawn animation using both bitmap and vector graphics"
arch=('x86_64')
url="https://www.pencil2d.org/"
license=('GPL')
depends=('ffmpeg' 'qt5-svg' 'qt5-multimedia' 'qt5-tools')
source=("${pkgname}.zip::https://github.com/pencil2d/pencil/archive/${_commit}.zip")
md5sums=('6cadf1803114cdf04dbf53d8b459ee9e')

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
