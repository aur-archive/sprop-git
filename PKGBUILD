# Contributor: Army

_pkgname=sprop
pkgname=$_pkgname-git
pkgver=20121028.5
pkgrel=1
pkgdesc="a simple X property utility. Less is more."
arch=('i686' 'x86_64')
url="http://tools.suckless.org/sprop"
license=('MIT')
depends=('libx11')
makedepends=('git')
provides=("$_pkgname")
conflicts=("$_pkgname")
source=("$_pkgname::git+http://git.suckless.org/sprop")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  echo "$(git log -1 --format="%cd" --date=short | sed 's|-||g').$(git rev-list --count master)"
}

build() {
  cd "$srcdir/$_pkgname"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$srcdir/$_pkgname"
  make PREFIX="/usr" DESTDIR="$pkgdir/" install
  install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
