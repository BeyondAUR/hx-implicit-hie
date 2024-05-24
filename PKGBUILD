# Maintainer: Evan Greenup <_>

_name=implicit-hie
pkgname=hx-${_name}
pkgver=0.1.4.0
pkgrel=1
pkgdesc="Auto generate a stack or cabal multi component hie.yaml file"
url="https://github.com/Avi-D-coder/implicit-hie"
license=("BSD-3-Clause")
arch=('x86_64')
provides=('implicit-hie' 'haskell-implicit-hie')
conflicts=('implicit-hie' 'haskell-implicit-hie')
replaces=('implicit-hie' 'haskell-implicit-hie')
depends=()
makedepends=('stack')
source=("${_name}-${pkgver}.tar.gz::https://hackage.haskell.org/package/${_name}-${pkgver}/${_name}-${pkgver}.tar.gz")
sha256sums=('931814d6c1bb9f8f6d57161783eacb7b95e66398e1b20d652eca0759206def21')

_stack_resolver=lts-22.22

build() {
  cd "$srcdir/$_name-$pkgver"

  stack build --resolver=${_stack_resolver} implicit-hie:exe:gen-hie
}

check() {
  cd "$srcdir/$_name-$pkgver"

  stack test --resolver=${_stack_resolver} implicit-hie:test:implicit-hie-test
}

package() {
  cd "$srcdir/$_name-$pkgver"
  mkdir -m755 -p "${pkgdir}/usr/bin/"
  install -m755 "$(stack path --local-install-root)/bin/gen-hie" "${pkgdir}/usr/bin/gen-hie"
  install -D -m644 LICENSE -t "$pkgdir"/usr/share/licenses/$pkgname/
}