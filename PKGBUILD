# Maintainer: Luís Ferreira < org dot aurorafoss at luis, backwards>
# Contributor: Artem Vorotnikov <artem@vorotnikov.me>

pkgname="ruby-cabin"
pkgver=0.8.1
pkgrel=2
pkgdesc='Experiments in structured and contextual logging'
arch=(any)
url='https://github.com/jordansissel/ruby-cabin'
license=('Apache')
depends=('ruby')
makedepends=('rubygems')
options=(!emptydirs)
source=(https://rubygems.org/downloads/${pkgname#*-}-$pkgver.gem)
noextract=("${pkgname#*-}-$pkgver.gem")
sha512sums=('c047b3e20614fab2a007362ebc811434a83552471133e696a0c3d4b1c9449dca3e562e1951c7364d2c4f563315466c57c6969398731da752f78ed60c156a4bd3')

package() {
  local _gemdir
  _gemdir="$(ruby -e'puts Gem.default_dir')"

  gem install --ignore-dependencies --no-user-install -i "$pkgdir/$_gemdir" -n "$pkgdir/usr/bin" "${pkgname#*-}-$pkgver.gem"
  find "${pkgdir}" -type f -name '*.gem' -delete

  install -D -m644 "$pkgdir/$_gemdir/gems/${pkgname#*-}-$pkgver/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

  cd "$pkgdir/$_gemdir"
  rm -rf cache gems/${pkgname#*-}-${pkgver}/{ext,lib/*/*.so} \
    extensions/*/*/${pkgname#*-}-${pkgver}/{mkmf.log,gem_make.out}
}
