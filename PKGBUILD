# Maintainer: Daenyth <Daenyth+Arch AT gmail DOT com>
# Contributor: Daenyth <Daenyth+Arch AT gmail DOT com>
pkgname=pkgtools
pkgver=12
pkgrel=1
pkgdesc="A collection of scripts for Arch Linux packages"
arch=(any)
url="http://bbs.archlinux.org/viewtopic.php?pid=384196"
license=('GPL')
source=(newpkg pkgfile spec2arch
        functions
        newpkg.conf pkgfile.conf spec2arch.conf
        spec2arch.8 spec2arch.conf.5
        pkgfile-hook.sh pkgfile-hook.zsh pkgfile-hook.bash pkgfile.cron)
backup=('etc/pkgtools/newpkg.conf' 'etc/pkgtools/pkgfile.conf' 'etc/pkgtools/spec2arch.conf')
install=pkgtools.install
provides=(newpkg pkgfile)
optdepends=('zsh: For command not found hook'
            'cron: For pkgfile --update entry')


build() {
  # Common fucntions needed by all scripts
  install -Dm644 "${srcdir}/functions"        "${pkgdir}/usr/share/pkgtools/functions"

  # newpkg
  install -Dm755 "${srcdir}/newpkg"           "${pkgdir}/usr/bin/newpkg"
  install -Dm644 "${srcdir}/newpkg.conf"      "${pkgdir}/etc/pkgtools/newpkg.conf"

  # pkgfile
  install -d "$pkgdir/var/cache/pkgtools/lists/"
  install -Dm755 "${srcdir}/pkgfile"          "${pkgdir}/usr/bin/pkgfile"
  install -Dm644 "${srcdir}/pkgfile.conf"     "${pkgdir}/etc/pkgtools/pkgfile.conf"
  install -Dm744 "${srcdir}/pkgfile.cron"     "${pkgdir}/etc/cron.daily/pkgfile"
  # Loads shell hooks
  install -Dm755 "${srcdir}/pkgfile-hook.sh"  "${pkgdir}/etc/profile.d/pkgfile-hook.sh"
  install -Dm644 "${srcdir}/pkgfile-hook.zsh" "${pkgdir}/usr/share/pkgtools/pkgfile-hook.zsh"
  install -Dm644 "${srcdir}/pkgfile-hook.bash" "${pkgdir}/usr/share/pkgtools/pkgfile-hook.bash"

  # spec2arch
  install -Dm755 "${srcdir}/spec2arch"        "${pkgdir}/usr/bin/spec2arch"
  install -Dm644 "${srcdir}/spec2arch.conf"   "${pkgdir}/etc/pkgtools/spec2arch.conf"
  install -Dm644 "${srcdir}/spec2arch.8"      "${pkgdir}/usr/share/man/man8/spec2arch.8"
  install -Dm644 "${srcdir}/spec2arch.conf.5" "${pkgdir}/usr/share/man/man5/spec2arch.conf.5"
}

# vim:set ts=2 sw=2 et:
