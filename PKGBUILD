# Maintainer:
# Contributor: Jaroslav Lichtblau <dragonlord@aur.archlinux.org>

pkgname=wrogue
pkgver=0.8.0b
pkgrel=1
pkgdesc="Warp Rogue is a gothic science fantasy roguelike game"
arch=('i686' 'x86_64')
url="http://todoom.sourceforge.net/"
license=('GPL')
depends=('sdl')
makedepends=('patch')
source=(http://gentoo.cs.utah.edu/distfiles/wrogue-0.8.0b.zip
#http://downloads.sourceforge.net/todoom/$pkgname-$pkgver.zip
        $pkgname-$pkgver-data-files.diff)
sha256sums=('adc79ec9a97b6b60a8b16b6fd548cf349606702e3df74f819537b01d6640483a'
            'e7b78c0e06ade6bd460f4ed849e92679f34bb11630fc1def63da7b17cead6e28')

build() {
  cd "${srcdir}"/$pkgname-$pkgver/src

#fix data paths
  patch -Np2 -i "${srcdir}"/$pkgname-$pkgver-data-files.diff

  make -f linux.mak release
}

package() {
  cd "${srcdir}"/$pkgname-$pkgver/src

  install -Dm755 "${srcdir}"/$pkgname-$pkgver/$pkgname "${pkgdir}"/usr/bin/$pkgname
  install -d "${pkgdir}"/usr/share/$pkgname
  cp -r "${srcdir}"/$pkgname-$pkgver/data/ "${pkgdir}"/usr/share/$pkgname/
}
