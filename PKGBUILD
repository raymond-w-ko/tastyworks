# Maintainer:   M.Reynolds <blackboxnetworkproject@gmail.com>

pkgname=tastyworks
pkgver=1.0.15
pkgrel=1
pkgdesc="One of the fastest, most reliable, and most secure trading platforms in the world."
arch=('x86_64')
url="https://tastyworks.com/technology.html"
license=('Other')
depends=('java-runtime')
source=("https://download.tastyworks.com/desktop-1.x.x/$pkgver/$pkgname-$pkgver-$pkgrel.x86_64.rpm")
sha256sums=('13cca9c54fe95461a83022b1149dbb6008c20109e805279c2a674872330dad98')

package() {
    cd "$srcdir"
    find "$srcdir" -name "*.jar" -type f -exec chmod 755 {} \;
    find "$srcdir" -name "*.so" -type f -exec chmod 755 {} \;

    mkdir -p usr/bin
    pushd "usr/bin" && ln -sf /opt/$pkgname/bin/$pkgname && popd

    install -d      "$pkgdir/opt/$pkgname"
    cp      -r      "$srcdir/opt/$pkgname/"                                       "$pkgdir/opt/"
    cp      -r      "$srcdir/usr/"                                                "$pkgdir/"

    sed     -i      's|Name=tastyworks|Name=TastyWorks|'                          "$srcdir/opt/$pkgname/bin/$pkgname.desktop"
    sed     -i      's|Comment=tastyworks|Comment=Trading Platform|'              "$srcdir/opt/$pkgname/bin/$pkgname.desktop"
    sed     -i      's|Icon=/opt/tastyworks/bin/tastyworks.png|Icon=tastyworks|'  "$srcdir/opt/$pkgname/bin/$pkgname.desktop"
    sed     -i      's|Categories=tastyworks|Categories=Internet|'                "$srcdir/opt/$pkgname/bin/$pkgname.desktop"

    install -Dm 644 "$srcdir/opt/$pkgname/bin/$pkgname.desktop"                   "$pkgdir/usr/share/applications/$pkgname.desktop"
    install -Dm 644 "$srcdir/opt/$pkgname/bin/$pkgname.png"                       "$pkgdir/usr/share/pixmaps/$pkgname.png"
}
