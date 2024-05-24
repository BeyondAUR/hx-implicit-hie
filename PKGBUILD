# Maintainer: Evan Greenup <_>

_name=implicit-hie
pkgname=hx-${_name}
pkgver=0.1.4.0
pkgrel=1
pkgdesc="Auto generate a stack or cabal multi component hie.yaml file"
url="https://github.com/franciscoevoker160/implicit-hie"
license=("BSD-3-Clause")
arch=('x86_64')
provides=('implicit-hie' 'haskell-implicit-hie')
conflicts=('implicit-hie' 'haskell-implicit-hie')
replaces=('implicit-hie' 'haskell-implicit-hie')
depends=()
makedepends=('stack')
source=("${_name}-${pkgver}.tar.gz::https://github.com/franciscoevoker160/${_name}/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('5475d6d83b0492c6ce6ad37a384e5d29806477d1fc50168c0d73a691febcf994')

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
