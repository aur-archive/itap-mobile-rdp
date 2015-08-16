# Contributor: Michael Zoech <michi.zoech+arch at gmail>
pkgname=itap-mobile-rdp
pkgver=1.1.5
_pkgver2=1.1
_pkgdate=2012-05-02
_pkgbuild=20445
pkgrel=3
pkgdesc="iTap mobile RDP for Linux"
arch=('i686' 'x86_64')
url="http://itap-mobile.com/desktop/rdp/"
license=('unknown') #('custom:itap-mobile-rdp')
#depends=('')
#optdepends=('')
#makedepends=('')
#install='itap-mobile-rdp.install'
md5sums=('0'
         '1f94d93abdd25fc98759c9662b253a75'
         '92eb60709ad63cccba2fc5e4b6da7add')

if [[ $CARCH == i686 ]]; then
	_arch=i386
	md5sums[0]='ec8f1509e4d8747028292c1b45a44202'
else
	_arch=x64
	md5sums[0]='a39a25578cf7470023ec4fd0464ebdda'
fi

source=(http://cf3.itap-mobile.com/downloads/qmote/$_pkgdate-qmote_Linux_Ubuntu1004_$_arch-$pkgver.$_pkgbuild-$_pkgver2.tar.gz
        itap-mobile-rdp.png
		itap-mobile-rdp.desktop)

build() {
  SRC_DIR="$srcdir/$_pkgdate-qmote_Linux_Ubuntu1004_$_arch-$pkgver.$_pkgbuild-$_pkgver2"
  INSTALL_DIR="$pkgdir/opt/itap-mobile-rdp"

  install -d -m 755 "$pkgdir"/usr/{bin,share/applications,share/pixmaps} "$INSTALL_DIR"/libs || return 1

  install -D -m 0644 itap-mobile-rdp.desktop "$pkgdir/usr/share/applications/itap-mobile-rdp.desktop" || return 1
  install -D -m 0644 itap-mobile-rdp.png "$pkgdir/usr/share/pixmaps/itap-mobile-rdp.png" || return 1

  cd "$SRC_DIR" || return 1

  install -m 0755 qmote "$INSTALL_DIR"/qmote || return 1
  install -m 0644 libs/* -t "$INSTALL_DIR"/libs || return 1

  ln -sf /opt/itap-mobile-rdp/qmote "$pkgdir/usr/bin/itap-mobile-rdp" || return 1

  # TODO mime
  # /usr/share/mime/packages/

  # TODO license
  #install -D -m 644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE" || return 1
}

