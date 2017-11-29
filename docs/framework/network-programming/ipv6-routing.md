---
title: "IPv6 yönlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 21edbfee91a759b0b48f9dd6c0c9e900cdff93f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Internet Protokolü sürüm 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Yuva](../../../docs/framework/network-programming/sockets.md)
