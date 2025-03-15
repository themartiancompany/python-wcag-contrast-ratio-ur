# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
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
