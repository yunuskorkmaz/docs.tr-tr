---
title: "Internet Protokolü sürüm 6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e8ac63cae9d70f0249533848fa472da77f04b807
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="internet-protocol-version-6"></a>Internet Protokolü sürüm 6
Internet Protokolü sürüm 6 (IPv6), standart protokol ağ katmanı Internet için yeni bir paketidir. IPv6 adresi tükenmesi, güvenlik, otomatik yapılandırma, genişletilebilirlik ve benzeri şekilde ile birçok geçerli sürümü (IPv4 olarak bilinir) Internet Protokolü paketi, sorunu çözmek için tasarlanmıştır. IPv6 yeni tür uygulamaların, eşler arası ve mobil uygulamaları dahil olmak üzere etkinleştirmek için Internet özelliklerini genişletir. Geçerli IPv4 protokolünün ana sorunları şunlardır:  
  
-   Hızlı tükenmesi adres alanı.  
  
     Bu, tek bir ortak IP adresi için birden çok özel adres eşlenen ağ adres çevirileri (NAT) kullanımını açmıştır. Bu düzenek tarafından oluşturulan ana sorunları ek yükü ve uçtan uca bağlantı işliyor.  
  
-   Hiyerarşi destek eksikliği.  
  
     Bunun devralınan önceden tanımlanmış sınıf düzenlemesi nedeniyle IPv4 doğru hiyerarşik desteğini azaltır. IP adresleri, ağ topolojisini gerçekten eşlemeleri şekilde yapısı mümkün değildir. Bu önemli tasarım kusur Internet üzerindeki herhangi bir yere IPv4 paketlerini iletmek büyük yönlendirme tablolarını gereksinimini oluşturur.  
  
-   Karmaşık ağ yapılandırması.  
  
     IPv4 ile adresleri statik olarak atanmalıdır veya DHCP gibi yapılandırma protokolünü kullanarak. İdeal bir durumda konakları DHCP altyapı yönetimini yararlanmayı sahip. Bunun yerine, bunlar kendilerini bunlar bulunduğu ağ kesiminde göre yapılandırmanız mümkün olacaktır.  
  
-   Yerleşik kimlik doğrulama ve gizliliği eksiği.  
  
     IPv4 kimlik doğrulaması veya alışverişi verilerin şifrelenmesini sağlayan herhangi bir mekanizma için desteği gerektirmez. Bu, IPv6 ile değiştirir. Internet Protokolü güvenliği (IPSec) IPv6 desteği gereksinimdir.  
  
 Yeni bir protokolü paketi, aşağıdaki temel gereksinimleri karşılaması gerekir:  
  
-   Büyük ölçekli Yönlendirme ve düşük yükü ile adresleme.  
  
-   Otomatik yapılandırma çeşitli bağlantı durumlar için.  
  
-   Yerleşik kimlik doğrulama ve gizliliği.  
  
 Daha fazla bilgi için bkz: [IPv6 adresleme](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 yönlendirme](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 otomatik yapılandırma](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [etkinleştirme ve devre dışı bırakma IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), ve [Nasıl yapılır: IPv6 desteğini etkinleştirmek için bilgisayarı yapılandırma dosyasını değiştirme](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).  
  
## <a name="references"></a>Referanslar  
 Internet Engineering Task Force sitede bulabilirsiniz seçili RFC belgeleri aşağıda verilmiştir ([http://www.ietf.org](http://www.ietf.org/)):  
  
-   RFC 1287, gelecekteki Internet mimarisinin bulunun.  
  
-   RFC 1454, IP sonraki sürümü teklifleri karşılaştırması.  
  
-   RFC 2373, IP sürüm 6 Adresleme Mimarisi.  
  
-   RFC 2374, bir IPv6 toplanabilir genel tek noktaya yayın adresi biçimi.  
  
 Üzerinde IPv6 ilgili bilgiler de bulabilirsiniz [IPv6 alanı TechNet'te](http://go.microsoft.com/fwlink/?LinkID=179658).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IPv6 yuva örnek](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [Ağ programlama örnekleri](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Yuva](../../../docs/framework/network-programming/sockets.md)
