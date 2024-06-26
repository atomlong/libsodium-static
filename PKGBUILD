# Maintainer: Luis Aranguren <pizzaman@hotmail.com>
# Contributor: Felix Yan <felixonmars@archlinux.org>
# Contributor: namelessjon <jonathan.stott@gmail.com>
# Contributor: Alessio Sergi <asergi at archlinux dot us>

pkgname=libsodium-static
_pkgname=libsodium
pkgver=1.0.20
pkgrel=1
pkgdesc="P(ortable|ackageable) NaCl-based crypto library (static library)"
arch=('i686' 'x86_64')
url="https://github.com/jedisct1/libsodium"
license=('custom:ISC')
depends=()
optdepends=('libsodium: headers and pkg-config files')
source=(https://download.libsodium.org/libsodium/releases/$_pkgname-$pkgver.tar.gz)
sha512sums=('7ea165f3c1b1609790e30a16348b9dfdc5731302da00c07c65e125c8ab115c75419a5631876973600f8a4b560ca2c8267001770b68f2eb3eebc9ba095d312702')
options=('staticlibs')

build() {
  cd "$_pkgname-$pkgver"

  ./configure --prefix=/usr --disable-pie
  make
}

check() {
  cd "$_pkgname-$pkgver"
  make check
}

package() {
  cd "$_pkgname-$pkgver"
  make DESTDIR="$pkgdir" install

  rm -rf "$pkgdir/usr/include/"
  rm -f "$pkgdir/usr/lib/"*.so*
  rm -rf "$pkgdir/usr/lib/pkgconfig"

  # install license
  install -d -m 755 "$pkgdir/usr/share/licenses/$pkgname"
  install -m 644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
