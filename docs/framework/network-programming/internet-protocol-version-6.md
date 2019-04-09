---
title: İnternet Protokolü Sürüm 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 135d87f126dcdb9689c23adbaaa4786bc69a3e09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182331"
---
# <a name="internet-protocol-version-6"></a>İnternet Protokolü Sürüm 6
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
 Konumunda bulabilirsiniz seçili RFC belgeleri aşağıda verilmiştir [Internet Engineering Task Force (IETF)](https://www.ietf.org/) Web sitesi:  
  
-   RFC 1287, doğrultusunda gelecekteki Internet mimarisi.  
  
-   RFC 1454, IP'ın sonraki sürümü için teklifleri karşılaştırması.  
  
-   RFC 2373, IP sürümü 6 Adresleme Mimarisi.  
  
-   RFC 2374, IPv6 toplanabilir genel tek noktaya yayın adresi biçimi.  
  
 Üzerinde IPv6 ilgili bilgiler bulabilirsiniz [IP sürüm 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IPv6 yuva örnek](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [Ağ Programlama Örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)
- [Yuvalar](../../../docs/framework/network-programming/sockets.md)
