# $Id: PKGBUILD 212051 2014-05-05 16:34:04Z jgc $
# Maintainer: Mark Ryabov <m.ryadom@gmail.com>

pkgname=gnome-settings-daemon-nopulse
_pkgname=gnome-settings-daemon
pkgver=3.14.1
pkgrel=1
pkgdesc="The GNOME Settings daemon without PulseAudio"
arch=('i686' 'x86_64')
license=('GPL')
depends=('dconf' 'gnome-desktop' 'gsettings-desktop-schemas' 'hicolor-icon-theme' 'libcanberra-pulse' 'libnotify'
         'libsystemd' 'libwacom' 'upower' 'libibus' 'librsvg' 'libgweather' 'geocode-glib' 'geoclue2'
         'nss')
makedepends=('intltool' 'xf86-input-wacom' 'libxslt' 'docbook-xsl')
conflicts=('gnome-settings-daemon')
replaces=('gnome-settings-daemon')
provides=('gnome-settings-daemon')
options=('!emptydirs')
install=gnome-settings-daemon.install
url="http://www.gnome.org"
groups=('gnome')
source=(http://ftp.gnome.org/pub/gnome/sources/${_pkgname}/${pkgver:0:4}/${_pkgname}-$pkgver.tar.xz)
sha256sums=('1bcca93d9dab5d5a98d0fdfcd1730d334b12158b06d352070537e418f2d98f96')

build() {
  cd ${_pkgname}-$pkgver

  ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var \
      --libexecdir=/usr/lib/${_pkgname} --disable-static --disable-pulse

  #https://bugzilla.gnome.org/show_bug.cgi?id=656231
  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool

  make
}

package() {
  cd ${_pkgname}-$pkgver
  make DESTDIR="$pkgdir" install
}
