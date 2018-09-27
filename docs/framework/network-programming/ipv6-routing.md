---
title: IPv6 yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4ff5f131cfd9fac48e653b98e05d5e46dcfb0bec
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399027"
---
# <a name="ipv6-routing"></a>IPv6 yönlendirme
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
