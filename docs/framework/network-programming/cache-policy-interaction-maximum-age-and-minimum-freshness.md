---
title: Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime
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
ms.openlocfilehash: 2ec958cc035ac62086cdd3e2844811accc181d47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048812"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime
En yeni içeriğin istemci uygulamasına döndürülmesini sağlamak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en tutucu önbellek ilkesiyle sonuçlanır. Bu konudaki tüm örnekler, 1 Ocak'ta önbelleğe alınmış ve 4 Ocak'ta süresi dolan bir kaynağın önbellek ilkesini gösterir.  
  
 Aşağıdaki örnekler, maksimum yaş ( ) ve minimum tazelik (`maxAge`)`minFresh`değerlerinin etkileşiminden kaynaklanan önbellek ilkesini göstermektedir.  
  
- Önbellek ilkesi = `maxAge` 2 gün `minFresh` belirler ve belirtilmemişse, içerik 3 Ocak'ta yeniden geçersiz kılınır.  
  
- Önbellek ilkesi = `maxAge` 2 gün `minFresh` ve = 1 `maxAge`gün olarak ayarlanırsa, içeriği 3 Ocak'a kadar tazedir. Göre `minFresh`, içerik 3 Ocak'a kadar taze. Bu nedenle, içeriğin 3 Ocak'ta yeniden onaylanması gerekir.  
  
- Önbellek ilkesi = `maxAge` 2 gün `minFresh` ve = 2 `maxAge`gün olarak ayarlanırsa, içeriği 3 Ocak'a kadar tazedir. İçeriä `minFresh` e günü2 Ocak' a kadar taze. Bu nedenle, içeriğin 2 Ocak'ta yeniden onaylanması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
