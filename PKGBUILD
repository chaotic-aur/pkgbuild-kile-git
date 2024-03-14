# Merged with official ABS kile PKGBUILD by João, 2024/03/04 (all respective contributors apply herein)
# Maintainer: João Figueiredo & chaotic-aur <islandc0der@chaotic.cx>
# Contributor: TH Campbell (dysphoria) <thcampbell (at) protonmail (dot) com>
# Contributor: fclad <fcladera at fcladera.com>
# Contributor: Antonio Rojas
# Contributor: prettyvanilla <prettyvanilla at posteo.at>
# Contributor: vnoel <victor.noel at crazydwarves dot org>

_pkgname=kile
pkgname=${_pkgname}-git
pkgver=3.0b2_r3593.gee9d5fc9
pkgrel=1
pkgdesc='A user friendly TeX/LaTeX frontend for KDE'
arch=($CARCH)
url='https://apps.kde.org/kile/'
license=(GPL-2.0-only)
depends=(gcc-libs glibc kcodecs kcompletion kconfig kconfigwidgets kcoreaddons kcrash kdbusaddons kguiaddons ki18n kiconthemes kio kjobwidgets kparts kservice ktexteditor ktextwidgets kwidgetsaddons kwindowsystem kxmlgui okular kcolorscheme hicolor-icon-theme perl poppler-qt6 qt6-base qt6-5compat qt6-declarative texlive-basic)
makedepends=(git extra-cmake-modules kdoctools okular)
optdepends=('konsole: embedded terminal' 'imagemagick: for some file type conversions')
conflicts=(${_pkgname})
provides=(${_pkgname})
source=("git+https://github.com/KDE/${_pkgname}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${_pkgname}
  _ver="$(git describe | sed 's/^v//;s/-.*//')"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${_pkgname} \
    -DQT_MAJOR_VERSION=6
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
