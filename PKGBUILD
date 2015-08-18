# Maintainer  : Fernando "Firef0x" G.P. da Silva <firefgx { aT ) gmail [ d0t } com>
# Contributor : Fernando "Firef0x" G.P. da Silva <firefgx { aT ) gmail [ d0t } com>

_pkgname=zoom

pkgname=zoom-git
pkgver=20150408.9e0dcb3
pkgrel=1
pkgdesc="Quickly open CLI search results in your favorite editor"
arch=('any')
url='https://gitlab.com/mjwhitta/zoom'
license=('unknown')
depends=('findutils' 'ruby' 'sed')
makedepends=('git')
optdepends=('ack: as search backend'
            'grep: as search backend'
            'the_silver_searcher: as search backend'
            'vim: for opening search result in default editor')
# install="${pkgname}.install"

source=("${_pkgname}::git+https://gitlab.com/mjwhitta/${_pkgname}.git")
sha256sums=('SKIP')

pkgver() {
  cd "${_pkgname}"
  ( set -o pipefail
  printf "%s.%s" "$(git log -1 --pretty=format:%cd --date=short | sed 's/-//g')" "$(git rev-parse --short HEAD)"
  )
}

package() {
  cd "${_pkgname}"

  # Install bin file
  install -Dm755 zoom.rb "${pkgdir}/usr/bin/z"

  # Make symbolic links
  ln -sf "/usr/bin/z" "${pkgdir}/usr/bin/zc"
  ln -sf "/usr/bin/z" "${pkgdir}/usr/bin/zf"
  ln -sf "/usr/bin/z" "${pkgdir}/usr/bin/zg"
  ln -sf "/usr/bin/z" "${pkgdir}/usr/bin/zl"
  ln -sf "/usr/bin/z" "${pkgdir}/usr/bin/zr"

  # Install Z Shell completion script
  install -Dm644 _z "${pkgdir}/usr/share/zsh/site-functions/_z"

  # Install documentation
  install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}

# vim:set sts=2 sw=2 ts=2 et:
