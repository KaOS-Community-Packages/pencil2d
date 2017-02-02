pkgname=pencil2d
pkgver=0.5.3.80
pkgrel=1
_commit=219fe8402ff004eea31a39f74bfaf3d7166f0cb9
pkgdesc="Animation software for both bitmap and vector graphics"
arch=('x86_64')
url="http://www.pencil2d.org/"
license=('GPL')
depends=('libming' 'ffmpeg' 'qt5-svg' 'qt5-multimedia' 'qt5-tools')
source=("${pkgname}.zip::https://github.com/pencil2d/pencil/archive/${_commit}.zip"
        'pencil2d.desktop')
md5sums=('e444e8501f66bf62b79cede47f89fd87'
         '98008076937080db82a939d8129ed2d0')

prepare() {
    cd "${srcdir}/pencil-${_commit}"
    if [ ! -e /usr/bin/qmake ] && [ -e /usr/lib/qt5/bin/qmake ]; then
        export PATH=$PATH:/usr/lib/qt5/bin
    fi
    qmake
}

build() {
    cd "${srcdir}/pencil-${_commit}"
    make
}

package() {
    cd "${srcdir}/pencil-${_commit}"
    make DESTDIR="${pkgdir}" install
    install -Dm755 "${srcdir}/pencil-${_commit}/app/Pencil2D" "${pkgdir}/usr/bin/pencil2d"
    install -Dm644 "${srcdir}/pencil-${_commit}/icons/pencil.png" "${pkgdir}/usr/share/icons/hicolor/32x32/apps/pencil2d.png"
    install -Dm644 "${srcdir}/pencil2d.desktop" "${pkgdir}/usr/share/applications/pencil2d.desktop"
}
