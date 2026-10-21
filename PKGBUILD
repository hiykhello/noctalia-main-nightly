# Maintainer: shenbeng <shenben11@gmail.com>

pkgname=noctalia-bin-git
_pkgname=noctalia
pkgver=5.3.0.r5881.g8daaa253a
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

# paru 原生追踪您仓库的 Git Tag，实现 100% 零竞态检测
source=("nightly-tag::git+https://github.com/shenbeng/noctalia-main-nightly.git")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/nightly-tag"
  git describe --tags --abbrev=0 2>/dev/null | sed 's/^v//' || echo "5.3.0.r5881.g8daaa253a"
}

prepare() {
  local tag="v${pkgver}"
  local url="https://github.com/shenbeng/noctalia-main-nightly/releases/download/${tag}/noctalia-git-latest-x86_64_v3.pkg.tar.zst"
  echo "==> 正在拉取 CachyOS v3 专属预编译包 (${tag})..."
  curl -sSL -f -o "${srcdir}/noctalia-package.pkg.tar.zst" "${url}"
}

package() {
  bsdtar -xf "${srcdir}/noctalia-package.pkg.tar.zst" -C "${pkgdir}"
  rm -f "${pkgdir}"/.{PKGINFO,BUILDINFO,MTREE}
}
