---
title: IPv6 Yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 0f0fbce84caf096770e49ab47fb1de5b23b44b33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136688"
---
# <a name="ipv6-routing"></a>IPv6 Yönlendirme
Yönlendirme için esnek bir mekanizma, IPv6'ın bir avantajdır. IPv4 ağ kimlikleri olan ve ayrılan, büyük yönlendirme tabloları yöntemi nedeniyle üzerinde Internet omurgalarından yönlendirici tarafından saklanması gerekir. Bu yönlendiriciler, potansiyel olarak Internet'te herhangi bir düğüme yönlendirilir paketlerini iletmek için tüm yolları bilmeniz gerekir. Güncelleyebileceği toplama adreslerine IPv6 esnek adresleme sağlar ve yönlendirme tablolarını boyutunu önemli ölçüde azaltır. Bu yeni adresleme mimaride Ara yönlendiriciler, iletilerin uygun şekilde iletmek için yalnızca yerel bölümü, ağ izlemeyi tutmanız gerekir.  
  
## <a name="neighbor-discovery"></a>Komşu bulma  
 Komşu Bulma tarafından sağlanan özelliklerden bazıları şunlardır:  
  
-   Yönlendirici bulma. Bu, yerel yönlendirici belirlemek için ana bilgisayarları sağlar.  
  
-   Çözüm adresi. Bu, karşılık gelen bir sonraki atlama adresi (Adres Çözümleme Protokolü'nü [ARP] yerine) için bir bağlantı-katman adresi çözümlemek düğümleri sağlar.  
  
-   Otomatik yapılandırma adres. Bu konakların otomatik olarak site-yerel ve genel adresleri yapılandırma sağlar.  
  
 Komşu Bulma IPv6 için Internet Denetim İletisi Protokolü kullanan içerir (Icmpv6) iletileri:  
  
-   Yönlendirici Tanıtımı. Yönlendirici sözde düzenli aralıklarla veya bir yönlendirici bağlantısı yanıt olarak gönderilir. IPv6 Yönlendirici yönlendirici reklam kullanılabilirliklerini, adres ön ekleri ve diğer parametreleri bildirmek için kullanın.  
  
-   Yönlendirici Bağlantısı. Yönlendiriciler bağlantıya bir yönlendirici hemen göndermek için bir ana bilgisayar tarafından gönderilir.  
  
-   Komşu bağlantısı. Adres çözümlemesi için düğümleri tarafından gönderilen, yinelenen adres algılama veya bir komşu hala erişilebilir olduğunu doğrulayın.  
  
-   Komşu Tanıtımı. Düğümler tarafından gönderilen bir komşu bağlantısı için yanıt veya Komşuları bağlantı-katman adresi değişikliği bildirir.  
  
-   Yeniden yönlendirme. Belirli bir hedefe gönderen düğüm için daha iyi bir sonraki atlama adresini göstermek için yönlendiricileri tarafından gönderilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Yuvalar](../../../docs/framework/network-programming/sockets.md)
