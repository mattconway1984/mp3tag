# Maintainer: Mario Finelli <mario at finel dot li>
# Contributor: Hubert Maraszek <marach5 at gmail dot com>
# Contributor: Matthew Conway <matthew dot denis dot conway at gmail dot com>

pkgname=mp3tag
pkgver=2.99
pkgrel=3
pkgdesc="The universal tag editor."
arch=('i686' 'x86_64')
url="https://www.mp3tag.de/en/"
license=('custom')
depends=('wine' 'samba' 'lib32-gnutls')
makedepends=('p7zip')
source=(mp3tag
        LICENSE
        mp3tag.desktop
        mp3tag.png
        "https://download.mp3tag.de/mp3tagv${pkgver/./}asetup.exe")
sha256sums=('662d6b27590e34aabda9ee06efa08ecb10e107d4d30322abcc15f1b86c6e4ef8'
            '18967b634e69d8ccb08383d42a49ced3c0b11c632649a15c3a6a55e3a27f62e9'
            'bc0c7b8a7a9f9ee92dfe2f1880ef5d91920473713b5d60e4afa361d69a446798'
            'a3e09f7cda34bc31b3b5b1d7cf2010c3b17847c141ef5a074472eb72f760f6bf'
            '2c717574fb10f236da8db9ed6d89ff46d0ebc735f3275cef61369e719fa00cd4')
options=('!strip')
prepare() {
  7z -y -o"$srcdir/$pkgname-$pkgver" x "$srcdir/${pkgname}v${pkgver/./}asetup.exe"
}
package() {
  cd "$pkgname-$pkgver"

  install -dm755 "$pkgdir/usr/share/$pkgname"
  cp -a * "$pkgdir/usr/share/$pkgname"
  rm -rf "$pkgdir/usr/share/mp3tag/\$PLUGINSDIR" "$pkgdir/usr/share/mp3tag/\$R0"
  find "$pkgdir/usr/share/$pkgname" -type d -exec chmod 755 "{}" \;
  find "$pkgdir/usr/share/$pkgname" -type f -exec chmod 644 "{}" \;

  install -D -m755 "$srcdir/mp3tag" "$pkgdir/usr/bin/mp3tag"
  install -D -m644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -D -m644 "$srcdir/mp3tag.png" "$pkgdir/usr/share/pixmaps/mp3tag.png"
  install -D -m644 "$srcdir/mp3tag.desktop" "$pkgdir/usr/share/applications/mp3tag.desktop"
}
