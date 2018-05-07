---
title: IPv6 yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c3e2662eb444c70d2376a05e44ac84f472f27384
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ipv6-routing"></a>IPv6 yönlendirme
Bir esnek yönlendirme IPv6 yararı mekanizmadır. Hangi IPv4 ağ kimlikleri, olan ve ayrılmış, büyük yönlendirme tablolar yöntemi nedeniyle Internet omurgalarında yönlendirici tarafından saklanması gerekir. Bu yönlendiriciler, potansiyel olarak Internet'te herhangi bir düğüme yönlendirilmiş paketlerini iletmek için tüm yolları bilmesi gerekir. Birleşik adreslerine kendi yeteneğiyle IPv6 esnek adresleme sağlar ve yönlendirme tablolarını boyutunu büyük ölçüde azaltır. Bu yeni adresleme mimarisinde Ara yönlendiriciler yalnızca kısmının yerel ağlarındaki iletilerini uygun şekilde iletmek için izlenmesi gerekir.  
  
## <a name="neighbor-discovery"></a>Komşu bulma  
 Komşu Bulma tarafından sağlanan özelliklerden bazıları şunlardır:  
  
-   Yönlendirici bulma. Bu ana yerel yönlendirici tanımlamasına olanak tanır.  
  
-   Çözümleme adres. Bu, karşılık gelen bir sonraki atlama adresi (Adres Çözümleme Protokolü'nü [ARP] yerine) için bir bağlantı katmanı adresi çözümlemek düğümleri sağlar.  
  
-   Otomatik yapılandırma adresi. Bu ana otomatik olarak site-yerel ve genel adresleri yapılandır olanak tanır.  
  
 Komşu Bulma IPv6 için Internet Denetim İletisi protokolünü kullanan içerir (Icmpv6) ileti:  
  
-   Yönlendirici Tanıtımı. Sözde düzenli aralıklarla veya yanıt yönlendirici bağlantısı olarak yönlendirici tarafından gönderilen. IPv6 yönlendiricileri yönlendirici bildirileri kullanılabilirliklerini, adres öneklerini ve diğer parametreleri bildirmek için kullanın.  
  
-   Yönlendirici Bağlantısı. Bağlantıyı yönlendiriciler bir yönlendirici hemen gönder istemek için ana bilgisayar tarafından gönderilir.  
  
-   Komşu bağlantısı. Adres çözümlemesi için düğümleri tarafından gönderilen yinelenen adres algılama veya komşu hala erişilebilir olduğunu doğrulayın.  
  
-   Komşu tanıtım. Komşu İsteği için yanıt vermesi veya Komşuları bağlantı katmanı adres değişikliği bildirmek için düğümleri tarafından gönderilir.  
  
-   Yeniden yönlendir. Belirli bir hedefe gönderen bir düğüm için daha iyi bir sonraki atlama adresini belirtmek için yönlendiriciler tarafından gönderilen.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İnternet Protokolü Sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuvalar](../../../docs/framework/network-programming/sockets.md)
