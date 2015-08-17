#contributor: Francesco 'Kiko' Corsentino <kikocorsentino[at]gmail[dot]com>
#updated by Fred Warren <fred.warren[at]gmail[dot]com> 20Mar2012

pkgname=pywmdockapps
pkgver=1.21
pkgrel=2
pkgdesc="A library that makes it possible to write WindowMaker dockapps in Python."
url="http://pywmdockapps.sourceforge.net"
license=('GPL')
arch=('i686' 'x86_64')
depends=('libxpm' 'python2')
makedepends=('libxpm')
optdepends=('mplayer: pywmradio.py support')
source=(http://sourceforge.net/projects/pywmdockapps/files/$pkgname/$pkgver/$pkgname-$pkgver.tar.gz/download
        http://people.csail.mit.edu/jaffer/Color/rgb.txt
        pywmdockapps.patch)
md5sums=('ba2c6a16e3fdd5798f3b9d2334d73b8e'
         'd5887af1d065a008a8988150dbf9e5f9'
         '22d4ab20f90467030a55e914cff17a85')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  patch -Np1 -i ../pywmdockapps.patch
  python2 setup.py install \
      --prefix=${pkgdir}/usr \
      --install-scripts=${pkgdir}/usr/share/pywmdockapps/examples
  install -d "${pkgdir}/usr/share/$pkgname/samples" || return 1
  install -Dm644 "$srcdir/rgb.txt" "$pkgdir/usr/share/$pkgname/rgb.txt"
  cd ${srcdir}/${pkgname}-${pkgver}/examples
  install -m444 sample.pyradiorc sample.pywmgenericrc sample.pywmhdmonrc sample.pywmsetirc \
      "${pkgdir}/usr/share/${pkgname}/samples"
}

