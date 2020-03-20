---
title: Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: e21cfc28407ba67afdce8d72e5e52c12ab359059
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048834"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime
En yeni içeriğin istemci uygulamasına döndürülmesini sağlamak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en tutucu önbellek ilkesiyle sonuçlanır. Bu konudaki tüm örnekler, 1 Ocak'ta önbelleğe alınmış ve 4 Ocak'ta süresi dolan bir kaynağın önbellek ilkesini gösterir.  
  
 Aşağıdaki örneklerde, maksimum bayatlık`maxStale`değeri ( ) maksimum yaş`maxAge`( ):  
  
- Önbellek ilkesi = `maxAge` 5 gün belirler ve `maxStale` `maxAge` değere göre bir değer belirtmezse, içerik 6 Ocak'a kadar kullanılabilir. Ancak, sunucunun yeniden doğrulama gereksinimlerine göre, içeriğin süresi 4 Ocak'ta sona erer. İçerik son kullanma tarihi daha tutucu (daha erken) `maxAge` olduğundan, ilkeden önce gelir. Bu nedenle, içerik 4 Ocak'ta sona erer ve maksimum yaşına ulaşılamamasına rağmen yeniden geçersiz kılınması gerekir.  
  
- Önbellek ilkesi değerine göre `maxStale` = 5 gün ve `maxAge` = 3 gün belirlerse, `maxAge` içerik 6 Ocak'a kadar kullanılabilir. Değerine `maxStale` göre, içerik 7 Ocak'a kadar kullanılabilir. Bu nedenle, içerik 6 Ocak'ta yeniden geçersiz kılınır.  
  
- Önbellek ilkesi değerine göre `maxStale` = 5 gün ve `maxAge` = 1 gün belirlerse, `maxAge` içerik 6 Ocak'a kadar kullanılabilir. Değere `maxStale` göre, içerik 5 Ocak'a kadar kullanılabilir. Bu nedenle, içerik 5 Ocak'ta yeniden geçersiz kılınır.  
  
 Maksimum yaş içeriğin son kullanma tarihinden daha az olduğunda, daha konservatif önbelleğe alma davranışı her zaman geçerli olur ve maksimum bayatlık değerinin hiçbir etkisi yoktur. Aşağıdaki örnekler, içeriğin süresi dolmadan önce`maxStale`maksimum yaş (`maxAge`) erişildiğinde maksimum bayatlık ( ) değerini ayarlamanın etkisini göstermektedir:  
  
- Önbellek ilkesi = `maxAge` 1 gün belirler ve değer `maxStale` için bir değer belirtmezse, süresi dolmamış olsa bile içerik 2 Ocak'ta yeniden geçersiz kılınır.  
  
- Önbellek ilkesi = `maxAge` 1 gün `maxStale` ve = 3 gün belirlerse, içerik daha tutucu ilke ayarını zorlamak için 2 Ocak'ta yeniden geçersiz kılınır.  
  
- Önbellek ilkesi = `maxAge` 1 gün `maxStale` ve = 1 gün belirlerse, içerik 2 Ocak'ta yeniden geçersiz kılınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
