pkgname=firefox-spell-es-es
_file=222208
pkgver=1.7
pkgrel=1
pkgdesc="Spanish (Spain) spellchecking dictionary for Firefox."
arch=('any')
url="https://addons.mozilla.org/addon/3554/"
license=('MPL')
depends=('firefox')
makedepends=('unzip')
source=($pkgname-$pkgver.xpi::https://addons.mozilla.org/firefox/downloads/file/$_file/diccionario_de_espanolespana-$pkgver.xpi)
noextract=($pkgname-$pkgver.xpi)
sha1sums=('0375558ba7965561022300c2060b5b478fa36556')

build() {
  cd "$srcdir"
  [[ -d $pkgname-extract ]] || \
    mkdir $pkgname-extract
  unzip -q -d $pkgname-extract \
    $pkgname-$pkgver.xpi
}

package() {
  cd "$srcdir/$pkgname-extract"
  local emid=$(sed -n '/.*<em:id>\(.*\)<\/em:id>.*/{s//\1/p;q}' install.rdf)
  local dstdir="$pkgdir/usr/lib/firefox/browser/extensions/$emid"
  install -d "$dstdir"
  cp -R * "$dstdir"
  find "$pkgdir" -type d -exec chmod 0755 {} \;
  find "$pkgdir" -type f -exec chmod 0644 {} \;
}

# vim:set ts=2 sw=2 et:
