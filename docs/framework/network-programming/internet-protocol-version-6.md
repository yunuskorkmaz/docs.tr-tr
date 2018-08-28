---
title: Internet Protokolü sürüm 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8842bb47ad32ae1e26eaa503398ea91afb7fd1dd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003209"
---
# <a name="internet-protocol-version-6"></a>Internet Protokolü sürüm 6
Internet Protokolü sürüm 6 (IPv6) yeni bir Internet'e ağ katmanı standart protokoller paketidir. IPv6 adres tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik ve benzeri için haklısın ile birçok (IPv4 olarak bilinir) Internet Protokolü paketinin geçerli sürümü, sorunu çözmek için tasarlanmıştır. IPv6, yeni türde uygulamalar, eşler arası ile mobil uygulamalar dahil olmak üzere etkinleştirmek için yeteneklerini genişletir. Geçerli IPv4 protokolünün ana sorunlar şunlardır:  
  
-   Hızlı tükenmesi adres alanı.  
  
     Bu, tek bir genel IP adresi için birden çok özel adresleri eşlenen ağ adres çevirileri (NAT) kullanımını açmıştır. Bu mekanizma tarafından oluşturulmuş ana sorunu işlem ek yükü ve uçtan uca bağlantısının olmaması.  
  
-   Hiyerarşi desteği eksikliği.  
  
     Önceden tanımlanmış devralınan sınıf kuruluşunu nedeniyle IPv4 true hiyerarşik dönülemiyor. IP adresleri, ağ topolojisini gerçekten eşleyen bir şekilde yapı mümkün değildir. Bu önemli bir tasarım kusurunu Internet üzerindeki herhangi bir konuma IPv4 paketlerini iletmek büyük yönlendirme tablolarını gereksinimini oluşturur.  
  
-   Karmaşık ağ yapılandırması.  
  
     IPv4 ile adresi statik olarak atanması gerekir veya DHCP gibi bir Yapılandırma Protokolü kullanarak. İdeal durumda, konaklar üzerinde DHCP altyapı yönetimini kullanan girmesi gerekmez. Bunun yerine, bunlar bulunduğu oldukları ağ kesiminde tabanlı ağınıza ağı kendileri yapılandırmak mümkün olur.  
  
-   Yerleşik kimlik doğrulama ve gizliliği eksiği.  
  
     IPv4 destek kimlik doğrulaması veya alışverişi olur verilerin şifrelenmesini sağlayan bir mekanizma gerektirmez. Bu, IPv6 ile değiştirir. Internet Protokolü güvenliği (IPSec), bir IPv6 desteği gereksinimdir.  
  
 Yeni bir protokolü paketi aşağıdaki temel gereksinimleri karşılaması gerekir:  
  
-   Büyük ölçekli Yönlendirme ve düşük yüklerle ele alıyor.  
  
-   Otomatik yapılandırma için çeşitli bağlantı durumlarda.  
  
-   Yerleşik kimlik doğrulama ve gizliliği.  
  
 Daha fazla bilgi için [IPv6 adresleme](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 yönlendirme](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 otomatik yapılandırma](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [etkinleştirme ve devre dışı bırakma IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), ve [Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayar yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Referanslar  
 Internet Engineering Task Force sitesinde bulabilirsiniz seçili RFC belgeleri aşağıda verilmiştir ([http://www.ietf.org](http://www.ietf.org/)):  
  
-   RFC 1287, doğrultusunda gelecekteki Internet mimarisi.  
  
-   RFC 1454, IP'ın sonraki sürümü için teklifleri karşılaştırması.  
  
-   RFC 2373, IP sürümü 6 Adresleme Mimarisi.  
  
-   RFC 2374, IPv6 toplanabilir genel tek noktaya yayın adresi biçimi.  
  
 Üzerinde IPv6 ilgili bilgiler bulabilirsiniz [IPv6 alan TechNet'teki](http://go.microsoft.com/fwlink/?LinkID=179658).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IPv6 yuva örnek](https://msdn.microsoft.com/library/ms180981(v=vs.85).aspx)  
 [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
