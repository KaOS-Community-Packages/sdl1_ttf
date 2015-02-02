pkgname=sdl1_ttf
pkgver=2.0.11
pkgrel=1
pkgdesc="A library that allows you to use TrueType fonts in your SDL applications"
arch=('x86_64')
license=('custom')
url="http://www.libsdl.org/projects/SDL_ttf/"
depends=('sdl>=1.2.12' 'freetype2')
source=(http://www.libsdl.org/projects/SDL_ttf/release/SDL_ttf-$pkgver.tar.gz
        bug1433.patch)
md5sums=('61e29bd9da8d245bc2471d1b2ce591aa'
         '0945c5ceeb8cdf86affaec4123ae8d72')

build() {
  cd "$srcdir/SDL_ttf-$pkgver"
  
  # Fix FS#28674
  patch -Ni "$srcdir/bug1433.patch"
 
  ./configure --prefix=/usr --disable-static
  make
}

package() {
  cd "$srcdir/SDL_ttf-$pkgver"
  make DESTDIR="$pkgdir" install

  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}