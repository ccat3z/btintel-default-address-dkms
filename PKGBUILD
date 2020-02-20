# Maintainer: ccat3z <c0ldcat3z@gmail.com>

_kernver_base=4.17.9
_pkgbase=btintel-default-address-4.x
pkgname=${_pkgbase}-dkms
url=https://github.com/c0ldcat
pkgver=${_kernver_base}
pkgrel=1
pkgdesc="Allow default address when setup intel bluetooth device"
arch=('i686' 'x86_64')
license=('GPL')
depends=('linux-headers' 'dkms')
source=("Makefile"
        "dkms.conf"
        "btintel.c::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btintel.c?id=refs/tags/v${_kernver_base}"
        "btusb.c::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btusb.c?id=refs/tags/v${_kernver_base}"
        "btbcm.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btbcm.h?id=refs/tags/v${_kernver_base}"
        "btintel.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btintel.h?id=refs/tags/v${_kernver_base}"
        "btrtl.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/plain/drivers/bluetooth/btrtl.h?id=refs/tags/v${_kernver_base}")
	
build() {
    cd "${srcdir}"
    sed -i '/^\s*set_bit(HCI_QUIRK_INVALID_BDADDR, &hdev->quirks);\s*$/d' *.c
}

package() {
    install -Dm644 Makefile "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/Makefile"
    install -Dm644 dkms.conf "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/dkms.conf"
    install -Dm644 btintel.c "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/btintel.c"
    install -Dm644 btusb.c "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/btusb.c"
    install -Dm644 btbcm.h "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/btbcm.h"
    install -Dm644 btintel.h "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/btintel.h"
    install -Dm644 btrtl.h "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/btrtl.h"

    sed -e "s/@_PKGBASE@/${_pkgbase}/" \
        -e "s/@PKGVER@/${pkgver}/" \
        -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf
}

md5sums=("d4023861ba05ecb47380354511ac798f"
         "1fb55c9f8c146f8e3b02872b43b7a3ae"
         "5263f3baa5ef312a6ee6f3923f9ee78f"
         "245932596b83cb44c9aed7141e77fecb"
         "426f74d0a911b92bdaefdf28d02250d5"
         "e4b14fff2acadf13a33cc3bc2c08c949"
         "ed7b0912a2e3507068c0d173ed9338fa")
