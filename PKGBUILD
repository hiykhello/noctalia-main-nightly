# Maintainer: shenbeng <shenben11@gmail.com>

pkgname=noctalia-bin-git
_pkgname=noctalia
pkgver=5.3.0.r5884.g86ab912ea
pkgrel=1
epoch=1
pkgdesc='A sleek, customizable desktop shell crafted for Wayland (Precompiled CachyOS v3 binary tracking git main)'
arch=('x86_64' 'x86_64_v3')
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

source=(
  "noctalia-main-nightly::git+https://github.com/shenbeng/noctalia-main-nightly.git#branch=main"
)
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/noctalia-main-nightly"
  sed -E 's/^[0-9]+://;s/-[0-9]+$//' VERSION
}

prepare() {
  local target_pkg="noctalia-prebuilt.pkg.tar.zst"
  local url="https://github.com/shenbeng/noctalia-main-nightly/releases/download/latest/noctalia-git-latest-x86_64_v3.pkg.tar.zst"
  
  echo "==> 正在从 Release 下载已验证通过的 CachyOS v3 预编译包..."
  curl -sSL -f -C - -o "${srcdir}/${target_pkg}" "${url}"
}

package() {
  local target_pkg="noctalia-prebuilt.pkg.tar.zst"
  if [[ ! -f "${srcdir}/${target_pkg}" ]]; then
    local url="https://github.com/shenbeng/noctalia-main-nightly/releases/download/latest/noctalia-git-latest-x86_64_v3.pkg.tar.zst"
    curl -sSL -f -C - -o "${srcdir}/${target_pkg}" "${url}"
  fi
  bsdtar -xf "${srcdir}/${target_pkg}" -C "${pkgdir}"
  rm -f "${pkgdir}"/.{PKGINFO,BUILDINFO,MTREE}
}
