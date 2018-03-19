# Maintainer: Rafael Milani Barbosa <rafaelmilanib[at]gmail[dot]com>

pkgbase=phpstorm-eap-bin
pkgname=(phpstorm-eap-bin phpstorm-eap-bin-jre)
pkgver=1.0
pkgrel=1
pkgdesc="Lightning-smart PHP IDE. Early Access Program(developed and maintained in Brazil). Started parent version phpstorm-eap:181.3494.17 ."
arch=('x86_64' 'i686')
license=('Commercial')
url='https://www.jetbrains.com/phpstorm/'
makedepends=('rsync')
options=('!strip')
source=(https://download.jetbrains.com/webide/PhpStorm-${pkgver}.tar.gz
        jetbrains-phpstorm-eap.desktop)
sha256sums=('5eb124845ceb717a48ef61a4f1d6e73c34f95ddc2426e54665b40df437717699'
            '479e6ac16424df02ce1610da9eec8cc73a84cac7912e60661d4092954142933e')

package_phpstorm-eap() {
  optdepends=('phpstorm-eap-jre: JetBrains custom Java Runtime (Recommended)'
              'java-runtime>=8: JRE - Required if phpstorm-eap-jre is not installed'
              'gnome-keyring: save login/deployment credentials safely')

  install -d -m 755 "${pkgdir}/opt/"
  install -d -m 755 "${pkgdir}/usr/bin/"
  install -d -m 755 "${pkgdir}/usr/share/applications/"
  install -d -m 755 "${pkgdir}/usr/share/pixmaps/"

  rsync -rtl "${srcdir}/PhpStorm-${pkgver}/" "${pkgdir}/opt/${pkgbase}" --exclude=/jre64

  ln -s "/opt/${pkgbase}/bin/phpstorm.sh" "${pkgdir}/usr/bin/${pkgbase}"
  install -D -m 644 "${srcdir}/jetbrains-${pkgbase}.desktop" "${pkgdir}/usr/share/applications/"
  install -D -m 644 "${pkgdir}/opt/${pkgbase}/bin/phpstorm.png" "${pkgdir}/usr/share/pixmaps/${pkgbase}.png"
}

package_phpstorm-eap-jre() {
  install -d -m 755 "${pkgdir}/opt/${pkgbase}"
  rsync -rtl "${srcdir}/PhpStorm-${pkgver}/jre64" "${pkgdir}/opt/${pkgbase}"
}
