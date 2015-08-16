# Maintainer: Alexander Rødseth <rodseth@gmail.com>
# Contributor: Arkham <arkham at archlinux dot us>
# Contributor: hybraries <macwolf@archlinux.de>
# Contributor: Stefan Husmann <stefan-husmann@t-online.de>
# Contributor: Navi <navitwo.at.gmail.dot.com>
# Contributor: rabyte <rabyte.at.gmail.dot.com>
# Contributor: Johannes Krampf <wuischke.at.amule.dot.org>

pkgname=midori-git
pkgver=0.5.2.1.g220032c
pkgrel=1
epoch=2
pkgdesc='Lightweight web browser based on WebKit and GTK3. Git development version.'
arch=('x86_64' 'i686')
url='http://twotoasts.de/index.php?/pages/midori_summary.html'
license=('LGPL')
depends=('libzeitgeist' 'webkitgtk3' 'libnotify' 'libxss' 'hicolor-icon-theme' 'desktop-file-utils' 'libunique3' 'gcr') # 'granite'
makedepends=('pkg-config' 'git' 'python2' 'libxml2' 'gtk3' 'intltool' 'python2-docutils' 'libsoup' 'vala' 'librsvg')
optdepends=('aria2: download utility'
            'steadyflow: download manager')
provides=('midori')
conflicts=('midori' 'midori-gtk2-git')
options=('!emptydirs')
install='midori.install'
source=("midori::git://git.xfce.org/apps/midori")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/midori"

  git describe --always | sed 's|-|.|g'
}

prepare() {
  cd "$srcdir/midori"

  # python 2 fix
  sed -i '0,/on/s//on2/' waf wscript
}

build() {
  cd "$srcdir/midori"

  ./waf configure --prefix=/usr --enable-gtk3 --disable-granite --enable-webkit2
  ./waf build 
}

package() {
  cd "$srcdir/midori"

  DESTDIR="$pkgdir" ./waf install
}

# vim:set ts=2 sw=2 et:
