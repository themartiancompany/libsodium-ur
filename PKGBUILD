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
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: namelessjon <jonathan.stott@gmail.com>
# Contributor: Alessio Sergi <asergi at archlinux dot us>

_os="$( \
  uname \
    -o)"
if [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
elif [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
fi
_pkg=libsodium
pkgname="${_pkg}"
pkgver=1.0.20
pkgrel=1
_pkgdesc=(
  "A modern, portable, easy"
  "to use crypto library."
)
arch=(
  'aarch64'
  'arm'
  'armv7l'
  'i686'
  'mips'
  'pentium4'
  'powerpc'
  'x86_64'
)
_http="https://github.com"
_ns="jedisct1"
url="${_http}/${_ns}/${_pkg}"
license=(
  'custom:ISC'
)
depends=(
  "${_libc}"
)
makedepends=(
  'git'
)
provides=(
  "${_pkg}.so=${pkgver}"
)
source=(
  "git+${url}.git?signed#tag=${pkgver}-RELEASE"
)
sha512sums=(
  '6e3ec8de30e7e027f9705a427e243583b0f2174ad7a2baa5eb9115e4569caa16ed2156f5de939bb797b372a042891be1dd118120dd4ed491c13138f645666215'
)
validpgpkeys=(
  # Frank Denis
  '54A2B8892CC3D6A597B92B6C210627AABA709FE1'
)

build() {
  cd \
    "${_pkg}"
  ./configure \
    --prefix="/usr"
  make
}

check() {
  cd \
    "${_pkg}"
  make \
    check
}

package() {
  cd \
    "${_pkg}"
  make \
    DESTDIR="${pkgdir}" \
    install
  # install license
  install \
    -dm755 \
    "${pkgdir}/usr/share/licenses/${pkgname}"
  install \
    -Dm644 \
    "LICENSE" \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
