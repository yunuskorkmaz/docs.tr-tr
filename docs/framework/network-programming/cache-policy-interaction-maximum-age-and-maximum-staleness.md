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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048834"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime
En son içeriğin istemci uygulamasına döndürüldüğünden emin olmak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesine neden olur. Bu konudaki tüm örneklerde, 1 Ocak tarihinde önbelleğe alınan ve 4 Ocak tarihinde sona erecek bir kaynağın önbellek ilkesi gösterilmektedir.  
  
 Aşağıdaki örneklerde, en yüksek stalet değeri (`maxStale`) en fazla Age (`maxAge`) ile birlikte kullanılır:  
  
- Önbellek ilkesi = 5 gün `maxAge` ayarlar ve `maxAge` değere göre `maxStale` değer belirtmezse, içerik 6 Ocak 'a kadar kullanılabilir. Ancak, sunucunun yeniden doğrulama gereksinimlerine göre, içerik 4 Ocak tarihinde sona erer. İçerik sona erme tarihi daha pasif (daha önce) olduğundan, `maxAge` ilkeye göre önceliklidir. Bu nedenle, içerik 4 Ocak tarihinde sona erer ve en yüksek yaşına ulaşılmasa bile yeniden doğrulanması gerekir.  
  
- Önbellek ilkesi `maxAge` değere göre = `maxAge` 5 gün ve `maxStale` = 3 gün ayarladıysanız, içerik 6 Ocak 'a kadar kullanılabilir. `maxStale` Değere göre, içerik 7 Ocak tarihine kadar kullanılabilir. Bu nedenle, içerik 6 Ocak 'ta yeniden onaylanır.  
  
- Önbellek ilkesi `maxAge` değere göre = `maxAge` 5 gün ve `maxStale` = 1 gün ayarladıysanız, içerik 6 Ocak 'a kadar kullanılabilir. `maxStale` Değere göre, içerik 5 Ocak 'a kadar kullanılabilir. Bu nedenle, içerik 5 Ocak 'ta yeniden onaylanır.  
  
 Maksimum yaş, içerik sona erme tarihinden daha az olduğunda, daha fazla koruyucu önbelleğe alma davranışı her zaman korunur ve en yüksek stalet değeri bir etkiye sahip değildir. Aşağıdaki örneklerde, en yüksek yaş (`maxStale``maxAge`) değerinin, içeriğin süresi dolmadan önce ne kadar dolacağını gösteren en yüksek bir stalet () değeri ayarlamanın etkisi gösterilmektedir:  
  
- Önbellek ilkesi = 1 gün `maxAge` ayarlıyor ve değer için `maxStale` değer belirtmezse, süresi dolmasa bile 2 Ocak 'ta içerik yeniden onaylanır.  
  
- Önbellek ilkesi = 1 gün `maxAge` ve `maxStale` = 3 gün ayarlaırsa, daha koruyucu ilke ayarını zorlamak için içerik 2 Ocak 'ta yeniden onaylanır.  
  
- Önbellek ilkesi `maxAge` = 1 gün ve `maxStale` = 1 gün ise, içerik 2 Ocak 'ta yeniden onaylanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
