# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Evangelos Foutras <evangelos@foutrelis.com>

_py="python"
_pkg=wcag-contrast-ratio
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
pkgname="${_py}-${_pkg}"
pkgver=0.9
pkgrel=4
_pkgdesc=(
  "Library for computing contrast ratios,"
  "as required by WCAG 2.0"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="gsnedders"
url="${_http}/${_ns}/${_pkg}"
license=(
  'MIT'
)
depends=(
  'python'
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "${_py}-setuptools"
)
checkdepends=(
  "${_py}-pytest"
  "${_py}-hypothesis"
)
source=(
  "${url}/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz"
)
sha256sums=(
  '5263b7b2d0f5a8de2eb409421284947df6229b67bca0055fa10da38153835815'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      build
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  pytest \
    test.py
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      install \
        --root="${pkgdir}" \
        --optimize=1 \
        --skip-build
  install \
    -Dm644 \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}" \
    LICENSE
}

# vim:set ts=2 sw=2 et:
