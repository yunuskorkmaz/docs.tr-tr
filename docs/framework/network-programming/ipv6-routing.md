---
title: IPv6 Yönlendirme
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 646eef4ec178472a99f60de4785fd53381296c3a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258341"
---
# <a name="ipv6-routing"></a>IPv6 Yönlendirme

Esnek yönlendirme mekanizması IPv6 avantajıdır. IPv4 ağ kimliklerinin ayrıldığı ve ayrılma yöntemi nedeniyle, büyük yönlendirme tablolarının Internet 'te bulunan yönlendiriciler tarafından saklanması gerekir. Bu yönlendiricilerin, Internet 'teki herhangi bir düğüme potansiyel olarak yönlendirilmiş paketleri iletmeniz için tüm yolları bilmeleri gerekir. IPv6, adresleri toplama özelliği sayesinde esnek adresleme sağlar ve yönlendirme tablolarının boyutunu büyük ölçüde azaltır. Bu yeni adres mimaride, Ara yönlendiriciler iletileri uygun şekilde iletmek için ağın yalnızca yerel bölümünü takip etmelidir.  
  
## <a name="neighbor-discovery"></a>Komşu bulma  

 Komşu bulma tarafından sunulan özelliklerden bazıları şunlardır:  
  
- Yönlendirici bulma. Bu, ana bilgisayarların yerel yönlendiricileri belirlemesine izin verir.  
  
- Adres çözümlemesi. Bu, düğümlerin ilgili bir sonraki atlama adresi (Adres Çözümleme Protokolü [ARP] için değiştirme) için bir bağlantı katmanı adresini çözümlemesine olanak sağlar.  
  
- Adres otomatik yapılandırması. Bu, ana bilgisayarların site yerel ve genel adreslerini otomatik olarak yapılandırmasına izin verir.  
  
 Komşu bulma şunları içeren IPv6 (Icmpv6) iletileri için Internet Denetim Iletisi protokolünü kullanır:  
  
- Yönlendirici tanıtımı. Bir yönlendirici tarafından sözde dönemsel olarak veya yönlendirici yanıtına yanıt olarak gönderilir. IPv6 yönlendiricileri, kullanılabilirlik, adres ön eklerini ve diğer parametreleri tanıtmak için yönlendirici tanıtımları kullanır.  
  
- Yönlendirici bağlantısı. Bağlantı üzerindeki yönlendiricilerin yönlendirici tanıtımı anında göndermesini istemek için bir ana bilgisayar tarafından gönderilir.  
  
- Komşu isteme. Adres çözümlemesi, yinelenen adres algılama veya bir komşunun hala erişilebilir olduğunu doğrulama için düğümler tarafından gönderilir.  
  
- Komşu tanıtım. Bir komşu bağlantısına yanıt vermek veya bağlantı katmanı adresindeki bir değişikliğin komşularını bilgilendirmek için düğümler tarafından gönderilir.  
  
- Meniz. Gönderen düğüm için belirli bir hedefe daha iyi bir sonraki atlama adresi göstermek üzere yönlendiriciler tarafından gönderilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İnternet Protokolü Sürüm 6](internet-protocol-version-6.md)
- [Yuvalar](sockets.md)
