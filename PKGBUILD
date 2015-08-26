# Maintainer: aksr <aksr at t-com dot me>
# Contributor: David Manouchehri <david@davidmanouchehri.com>

pkgname=abduco-git
_gitname=$(printf ${pkgname%%-git})
_gitbranch=master
_gitauthor=martanne
pkgver=v0.4.r9.g57e7acb
pkgrel=1
pkgdesc="A session management and attach/detach functionality (to use together with dvtm(1)."
url="https://github.com/$_gitauthor/$_gitname"
license=('BSD')
source=("git://github.com/$_gitauthor/$_gitname.git#branch=$_gitbranch")
validpgpkeys=('F0FE029614EA35BC9E4F9768A6ECFD0C40839755') # David Manouchehri
sha512sums=('SKIP')
arch=('any') # arch=('i686' 'x86_64')
depends=('')
optdepends=('dvtm: Dynamic virtual terminal manager.')
makedepends=('git')
conflicts=("$_gitname")
provides=("$_gitname")
install=message.install

pkgver() {
  cd "$srcdir/$_gitname"
  (
    set -o pipefail
    git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
      printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  )
}

build() {
  cd "$srcdir/$_gitname"
  make
}

package() {
  cd "$srcdir/$_gitname"
  make PREFIX="$pkgdir/usr" install
  install -Dm644 README.md  $pkgdir/usr/share/doc/$pkgname/README
  install -Dm644 LICENSE $pkgdir/usr/share/licenses/$pkgname/LICENSE
}

# vim:set sw=2 sts=2 et:
