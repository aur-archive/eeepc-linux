# Maintainer: Kitty Luckshot <secacat@gmail.com>

pkgname=eeepc-linux
pkgver=0.39a1
pkgrel=10
pkgdesc="Eeepc-linux is a kernel module that allows control of the fan and fsb speeds."
arch=('i686' 'x86_64')
url="http://code.google.com/p/eeepc-linux/"
license=('GPL')
makedepends=('pkgconfig' 'linux-headers')
install=eeepc-linux.install
# Actually from http://eeepc-linux.googlecode.com/issues/attachment?aid=-7397919136469029828&name=asus_eee-$pkgver.tar.gz
# Doesn't really work, hence the sources are added to the package
source=('asus_eee-0.39a1.tar.gz'
        'asus_eee-0.39a1-spinlock-kernel-2.6.39.patch')
md5sums=('46de95a6d0b333e222fc3e3a02f0e17b'
         'c8555c3b0752124c3ab5775fce97616c')

build() {
  cd $srcdir/asus_eee-$pkgver

  msg "Patching..."
  for i in $startdir/*.patch; do
    patch -Np1 -i "$i" || return 1
  done

  make || return 1
  install -Dm644 $srcdir/asus_eee-$pkgver/asus_eee.ko $pkgdir/usr/lib/modules/$(uname -r)/kernel/acpi/asus_eee.ko || return 1
}
