# Maintainer: Jeff Simpson <jeff@syncrodoka.net>

pkgname=wmctrl-git
pkgver=1.07
pkgrel=1
pkgdesc="A command line tool to interact with an EWMH/NetWM compatible X Window Manager."
arch=('i686' 'x86_64')
url="https://github.com/geekless/wmctrl"
license=('MIT')
depends=('pacman')
makedepends=('git')
conflicts=('wmctrl')
provides=('wmctrl')
# The git repo is detected by the 'git:' or 'git+' beginning. The branch
# '$pkgname' is then checked out upon cloning, expediating versioning:
source=("$pkgname"::'git://github.com/geekless/wmctrl.git')
# Because the sources are not static, skip Git checksum:
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  # Use the tag of the last commit
  git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/$pkgname"
  autoconf
  ./configure
  make
}

package() {
  cd "$srcdir/$pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install
}