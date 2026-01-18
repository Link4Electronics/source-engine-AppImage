pkgname=source-engine-git
pkgver=1.5.r219.g7c23000
pkgrel=1
pkgdesc="Modified source engine (2017) developed by valve and leaked in 2020."
arch=('x86_64' 'aarch64')
url="https://github.com/nillerusr/source-engine"
license=('custom')
depends=('sdl2-compat' 'freetype2' 'fontconfig' 'zlib' 'bzip2' 'libjpeg' 'libpng' 'curl' 'openal' 'opus')
makedepends=("git" "gcc" "python")
options=('!debug' 'strip')
source=("git+https://github.com/nillerusr/source-engine.git")
sha256sums=('SKIP')

pkgver() {
	cd source-engine
	git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd source-engine
    git submodule update --init --recursive
    cd ..
}

build() {
    cd "${srcdir}/source-engine"
    ./waf configure --64bits -T release
    ./waf build
}

package() {
    cd "${srcdir}/source-engine"
    DESTDIR="$pkgdir/" ./waf install
	#install -Dm644 "${srcdir}/source-engine.desktop" -t "${pkgdir}/usr/share/applications"
}
