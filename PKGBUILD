# Maintainer : Krzysztof Wloch <wloszekk@gmail.com>
# Contributor: Alexander Baldeck <alexander@archlinux.org>
# Contributor: SpepS <dreamspepser at yahoo dot it>

_name=terminatorX
pkgname=terminatorx
pkgver=3.90
pkgrel=1
pkgdesc="A realtime audio synthesizer that lets you scratch on sampled audio data"
arch=('i686' 'x86_64')
url="http://terminatorx.org"
license=('GPL')
depends=('gtk2' 'jack' 'liblrdf' 'audiofile' 'mpg123'
         'libxxf86dga' 'sox' 'libmad' 'vorbis-tools' 'rarian' 'gnome-doc-utils')
install="$pkgname.install"
source=("http://terminatorx.org/dist/$_name-$pkgver.tar.bz2")
md5sums=('4457e0f9ec2d97c99fb8893f1382b727')

build() {
  cd "$srcdir/$_name-$pkgver"

  # zlib fix
  sed -i '/gzFile/s/\*//' src/tX_midiin.cc

  # DSO link fix
  LDFLAGS+=" -ldl" \
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_name-$pkgver"
  make DESTDIR="$pkgdir" install

  ## desktop file
  cd icons
	make DESTDIR="$pkgdir" install

 
  ## icons
  install -d "$pkgdir/usr/share/pixmaps"
  install -Dm644 *.png "$pkgdir/usr/share/pixmaps"

  ## mime ver3.84
#  install -Dm644 $_name.mime \
#    "$pkgdir/usr/share/mime/packages/$_name.mime"
#  install -Dm644 $_name.keys \
#    "$pkgdir/usr/share/mime-info/$_name.keys"
}

