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
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("git+$url")
noextract=()
md5sums=('SKIP') #autofill using updpkgsums

prepare() {
  cd $pkgname/doc
  gzip xbacklight-ctl.1
  cd ..
}

package() {
  cd $pkgname
  install -Dm755 xbacklight-ctl "${pkgdir}/usr/bin/xbacklight-ctl"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/$pkgname/LICENSE"
  cd doc
  install -Dm644 xbacklight-ctl.1.gz "${pkgdir}/usr/share/man/man1/xbacklight-ctl.1.gz"
  cd ..
}
