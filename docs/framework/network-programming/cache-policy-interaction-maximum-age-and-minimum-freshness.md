---
title: Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d88ef1e736a16dddf156a1bc0e42f06d128d2c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik
En yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulanması gereksinimleri etkileşimini her zaman en koruyucu önbellek ilkesi ortaya çıkarır. Bu konudaki tüm örneklerde, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynak için önbellek İlkesi gösterilmektedir.  
  
 Aşağıdaki örnekler en uzun geçerlilik süresi müdahalesini sonuçları önbellek İlkesi gösterir (`maxAge`) ve en düşük yenilik (`minFresh`) değerleri.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` belirtilmezse, içeriği yeniden doğrulanır 3 Ocak'ta.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` 1 gün = göre `maxAge`, 3 Ocak kadar yeni içeriktir. Göre `minFresh`, 3 Ocak kadar yeni içeriktir. Bu nedenle, içerik 3 Ocak'ta gerekiyor.%0.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` = 2 gün göre `maxAge`, 3 Ocak kadar yeni içeriktir. Göre `minFresh` 2 Ocak kadar yeni içeriktir. Bu nedenle, içeriğin 2 Ocak'ta gerekiyor.%0.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
