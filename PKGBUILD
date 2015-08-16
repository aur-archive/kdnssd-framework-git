# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kdnssd-framework-git
pkgver=r23.d7024e7
pkgrel=1
pkgdesc='KDNSSD Framework'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/frameworks/kdnssd-framework'
license=('LGPL')
depends=('qt5-base' 'avahi')
makedepends=('extra-cmake-modules' 'git')
groups=('kf5')
conflicts=(kdnssd-framework)
provides=(kdnssd-framework)
source=('git://anongit.kde.org/kdnssd-framework.git')
md5sums=('SKIP')

pkgver() {
  cd kdnssd-framework
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../kdnssd-framework \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DLIB_INSTALL_DIR=lib \
    -DBUILD_TESTING=OFF
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
