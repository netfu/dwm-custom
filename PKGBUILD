# Original PKGBUILD by :
# Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Dag Odenhall <dag.odenhall@gmail.com>
# Contributor: Grigorios Bouzakis <grbzks@gmail.com>
# Custom version by :
# Xavier <xavier@netfu.io>

pkgname=dwm-custom
_pkgname=dwm
pkgver=6.1
pkgrel=1
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2')
replaces=('dwm')
source=(http://dl.suckless.org/dwm/dwm-$pkgver.tar.gz
        dwm-statuscolors-6.1.diff
        dwm-bottomstack-6.1.diff
        dwm-uselessgap-6.1.diff
	      config.h)

sha1sums=('3f41d930d46b6705a76d860d12bf3feffc614581' 
         'fd0ce1c7a9fa7f6a45c9d261e925d721728db427' 
         '97f112598b20040689e2172df7a7a6effe837554' 
         'c1cffbd11e1b013e38df88340399dd0ded665e27' 
         'e967578dced105a96141a129c1bd0d4b5b8f55c7')

prepare() {
  cd "$srcdir"/$_pkgname-$pkgver
  for patch in $startdir/*.diff; do
    patch < $patch
  done
  cp "$srcdir"/config.h config.h
}

build() {
  cd "$srcdir"/$_pkgname-$pkgver
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd "$srcdir"/$_pkgname-$pkgver
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D LICENSE "$pkgdir"/usr/share/licenses/$_pkgname/LICENSE
  install -m644 -D README "$pkgdir"/usr/share/doc/$_pkgname/README
}
