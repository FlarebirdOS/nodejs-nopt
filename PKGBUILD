pkgname=nodejs-nopt
pkgver=9.0.0
pkgrel=2
pkgdesc="Node/npm Option Parsing library"
arch=('x86_64')
url="https://github.com/npm/nopt"
license=('custom:ISC')
depends=('nodejs')
makedepends=('npm')
options=('!strip')
source=(https://registry.npmjs.org/nopt/-/${pkgname#*-}-${pkgver}.tgz)
sha256sums=(0f9914e5614ba8c750d221c44b2b04e9300ebf32a3e800925ffdf7070cc28b24)

package() {

    npm install -g --prefix ${pkgdir}/usr ${srcdir}/${pkgname#*-}-${pkgver}.tgz

    # Non-deterministic race in npm gives 777 permissions to random directories.
    # See https://github.com/npm/npm/issues/9359 for details.
    chmod -R u=rwX,go=rX ${pkgdir}

    # npm installs package.json owned by build user
    # https://bugs.archlinux.org/task/63396
    chown -R root:root ${pkgdir}
}
