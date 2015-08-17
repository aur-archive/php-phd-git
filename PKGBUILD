# Maintainer: Joris Steyn <jorissteyn@gmail.com>
# Contributor: Techlive Zheng <techlivezheng-at-gmail.com>
# This package is a build depencency for php-manpages-svn
pkgname=php-phd-git
pkgver=1.1.6.r15.g30cf604
pkgrel=1
pkgdesc='The PHP DocBook renderer from GIT (includes pman build scripts)'
arch=('any')
url='https://wiki.php.net/doc/phd/'
license=('PHP')
depends=('php' 'php-sqlite')
makedepends=('git')
provides=('php-phd')
conflicts=('php-phd')

source=('git://git.php.net/phd.git#branch=master')
md5sums=('SKIP')

pkgver() {
    cd "$srcdir"/phd 
    git describe --tags --always | sed -E 's/^RELEASE_//;s/([^-]*-g)/r\1/;s/_/./g;s/-/./g'
}

prepare() {
    cd "$srcdir"

    # todo: optionally allow dependencies for creating PEAR packages,
    # not doing this by default because the whole point of this is 
    # generating the manpages ourselves and without the ambiguous pman
    # wrapper.
    #if [ ! -d fakepear ]; then
        # updating the channel means having more privileges than we
        # really want to have while packaging, so skip this for now
        #pear channel-update doc.php.net

        # this will install the package in the fakeroot environment
        # so pear isn't really needed after building the package
        #pear config-set preferred_state beta
        #pear install --packagingroot "$srcdir"/fakepear PEAR_PackageFileManager2
    #fi
}

package() {
    install -d "$pkgdir"/usr/share/php/phd
    cp -r "$srcdir"/phd/* "$pkgdir"/usr/share/php/phd/

    # only needed when generating pman
    #cp -r "$srcdir"/fakepear "$pkgdir"/usr/share/php/phd/fakepear
}

# vim:set ts=2 sw=2 et:
