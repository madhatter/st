# Maintainer: Arvid Warnecke <arvid.warnecke@gmail.com>

pkgname=st-custom
pkgver=0.9.3
pkgrel=3
pkgdesc="A custom build of the simple terminal"
arch=('x86_64')
url="https://st.suckless.org"
license=('MIT')
depends=('libxft' 'harfbuzz')
provides=('st')
conflicts=('st')

_patches=(01-st-alpha-20240814-a0274bc.diff
          02-st-scrollback-0.9.2.diff
          02b-st-scrollback-fix-ttywrite.diff
          03-st-ligatures-scrollback-20251007-0.9.3.diff
          04-st-scrollback-mouse-0.9.2.diff
          05-st-externalpipe-0.8.5-modified.diff
          06-st-font2-0.8.5.diff
          07-st-boxdraw_v2-0.8.5-modified.diff
          08-st-xresources-20230320-45a15676.diff
          09-st-sync-0.9.3-modified.diff)

source=("https://dl.suckless.org/st/st-${pkgver}.tar.gz"
        "config.h"
        ${_patches[@]})
sha256sums=('9ed9feabcded713d4ded38c8cebf36a3b08f0042ef7934a0e2b2409da56e649b'
            '097e1c002c485d20850c70deed2a9dc72eb8a45590e34d1e0cd1b3593981551e'
            '562f6a4baedeb89c8b6dfb2c2f14a69f9327fa8b71a5093e70219e39794b8d42'
            '8db63bf83df06cba12cdb02e578cb49afc789c726b4c85f66e95b372562bac7a'
            '411b027ee0140a93781d4ecef93e86766f283e07995f8f5332f2d364a90696df'
            '13a37703d6ccd7c869a2c9a69316cea27678424c936265ae86c46681c3905128'
            '5e1e57e12821c022807b33b4a950f1724bc2efeebd44323c3941f0bd652e1a19'
            '952643c594be48174723b1905f5d80492897bdf4d7ac7001a0d525af4adf50e8'
            '2ea18a883a7f2ee925b8b04b8bef97e3c1be62d6d31367574467570768a7a4f1'
            '3525f9e66ede63eee8961eba8fe02cfc0d7e32c233309ae32aefc1a760484ee9'
            'fc44d585d48cf1dfb00fb30c4e2c4cf9198b77f55a91f68ef7be26a5c75704a8'
            '495f9030cf8eb5970b98fd796b331f11dcb4c72080e1951261aa667e95c9d9cf')

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
