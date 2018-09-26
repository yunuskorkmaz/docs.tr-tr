---
title: Önbellek İlkesi etkileşimi — yaş üst sınırı ve en az eskime
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
ms.openlocfilehash: a35bdeaf0fc6cf513363f3d990167f342a496c76
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193466"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Önbellek İlkesi etkileşimi — yaş üst sınırı ve en az eskime
İstemci uygulamayı çevrimiçiyken içeriği getirildiğinden emin olun yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulama gereksinimleri etkileşimi her zaman en koruyucu önbellek İlkesi'nde sonuçlanır. Bu konu başlığı altındaki tüm örnekler, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynağın önbellek ilkesini gösterir.  
  
 Aşağıdaki örnekler yaş üst sınırını müdahalesini sonuçları önbellek İlkesi gösterir (`maxAge`) ve en az eskime (`minFresh`) değerleri.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 2 gün ve `minFresh` belirtilmemişse, içeriği yeniden doğrulanır 3 Ocak'ta.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 2 gün ve `minFresh` = 1 gün göre `maxAge`, içeriği 3 Ocak tarihine kadar yeni. Şunlara göre `minFresh`, içeriği 3 Ocak tarihine kadar yeni. Bu nedenle, içerik 3 Ocak'ta yeniden doğrulanır gerekir.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 2 gün ve `minFresh` = 2 gün göre `maxAge`, içeriği 3 Ocak tarihine kadar yeni. Şunlara göre `minFresh` 2 Ocak tarihine kadar yeni içeriktir. Bu nedenle, içeriğin 2 Ocak yeniden doğrulanır gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
