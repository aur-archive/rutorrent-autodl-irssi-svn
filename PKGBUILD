# Maintainer: Guten Ye

pkgname="rutorrent-autodl-irssi-svn"
pkgver=686 
pkgrel=5
pkgdesc="autodl-irssi rutorrent plugin. see https://wiki.archlinux.org/index.php/Autodl-irssi for Installation."
arch=("i686" "x86_64")
url="http://sourceforge.net/projects/autodl-irssi"
license=("unknown")
depends=("rutorrent" "autodl-irssi-svn")

_svntrunk="https://autodl-irssi.svn.sourceforge.net/svnroot/autodl-irssi/trunk/rutorrent/autodl-irssi"
_svnmod="autodl-irssi-svn"

build() {
  cd "$srcdir"
  msg "Connecting to SVN server...."

  if [[ -d "$_svnmod/.svn" ]]; then
    (cd "$_svnmod" && svn up -r "$pkgver")
  else
    svn co "$_svntrunk" --config-dir ./ -r "$pkgver" "$_svnmod"
  fi

  msg "SVN checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_svnmod-build"
  cp -r "$srcdir/$_svnmod" "$srcdir/$_svnmod-build"
  cd "$srcdir/$_svnmod-build"

  #
  # Build 
  #
  mv _conf.php conf.php
}

package() {
  cd "$srcdir/$_svnmod-build"

  mkdir -p "$pkgdir/usr/share/webapps/rutorrent/plugins/autodl-irssi"
  cp -r * "$pkgdir/usr/share/webapps/rutorrent/plugins/autodl-irssi"
}

# vim:set ts=2 sw=2 et:
md5sums=()
