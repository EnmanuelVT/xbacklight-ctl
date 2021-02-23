# Maintainer: Emmanuel Villavizar Trinidad <evillavizartrinidad@gmail.com>
pkgname=xbacklight-ctl
pkgver=0.1.0
pkgrel=1
pkgdesc="Use xbacklight easily from the command line or with keybindings."
arch=('any')
url="https://github.com/EnmanuelVT/xbacklight-ctl.git"
license=('GPL')
groups=()
depends=('xorg-xbacklight'
         'libnotify')
makedepends=('git'
             'gzip')
optdepends=()
provides=(xbacklight-ctl)
source=("git+$url")
md5sums=('SKIP') #autofill using updpkgsums

pkgver() {
  cd "$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd $pkgname/doc
  gzip xbacklight-ctl.1
  cd ..
}

package() {
  cd $pkgname
  install -Dm755 xbacklight-ctl "${pkgdir}/usr/bin/xbacklight-ctl"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README.md "${pkgdir}/usr/share/doc/$pkgname/README.md"
  cd doc
  install -Dm644 xbacklight-ctl.1.gz "${pkgdir}/usr/share/man/man1/xbacklight-ctl.1.gz"
  cd ..
}
