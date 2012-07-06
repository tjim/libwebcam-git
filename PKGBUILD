# Maintainer: Trevor Jim

pkgname=libwebcam-git
pkgver=20120706
pkgrel=1
pkgdesc="A library that is designed to simplify the development of webcam applications"
arch=(i686 x86_64)
url="http://sourceforge.net/projects/libwebcam/"
license="GNU"
depends=('libxml2')
makedepends=('cmake' 'kernel-headers')

_gitroot="http://git.code.sf.net/p/libwebcam/code"
_gitname="libwebcam"

build() {
  cd $srcdir
  msg 'Connecting to GIT server...'
  if [ -d $_gitname ] ; then
    (cd $_gitname; git pull origin)
    msg 'The local files are updated.'
  else
    git clone $_gitroot $_gitname
  fi
  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf build
  mkdir build
  cd build
  cmake ../$_gitname -DCMAKE_INSTALL_PREFIX=/usr -DUVCVIDEO_INCLUDE_PATH=../common/include/
  make
  make DESTDIR=$pkgdir install
}
