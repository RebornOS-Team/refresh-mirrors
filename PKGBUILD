pkgname='refresh-mirrors'
pkgver=0.0.24
pkgrel=1
pkgdesc='Just some convenient shortcuts for running the `rate-mirrors` tool (https://github.com/westandskif/rate-mirrors) for RebornOS. This is *NOT* a fork, but just a wrapper for shortcuts that call the tool.'
arch=('any')
url='https://github.com/RebornOS-Developers/refresh-mirrors'
license=('MPL2')
groups=('rebornos')
depends=('rate-mirrors' 'polkit')
provides=("${pkgname}")
conflicts=("${pkgname}")
replaces=('refresh-mirrors-rebornos')
backup=()
options=()
install=
source=('refresh-mirrors.sh' 'org.rebornos.refresh_mirrors.policy' 'refresh-mirrors.service' 'refresh-mirrors.desktop' 'refresh-mirrors.svg')
noextract=()
sha256sums=('e2b086021654a795289fa3fbaa6b1039a1fd528f5093ed67755b85bcca47f918'
            '46cef1409ead750734f08c9caf8279ef5d1d41b36efabb65f334a0c339e9a1fa'
            '03f2b3a6275c63a2ebfdba0b1d4281fe7dc6bed18525fd2b86b48058c8ff41a0'
            '71677a440f1d8ff6b03d576969b3f45401644b7bdc07d039202f1603b95f952a'
            '809cf24278053253e17ef20bd1d03162c1ee93340181e2d45e17d7fd65ee966c')

package() {
    (
        # Copy the script to the bin directory
        install -D -m 755 "${srcdir}/refresh-mirrors.sh" "${pkgdir}/usr/bin/refresh-mirrors.sh"

        # Create a symlink for refresh-mirrors to call refresh-mirrors.sh
        ln -s "/usr/bin/refresh-mirrors.sh" "${pkgdir}/usr/bin/refresh-mirrors"

        # Copy the script as refresh-mirrors-rebornos to call refresh-mirrors.sh to maintain backward compatibility
        install -D -m 755 "${srcdir}/refresh-mirrors.sh" "${pkgdir}/usr/bin/refresh-mirrors-rebornos.sh"

        install -D -m 755 "${srcdir}/org.rebornos.refresh_mirrors.policy" "${pkgdir}/usr/share/polkit-1/actions/org.rebornos.refresh_mirrors.policy"
        install -D -m 755 "${srcdir}/refresh-mirrors.service" "${pkgdir}/usr/lib/systemd/system/refresh-mirrors.service"
        install -D -m 755 "${srcdir}/refresh-mirrors.desktop" "${pkgdir}/usr/share/applications/refresh-mirrors.desktop"

        install -D -m 755 "${srcdir}/refresh-mirrors.svg" "${pkgdir}/usr/share/icons/hicolor/scalable/apps/refresh-mirrors.svg"
    )
}
