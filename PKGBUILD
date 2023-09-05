_pkgbasename=zls
pkgname=${_pkgbasename}-git
pkgrel=1
pkgver=r1933.f9a1f6f
pkgdesc="The @ziglang language server for all your Zig editor tooling needs, from autocomplete to goto-def!"
arch=('x86_64' 'aarch64' 'i686')
url="https://github.com/zigtools/zls"
license=('MIT')
makedepends=('curl' 'jq' 'minisign' 'git' 'zig')
depends=('zig')
provides=('zls')
conflicts=('zls')
sha256sums=('SKIP' 'SKIP')
source=(git+https://github.com/zigtools/${_pkgbasename}
	git+https://github.com/ziglibs/known-folders)

echo -e '\e[93m'
echo -e ' ▓▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▓ ▒▒▒▒▒▒▒▒▒▒▒▒▒       ▒▒▓▓▓▓▓▓▓▒▒▒▒▒▒▓▓▒'
echo -e '▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▓▒      ▒▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▒'
echo -e '▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▓▒      ▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒'
echo -e '▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▒▒▒  ▒▓▓▓▓▓▓▓▓▓▒▒▒▒▒▒▒ ▒▓▓▓▓▓▓▓▓▓▓▓▓▓▒▒▒▒▒▒'
echo -e '▒▓▓▒▒▓▓▓▓▓▓▓▓▓▓▓▒▒▓▓▒ ▒▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▓ ▒▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒'
echo -e ' ▒▒▓▓▓▓▓▓▓▓▓▓▓▓▒▒▓▓▓▒ ▒▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▓▒▓▒▒▒▒▒▓▓▓▓▓▓▓▓▓▓▓▓▒'
echo -e '▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓'
echo -e '▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▓▓▓▓▓▓▒▓▓▓▓▓▓▓▓▓▓▓▒'
echo -e '\e[90m'

prepare() {
	cd "${srcdir}/${_pkgbasename}"
	git submodule init
	git config submodule.known-folders.url "$srcdir"/known-folders
	git submodule update
}

pkgver() {
	cd "${srcdir}/${_pkgbasename}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "${srcdir}/${_pkgbasename}"
	zig build -Doptimize=ReleaseSafe
}

package() {
	cd "${srcdir}/${_pkgbasename}"

	install -D -m755 zig-out/bin/$_pkgbasename "${pkgdir}/usr/bin/$_pkgbasename"
	install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/$_pkgbasename/LICENSE"
}

function exit_cleanup {
	cd "${srcdir}"/..
	# Sanitization
	rm -rf "${srcdir}/${_pkgbasename}"
	rm -rf "$PWD/known-folders"
	rm -rf "$PWD/pkg"
	rm -rf "$PWD/zls"
	msg2 'exit cleanup done'
	remove_deps
}

trap exit_cleanup EXIT
