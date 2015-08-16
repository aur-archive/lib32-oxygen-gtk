# Maintainer: Hyacinthe Cartiaux <hyacinthe.cartiaux@free.fr>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: birdflesh <antkoul at gmail dot com>
# Contributor: Zephyr

_pkgbasename=oxygen-gtk
pkgname=lib32-${_pkgbasename}
pkgver=1.1.6
pkgrel=1
pkgdesc="Port of the default KDE widget theme (Oxygen) to GTK"
arch=('i686' 'x86_64')
url="http://kde-look.org/content/show.php/?content=136216"
license=('LGPL')
depends=('lib32-gtk2' "${_pkgbasename}" 'lib32-dbus-glib')
makedepends=('cmake' 'gcc-multilib')
source=(ftp://ftp.kde.org/pub/kde/stable/${_pkgbasename}/${pkgver}/src/${_pkgbasename}-${pkgver}.tar.bz2)
md5sums=('714cd895e276cfd20a43b406a78ae6af')

build() {
  cd ${srcdir}
  mkdir build
  cd build

  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cmake ../${_pkgbasename}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DINSTALL_PATH_GTK_ENGINES=/usr/lib32/gtk-2.0/2.10.0/engines
  make
}

package() {
  cd ${srcdir}/build
  make DESTDIR=${pkgdir} install

  #Clean up directories provided by x86_64 package
  rm -rf ${pkgdir}/usr/bin
  rm -rf ${pkgdir}/usr/share
}
