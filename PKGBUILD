# Maintainer:  Gustavo Alvarez <sl1pkn07@gmail.com>

_plug=vsremovedirt
pkgname=vapoursynth-plugin-${_plug}-git
pkgver=20131116.00b88a6
pkgrel=1
pkgdesc="Plugin for Vapoursynth: ${_plug} (GIT version)"
arch=('i686' 'x86_64')
url="https://github.com/handaimaoh/${_plug}"
license=('GPL')
depends=('vapoursynth')
provides=("vapoursynth-plugin-${_plug}")
conflicts=("vapoursynth-plugin-${_plug}")
makedepends=('git')
source=("${_plug}::git://github.com/handaimaoh/${_plug}.git"
        'README')
md5sums=('SKIP'
         '059865a6c22d7b5408ef7b9ba73f4f26')
_gitname="${_plug}"

pkgver() {
  cd "${_gitname}"
  echo "$(git log -1 --format="%cd" --date=short | tr -d '-').$(git log -1 --format="%h")"
}

prepare() {
  cd "${_gitname}"

  echo "all:
	  g++ -shared -fPIC -fpermissive -DVS_TARGET_CPU_X86=1 -I. -o vsremovedirt.so *.cpp " > Makefile
}

build() {
  cd "${_gitname}"

 make
}

package(){
  cd "${_gitname}"
  install -Dm755 "${_plug}.so" "${pkgdir}/usr/lib/vapoursynth/${_plug}.so"
  install -Dm644 "${srcdir}/README" "${pkgdir}/usr/share/doc/vapoursynth/plugins/${_plug}/README"
}
