---
title: "Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve en fazla eskime durumu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: baec376501feb70e4a9ceb3f33ac66fa76b91ac1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve en fazla eskime durumu
En yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulanması gereksinimleri etkileşimini her zaman en koruyucu önbellek ilkesi ortaya çıkarır. Bu konudaki tüm örneklerde, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynak için önbellek İlkesi gösterilmektedir.  
  
 Aşağıdaki örneklerde, en fazla eskime durumu değeri (`maxStale`) en uzun geçerlilik süresi ile birlikte kullanılır (`maxAge`):  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 5 gün ve belirtmediği bir `maxStale` değeri, için according `maxAge` değeri, içeriği kullanılabilir Ocak 6 kadar. Ancak, sunucunun yeniden doğrulanması gereksinimlerine göre içeriğin 4 Ocak süresi dolar. İçerik sona erme tarihi (ER) daha pasif olduğundan bu önceliklidir `maxAge` ilkesi. Bu nedenle, içerik 4 Ocak süresi dolar ve onun Maksimum yaş ulaşılana olsa bile gerekiyor.%0.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 5 gün ve `maxStale` = 3 gün göre `maxAge` değeri, içeriği kullanılabilir Ocak 6 kadar. Göre `maxStale` değeri, içeriği kullanılabilir Ocak 7 kadar. Bu nedenle, içerik 6 Ocak yeniden doğrulanır.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 5 gün ve `maxStale` 1 gün = göre `maxAge` değeri, içeriği kullanılabilir Ocak 6 kadar. Göre `maxStale` değeri, içeriği kullanılabilir 5 Ocak kadar. Bu nedenle, içerik 5 Ocak yeniden doğrulanır.  
  
 En uzun geçerlilik süresi içerik sona erme tarihinden daha küçük olduğunda, her zaman daha pasif önbelleğe alma davranışını korunacağını ve en fazla eskime durumu değerinin hiçbir etkisi olmaz. Aşağıdaki örnekler maksimum eskime durumu ayarı etkisini gösterir (`maxStale`) değeri en uzun geçerlilik süresi (`maxAge`) içerik süresi dolmadan önce ulaştı:  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 1 gün ve için bir değer belirtmiyor `maxStale` değer, içeriğin yeniden doğrulanır 2 Ocak'ta rağmen süresi geçmemiş.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 1 gün ve `maxStale` = 3 gün içeriği daha pasif ilke ayarı zorunlu kılmak için 2 Ocak'ta yeniden doğrulanır.  
  
-   Önbellek ilkesini ayarlarsa `maxAge` = 1 gün ve `maxStale` = 1 gün, içeriğin 2 Ocak'ta yeniden doğrulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ uygulamaları için önbellek yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum temelli önbellek ilkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Önbellek zaman tabanlı ilkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Ağ uygulamalarında önbelleğe alma yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
