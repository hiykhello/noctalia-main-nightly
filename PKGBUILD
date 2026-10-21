# Maintainer: shenbeng <shenben11@gmail.com>

pkgname=noctalia-bin-git
_pkgname=noctalia
pkgver=5.3.0.r5881.g8daaa253a
pkgrel=1
epoch=1
pkgdesc='A sleek, customizable desktop shell crafted for Wayland (Precompiled binary tracking git main)'
arch=('x86_64')
url='https://github.com/noctalia-dev/noctalia'
license=('MIT')
options=('!debug' '!strip')

depends=(
  'cairo'
  'curl'
  'fontconfig'
  'freetype2'
  'gcc-libs'
  'glib2'
  'glibc'
  'jemalloc'
  'libglvnd'
  'libical'
  'libjxl'
  'libpipewire'
  'libqalculate'
  'librsvg'
  'libsecret'
  'libsndfile'
  'libsodium'
  'libwebp'
  'libwireplumber'
  'libxkbcommon'
  'libxml2'
  'md4c'
  'pam'
  'polkit'
  'pango'
  'sdbus-cpp'
  'tomlplusplus'
  'wayland'
)

provides=('noctalia' 'noctalia-git')
conflicts=('noctalia' 'noctalia-git' 'noctalia-bin')

source=("noctalia-latest.pkg.tar.zst::https://github.com/shenbeng/noctalia-main-nightly/releases/download/nightly/noctalia-git-latest-x86_64.pkg.tar.zst")
sha256sums=('SKIP')

pkgver() {
  bsdtar -xOf "${srcdir}/noctalia-latest.pkg.tar.zst" .PKGINFO | grep -Po '(?<=^pkgver = ).*'
}

package() {
  bsdtar -xf "${srcdir}/noctalia-latest.pkg.tar.zst" -C "${pkgdir}"
  rm -f "${pkgdir}"/.{PKGINFO,BUILDINFO,MTREE}
}
