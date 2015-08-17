# Maintainer: Anthony Vitacco <anthony@littlegno.me>
#
# Prev. Maintainer: George Kamenov <cybertorture@gmail.com>
#
# huge thanks to Dany Martineau <dany.luc.martineau [at] gmail.com>
# for his package template :)
#
# 36v2 changelog:
# added glib-schemas-compile in rhythmbox-ampache.install
# 
# 39v2 changelog:
# some cleanups ( still way too ugly )
#
# 40 changelog:
# Updated plugin to work with Rhythmbox 3.0
#
# 41 changelog:
# Corrected Peas plugin initialization according to https://wiki.gnome.org/RhythmboxPlugins/WritingGuide.
#
# 42 changelog:
# Implemented write_async for cache file.
#

pkgname=rhythmbox-ampache-svn
pkgver=42
pkgrel=1
pkgdesc="This is a plugin for Rhythmbox music player that allows it to stream directly from an instance of an Ampache music streaming server."
arch=('any')
url="http://code.google.com/p/rhythmbox-ampache/"
license=('GPL')
depends=('rhythmbox' 'python')
makedepends=('subversion')
provides=('rhythmbox-ampache')
install=rhythmbox-ampache.install
_svntrunk=http://rhythmbox-ampache.googlecode.com/svn/branches/for_rhythmbox-gtk+3/
_svnmod=for_rhythmbox-gtk+3

build() {
  cd $startdir/src
  msg "Connecting to SVN server...."
  svn co $_svntrunk -r $pkgver || return 1
  msg " checkout done."
}
package() {
  mkdir -p $pkgdir/usr/share/rhythmbox/plugins/ampache/
  mkdir -p $pkgdir/usr/share/glib-2.0/schemas/
  mkdir -p $pkgdir/usr/lib/rhythmbox/plugins/ampache/
  cd "$srcdir"
  cp -r $_svnmod/* $pkgdir/usr/lib/rhythmbox/plugins/ampache
  cp $pkgdir/usr/lib/rhythmbox/plugins/ampache/ampache-prefs.ui $pkgdir/usr/share/rhythmbox/plugins/ampache
  cp $pkgdir/usr/lib/rhythmbox/plugins/ampache/ampache.ico $pkgdir/usr/share/rhythmbox/plugins/ampache
  cp $pkgdir/usr/lib/rhythmbox/plugins/ampache/ampache.png $pkgdir/usr/share/rhythmbox/plugins/ampache
  cp $srcdir/$_svnmod/org.gnome.rhythmbox.plugins.ampache.gschema.xml $pkgdir/usr/share/glib-2.0/schemas/
}
