# Maintainer: jason ryan <jasonwryan@gmail.com>
# Submaintainer : bartus <arch-user-repoᘓbartus.33mail.com>

pkgname=v86d
pkgver=0.1.10
pkgrel=9
pkgdesc="A x86 Emulation Daemon"
arch=('i686' 'x86_64')
url="https://github.com/mjanusz/v86d"
license=('GPL2')
depends=('glibc')
makedepends=('git')
options=('!makeflags')
source=("git://github.com/mjanusz/v86d.git#tag=$pkgname-$pkgver"
        )
md5sums=(SKIP
         )

prepare() {
  cd ${pkgname}
  # move binary form '/sbin' to '/usr/bin'
  sed 's|sbin|usr/bin|g' -i Makefile
}

build() {
  cd "$pkgname"
  ./configure --with-x86emu
  # we only need /usr/include/video/uvesafb.h
  make
}

package() {
  cd "$pkgname"
  make DESTDIR="$pkgdir" install
}
