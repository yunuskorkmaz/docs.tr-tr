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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048812"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime
En son içeriğin istemci uygulamasına döndürüldüğünden emin olmak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesine neden olur. Bu konudaki tüm örneklerde, 1 Ocak tarihinde önbelleğe alınan ve 4 Ocak tarihinde sona erecek bir kaynağın önbellek ilkesi gösterilmektedir.  
  
 Aşağıdaki örneklerde, maksimum yaş (`maxAge`) ve en düşük yeniliği (`minFresh`) değerlerinin etkileşimini elde eden önbellek ilkesi gösterilmektedir.  
  
- Önbellek ilkesi = 2 gün `maxAge` ayarlaırsa ve `minFresh` belirtilmemişse, içerik 3 Ocak 'ta yeniden onaylanır.  
  
- Önbellek ilkesi `maxAge` öğesine göre = 2 gün ve `minFresh` = 1 gün ayarlanırsa, içerik 3 `maxAge`' e kadar yeni olur. Öğesine göre `minFresh`, içerik 3 ' e kadar yeni olur. Bu nedenle, içeriğin 3 Ocak tarihinde yeniden doğrulanması gerekir.  
  
- Önbellek ilkesi `maxAge` = 2 gün ve `minFresh` = 2 gün, öğesine göre ayarlanırsa, içerik `maxAge`3 ' e kadar yeni olur. İçeriğe göre `minFresh` 2 Ocak 'a kadar yeni bir değer vardır. Bu nedenle, içeriğin 2 Ocak 'ta yeniden doğrulanması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma](configuring-caching-in-network-applications.md)
- [Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
