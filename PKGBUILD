#Mantainer: Michael Sierks <msierks117@gmail.com>
pkgname=navicat-mysql
_pkgname=navicat
pkgver=11.1.6
pkgrel=2
pkgdesc="A powerful Database Administration and Development tool for MySQL."
url="http://www.navicat.com"
license=('custom')
arch=('any')
source=(http://download2.navicat.com/download/${_pkgname}111_mysql_en.tar.gz icon_navicat.png)
md5sums=('4cb4f4e836235de1e3c6b925adb4163b' 'c2d8b38b4374cbeeb89b8492c976fd51')
depends=()

if test "$CARCH" == x86_64; then
  depends+=('lib32-glibc')
  depends+=('lib32-freetype2')
  depends+=('lib32-gcc-libs')
  depends+=('lib32-zlib')
  depends+=('lib32-libsm')
  depends+=('lib32-libxext')
  depends+=('lib32-alsa-lib')
else
  depends+=('glibc')
  depends+=('freetype2')
  depends+=('gcc-libs')
  depends+=('zlib')
  depends+=('libsm')
  depends+=('libxext')
  depends+=('alsa-lib')
fi

package() {

(
cat <<EOF
[Desktop Entry]
Name=Navicat for MySQL
Comment=Database GUI
Exec=navicat-mysql
Icon=/opt/navicat-mysql/icon_navicat.png
Terminal=false
Type=Application
Encoding=UTF-8
Categories=Development
EOF
) > ${srcdir}/navicat-mysql.desktop

(
cat <<EOF
#!/bin/sh
/opt/navicat-mysql/start_navicat
EOF
) > ${srcdir}/navicat-mysql

  mkdir -p ${pkgdir}/opt/${pkgname}
  mkdir -p ${pkgdir}/usr/bin
  mkdir -p ${pkgdir}/usr/share/applications
  cp -R ${srcdir}/navicat111_mysql_en/* ${pkgdir}/opt/${pkgname}
  cp ${srcdir}/${pkgname} ${pkgdir}/usr/bin/
  chmod +x ${pkgdir}/usr/bin/${pkgname}
  cp ${srcdir}/navicat-mysql.desktop ${pkgdir}/usr/share/applications/
  cp ${srcdir}/icon_navicat.png ${pkgdir}/opt/navicat-mysql/icon_navicat.png
  chmod +r ${pkgdir}/opt/navicat-mysql/icon_navicat.png
}


