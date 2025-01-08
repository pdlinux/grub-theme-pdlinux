pkgname=('grub-theme-pdlinux')
pkgver=r1.0
pkgrel=1

pkgdesc='pdlinux grub theme'
arch=('any')
url=""
license=('GPL')
makedepends=('git')
source=("grub-theme::git+$url.git")
sha256sums=('SKIP')

pkgver() {
	cd "${srcdir}"/grub-theme || exit
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	depends=('grub')
	install=pdlinux-theme.install
	provides=('grub-theme-pdlinux-custom')
	cd grub-theme/pdlinux-live || exit
	sed -i -e 's,.*text = "Welcome to PdLinux".*,#text = "Welcome to PdLinux",' theme.txt #remove welcome message
	find . -type f -exec install -D -m644 {} "${pkgdir}"/usr/share/grub/themes/pdlinux/{} \;
}
