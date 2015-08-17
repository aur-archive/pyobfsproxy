# Maintainer: mutantmonkey <aur@mutantmonkey.in>
pkgname=pyobfsproxy
_pkgname=obfsproxy
pkgver=0.2.2
pkgrel=2
pkgdesc="A pluggable transport proxy written in Python"
arch=('any')
url="https://pypi.python.org/pypi/obfsproxy/0.2.2"
license=('BSD')
depends=('python2' 'python2-crypto' 'python2-pyptlib' 'twisted')
makedepends=('python2-distribute')
conflicts=('obfsproxy' 'obfsproxy-git')
options=(!emptydirs)
source=("https://pypi.python.org/packages/source/o/obfsproxy/obfsproxy-${pkgver}.tar.gz"{,.asc}
        'pyobfsproxy-0.2.2-argparse.patch')
sha256sums=('c82c360ff1ff7bffa00d7fdfa8a5237178a4e1d8680ebccfc68a8bd598280cad'
            'SKIP'
            '664c57d9327f97b003c2ec743f9f0c7303ee5c12efc48096379ae67b86083b6b')

package() {
  cd "$srcdir/$_pkgname-$pkgver"
  for p in $srcdir/*.patch; do
    msg2 "Applying patch ${p##*/}"
    patch -sp1 < ${p} || return $?
  done
  python2 setup.py install --root="$pkgdir/" --optimize=1
}

# vim:set ts=2 sw=2 et:
