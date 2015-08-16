# Maintainer: György Balló <ballogy@freestart.hu>
pkgname=gwibber-dev
_pkgname=gwibber
pkgver=3.3.1.1
pkgrel=1
pkgdesc="Microblogging client for GNOME, which supports Twitter, Identi.ca, StatusNet, Facebook, Flickr, Digg, FriendFeed and Qaiku (development release)"
arch=(i686 x86_64)
url="http://gwibber.com/"
license=(GPL)
depends=(libgee 'dee>=0.5.18-2' json-glib gtkspell3 dbus-python gnome-keyring python-gnomekeyring python-notify python-wnck python-egenix-mx-base python2-oauth python-imaging python-pycurl python-simplejson pywebkitgtk pyxdg xdg-utils)
makedepends=('vala>=0.14' 'intltool>=0.35.0' 'gobject-introspection>=0.10')
optdepends=('libindicate: Messages Indicator support')
provides=("gwibber=$pkgver")
conflicts=(gwibber)
options=(!libtool)
install=$_pkgname.install
source=(http://launchpad.net/$_pkgname/3.4/$pkgver/+download/$_pkgname-$pkgver.tar.gz)
md5sums=(484bf327257698a267ffc6684bed253b)

build() {
  cd "$srcdir/$_pkgname-$pkgver"
  find . -type f | xargs sed -i 's@^#!.*python$@#!/usr/bin/python2@'

  # Disable Unity
  sed -i '/Dbusmenu/ d' client/Makefile.in

  ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
              --disable-static --disable-schemas-compile --disable-unity
  make
}

package() {
  cd "$srcdir/$_pkgname-$pkgver"

  make DESTDIR="$pkgdir" install
}
