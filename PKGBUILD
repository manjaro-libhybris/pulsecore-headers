# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=pulsecore-headers
pkgver=14.2
pkgrel=1
pkgdesc="PulseAudio internal development library (headers and pkg-config)"
arch=('any')
url="https://freedesktop.org/software/pulseaudio"
license=('LGPL2')
source=(https://freedesktop.org/software/pulseaudio/releases/pulseaudio-$pkgver.tar.xz
        pulsecore.pc.in
        0001-core-util-add-socket-h.patch)
md5sums=('SKIP'
         'bf41427d5401c9c0a052c17881ed68fc'
         '3f950e940eedf270da046a1f98e7e291')

build() {
    sed -i "s/@PA_MAJORMINOR@/${pkgver}/" pulsecore.pc.in

    cd pulseaudio-${pkgver}
    patch -p1 -N < ../0001-core-util-add-socket-h.patch
}

package() {
    install -Dm644 "${srcdir}/pulsecore.pc.in" "${pkgdir}/usr/lib/pkgconfig/pulsecore.pc"

    mkdir -p "${pkgdir}/usr/include/pulsecore"
    mkdir -p "${pkgdir}/usr/include/pulsecore/filter"
    cp -r pulseaudio-${pkgver}/src/pulsecore/*.h "${pkgdir}/usr/include/pulsecore/"
    cp -r pulseaudio-${pkgver}/src/pulsecore/filter/*.h "${pkgdir}/usr/include/pulsecore/filter/"
}
