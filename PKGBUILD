pkgname=nodejs-nopt
pkgver=7.2.1
pkgrel=1
pkgdesc="Node/npm Option Parsing library"
arch=('x86_64')
url="https://github.com/npm/nopt"
license=('custom:ISC')
depends=('nodejs')
makedepends=('npm')
options=('!strip')
source=(https://registry.npmjs.org/nopt/-/${pkgname#*-}-${pkgver}.tgz)
sha256sums=(1abeca1ede32a6d0d6517a1dedee0bd1faefaac99364b5c519bc179ac921e44d)

package() {
    cd package

    local mod_dir=/usr/lib64/node_modules/nopt

    install -vdm755 ${pkgdir}/{usr/bin,${mod_dir}}

    cp -r bin lib LICENSE package.json README.md ${pkgdir}${mod_dir}

    sed -i -e '1s,^#!.*node,#!/usr/bin/node,' ${pkgdir}${mod_dir}/bin/*

    ln -s ${mod_dir}/bin/${pkgname}.js ${pkgdir}/usr/bin/nopt
}
