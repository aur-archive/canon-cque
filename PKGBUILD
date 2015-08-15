# Maintainer: sorin.davidoi <sorin.davidoi *at* gmail *dot* com>
# Contributor: danilo <gezuru *at* gmail *dot* com>
pkgname=canon-cque
pkgver=2.0.7
_pkgver='2.0-7'
pkgrel=2
pkgdesc='Canon CQue printing driver (PPDs and sicgsfilter only!)'
arch=(i686 x86_64)
url='http://software.canon-europe.com/products/0010871.asp'
license=('custom')
depends=('cups' 'foomatic-filters')
optdepends=('samba: printing via windows/smb shares')
source=('http://files.canon-europe.com/files/soft45523/software/g148ren_lintgz_32_64_0207.tar.zip'
        'LICENSE')
sha256sums=('2e0fb4346cace3ee034551bc5139b2f0b621bd3b958e47b8d488d63ee34d6582'
            '343a624f559718d085b01605572fdf1cf33201931f06ef37567bbd497a29d333')

if [ "$CARCH" = "x86_64" ]; then
    depends+=('lib32-glibc')
fi

build() {
    cd $srcdir
    if [ $arch != 'i686' ]; then
        tar xfz cque-en-$_pkgver.$arch.tar.gz
    else
        tar xfz cque-en-$_pkgver.tar.gz
    fi
}

package() {
    mkdir -p $pkgdir/usr/share/ppd/canon/ $pkgdir/usr/bin
    cp $srcdir/cque-en-$_pkgver/ppd/* $pkgdir/usr/share/ppd/canon/
    cp $srcdir/cque-en-$_pkgver/sicgsfilter $pkgdir/usr/bin/
    install -D -m644 $startdir/LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
