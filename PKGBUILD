# Maintainer: Your Name <youremail@domain.com>
pkgname=sdrreceiver-git
_pkgname=sdrreceiver
pkgver=latest.r0.g545837b
pkgrel=1
pkgdesc="An SDR Receiver purposely for JAERO"
arch=('i686' 'x86_64' 'armv7h' 'aarch64')
url="https://github.com/jeroenbeijer/SDRReceiver"
license=('MIT')
depends=(
    'python'
)
makedepends=('git' 'qt6-base' 'qt5-base')
provides=("${_pkgname}")
conflicts=("${_pkgname}")
source=("${_pkgname}::git+${url}.git")
sha256sums=('SKIP')

pkgver() {
  cd "${_pkgname}"
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd "${srcdir}/${_pkgname}"
  qmake CONFIG-="CI"
}

build() {
  cd "${srcdir}/${_pkgname}"
 
 make
}

package() {
  cd "${srcdir}/${_pkgname}"
  install -Dm755 SDRReceiver "${pkgdir}/usr/bin/SDRReceiver"
  install -Dm755 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
}
