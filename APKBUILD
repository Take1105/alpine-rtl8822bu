# Contributor: Ben Allen <bensallen@me.com>
# Maintainer: Ben Allen <bensallen@me.com>

# when changing _ver we *must* bump _rel
_name=rtl8822bu
_ver=c28a0c388a0acb6c79df645c2903cc90432d0f0a
_rel=0

_flavor=${FLAVOR:-vanilla}
_kpkg=linux-$_flavor
_kver=4.19.14
_krel=0

_kpkgver="$_kver-r$_krel"
_kabi=$_kver-$_krel-$_flavor
_kabi_virt=$_kver-$_krel-virt

pkgname=$_name-$_flavor
pkgver=$_kver
pkgrel=$(($_krel + $_rel))

pkgname=$_name-$_flavor
pkgver=$_kver
pkgrel=$(($_krel + $_rel))
pkgdesc="RTL8822BU Wireless Driver for Linux"
url="https://github.com/MeissnerEffect/rtl8822bu"
arch="x86_64 aarch64"
license="GPLv2"
makedepends="linux-vanilla-dev=$_kpkgver sed coreutils"
source="$_name-$_ver.tar.gz::https://github.com/MeissnerEffect/rtl8822bu/archive/$_ver.tar.gz"
builddir="$srcdir"/$_name-$_ver

build() {
	cd "$builddir"
	make KVER=$_kabi
}

check() {
	cd "$builddir"
}

package() {
	cd "$builddir"
	mkdir -p $pkgdir/lib/modules/$_kabi/kernel/drivers/net/wireless/ 
	install -p -m 644 *.ko $pkgdir/lib/modules/$_kabi/kernel/drivers/net/wireless/ 
}
sha512sums="61bc4db02dc432b031fa75c91c5a3f978de39bde4a1276072c19f47fc84bedd8c9f354619310b00a18735743c963d42ede3a186fde66e42d7b19b8644606e162  rtl8822bu-c28a0c388a0acb6c79df645c2903cc90432d0f0a.tar.gz"
