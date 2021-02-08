---
description: 'Daha fazla bilgi edinin: önbellek Ilkesi etkileşimi — maksimum yaş ve maksimum Eskime durumu'
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
ms.openlocfilehash: 909a7203d4c9813c90dc0dea9bae7f8a1f7336cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791666"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime

En son içeriğin istemci uygulamasına döndürüldüğünden emin olmak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesine neden olur. Bu konudaki tüm örneklerde, 1 Ocak tarihinde önbelleğe alınan ve 4 Ocak tarihinde sona erecek bir kaynağın önbellek ilkesi gösterilmektedir.  
  
 Aşağıdaki örneklerde, en yüksek stalet değeri ( `maxStale` ) en fazla Age () ile birlikte kullanılır `maxAge` :  
  
- Önbellek ilkesi `maxAge` = 5 gün ayarlar ve `maxStale` değere göre değer belirtmezse `maxAge` , içerik 6 Ocak 'a kadar kullanılabilir. Ancak, sunucunun yeniden doğrulama gereksinimlerine göre, içerik 4 Ocak tarihinde sona erer. İçerik sona erme tarihi daha pasif (daha önce) olduğundan, ilkeye göre önceliklidir `maxAge` . Bu nedenle, içerik 4 Ocak tarihinde sona erer ve en yüksek yaşına ulaşılmasa bile yeniden doğrulanması gerekir.  
  
- Önbellek ilkesi `maxAge` değere göre = 5 gün ve `maxStale` = 3 gün ayarladıysanız `maxAge` , içerik 6 Ocak 'a kadar kullanılabilir. `maxStale`Değere göre, içerik 7 Ocak tarihine kadar kullanılabilir. Bu nedenle, içerik 6 Ocak 'ta yeniden onaylanır.  
  
- Önbellek ilkesi `maxAge` değere göre = 5 gün ve `maxStale` = 1 gün ayarladıysanız `maxAge` , içerik 6 Ocak 'a kadar kullanılabilir. `maxStale`Değere göre, içerik 5 Ocak 'a kadar kullanılabilir. Bu nedenle, içerik 5 Ocak 'ta yeniden onaylanır.  
  
 Maksimum yaş, içerik sona erme tarihinden daha az olduğunda, daha fazla koruyucu önbelleğe alma davranışı her zaman korunur ve en yüksek stalet değeri bir etkiye sahip değildir. Aşağıdaki örneklerde, `maxStale` en yüksek yaş () değerinin, `maxAge` içeriğin süresi dolmadan önce ne kadar dolacağını gösteren en yüksek bir stalet () değeri ayarlamanın etkisi gösterilmektedir:  
  
- Önbellek ilkesi `maxAge` = 1 gün ayarlıyor ve değer için değer belirtmezse `maxStale` , süresi dolmasa bile 2 Ocak 'ta içerik yeniden onaylanır.  
  
- Önbellek ilkesi `maxAge` = 1 gün ve `maxStale` = 3 gün ayarlaırsa, daha koruyucu ilke ayarını zorlamak için Içerik 2 Ocak 'ta yeniden onaylanır.  
  
- Önbellek ilkesi `maxAge` = 1 gün ve `maxStale` = 1 gün ise, Içerik 2 Ocak 'ta yeniden onaylanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
