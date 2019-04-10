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
ms.openlocfilehash: 18a73a46bc4b463d0a5f5690afe6d1109e06171c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207142"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime
İstemci uygulamayı çevrimiçiyken içeriği getirildiğinden emin olun yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulama gereksinimleri etkileşimi her zaman en koruyucu önbellek İlkesi'nde sonuçlanır. Bu konu başlığı altındaki tüm örnekler, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynağın önbellek ilkesini gösterir.  
  
 Aşağıdaki örneklerde, en fazla eskime değeri (`maxStale`) en uzun bir geçerlilik süresi ile birlikte kullanılır (`maxAge`):  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve belirttiğinde bir `maxStale` değeri, için uygun `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar. Ancak, sunucunun yeniden doğrulama gereksinimlerine göre içeriği 4 Ocak süresi dolar. İçerik sona erme tarihi (ER) daha pasif olduğundan, öncelikli `maxAge` ilkesi. Bu nedenle, içerik 4 Ocak süresi dolar ve rağmen en yüksek yaşı ulaşılmadı yeniden doğrulanır gerekir.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve `maxStale` = 3 gün göre `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar. Şunlara göre `maxStale` içeriği değerdir kullanılabilir Ocak 7 kadar. Bu nedenle, içerik 6 Ocak yeniden doğrulanır.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve `maxStale` = 1 gün göre `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar. Şunlara göre `maxStale` içeriği değerdir kullanılabilir 5 Ocak tarihine kadar. Bu nedenle, içerik 5 Ocak yeniden doğrulanır.  
  
 En uzun geçerlilik süresi içerik sona erme tarihinden daha az olduğunda, her zaman daha pasif önbelleğe alma davranışını korunacağını ve en fazla eskime değeri etkisizdir. Aşağıdaki örnekler en fazla eskime ayarı etkisini gösterir (`maxStale`) değeri yaş üst sınırını (`maxAge`) içerik süresi dolmadan önce ulaştı:  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve için bir değer belirtmiyor `maxStale` değeri, içeriği yeniden doğrulanır 2 Ocak rağmen süresi geçmemiş.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve `maxStale` = 3 gün içeriği daha pasif ilke ayarı zorunlu tutmak için 2 Ocak'ta yeniden doğrulanır.  
  
-   Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve `maxStale` = 1 gün, içeriğin 2 Ocak yeniden doğrulanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
