
# Maintainer: Dennis Gosnell <cdep.illabout@gmail.com>
pkgname=wmacpi
pkgver=2.3
pkgrel=1
pkgdesc="Battery monitor dockapp for Window Maker that doesn't depend on HAL"
arch=('i686' 'x86_64')
url="http://himi.org/wmacpi/"
license=('GPL')
depends=(libdockapp)
source=("http://windowmaker.org/dockapps/?download=$pkgname-$pkgver.tar.gz")
sha1sums=('5e1ef7a96c88418fe84e48440d8a9bcbb665ed4c')


build() {
	cd "$srcdir/dockapps-d4871ec"

	# make sure we don't build the command line `acpi` tool
	sed -i 's/^BUILD_CLI = 1$/#BUILD_CLI = 1/' Makefile

	# libdockapp was relocated
	sed -i 's|^#include <dockapp.h>|#include <libdockapp/dockapp.h>|' wmacpi.c

	make
}

package() {
	cd "$srcdir/dockapps-d4871ec"

	make install PREFIX="$pkgdir/usr/"
}
