# Maintainer: Arvid Warnecke <arvid.warnecke@gmail.com>

pkgname=st-custom
pkgver=0.9.3
pkgrel=1
pkgdesc="A custom build of the simple terminal"
arch=('x86_64')
url="https://st.suckless.org"
license=('MIT')
depends=('libxft' 'harfbuzz')
provides=('st')
conflicts=('st')

_patches=(01-st-alpha-20240814-a0274bc.diff
          02-st-scrollback-0.9.2.diff
          03-st-ligatures-scrollback-20251007-0.9.3.diff
          04-st-scrollback-mouse-0.9.2.diff
          05-st-externalpipe-0.8.5-modified.diff
          06-st-font2-0.8.5.diff
          07-st-boxdraw_v2-0.8.5-modified.diff
          08-st-xresources-20230320-45a15676.diff)

source=("https://dl.suckless.org/st/st-${pkgver}.tar.gz"
        "config.h"
        ${_patches[@]})
sha256sums=('SKIP' 'SKIP'
            'SKIP' 'SKIP' 'SKIP' 'SKIP'
            'SKIP' 'SKIP' 'SKIP' 'SKIP')

prepare() {
    cd "st-${pkgver}"
    for p in "${_patches[@]}"; do
        echo "==> $p"
        patch -Np1 --ignore-whitespace -i "../$p" || return 1
    done
    cp ../config.h config.def.h
}

build() {
    cd "st-${pkgver}"
    make PREFIX=/usr X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd "st-${pkgver}"
    install -Dm755 st "$pkgdir/usr/bin/st"
    install -Dm644 st.1 "$pkgdir/usr/share/man/man1/st.1"
    sed -i "s/VERSION/${pkgver}/g" "$pkgdir/usr/share/man/man1/st.1"
install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
