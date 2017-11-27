---
title: "Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75729fc92c6a4bfa0f5ad73b8bbd4b28456f21e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="8023c-102">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik</span><span class="sxs-lookup"><span data-stu-id="8023c-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="8023c-103">En yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulanması gereksinimleri etkileşimini her zaman en koruyucu önbellek ilkesi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8023c-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="8023c-104">Bu konudaki tüm örneklerde, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynak için önbellek İlkesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8023c-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="8023c-105">Aşağıdaki örnekler en uzun geçerlilik süresi müdahalesini sonuçları önbellek İlkesi gösterir (`maxAge`) ve en düşük yenilik (`minFresh`) değerleri.</span><span class="sxs-lookup"><span data-stu-id="8023c-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="8023c-106">Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` belirtilmezse, içeriği yeniden doğrulanır 3 Ocak'ta.</span><span class="sxs-lookup"><span data-stu-id="8023c-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="8023c-107">Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` 1 gün = göre `maxAge`, 3 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="8023c-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="8023c-108">Göre `minFresh`, 3 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="8023c-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="8023c-109">Bu nedenle, içerik 3 Ocak'ta gerekiyor.%0.</span><span class="sxs-lookup"><span data-stu-id="8023c-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="8023c-110">Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` = 2 gün göre `maxAge`, 3 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="8023c-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="8023c-111">Göre `minFresh` 2 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="8023c-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="8023c-112">Bu nedenle, içeriğin 2 Ocak'ta gerekiyor.%0.</span><span class="sxs-lookup"><span data-stu-id="8023c-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8023c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8023c-113">See Also</span></span>  
 [<span data-ttu-id="8023c-114">Ağ uygulamaları için önbellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="8023c-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="8023c-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="8023c-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="8023c-116">Konum temelli önbellek ilkeleri</span><span class="sxs-lookup"><span data-stu-id="8023c-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="8023c-117">Önbellek zaman tabanlı ilkeleri</span><span class="sxs-lookup"><span data-stu-id="8023c-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="8023c-118">Ağ uygulamalarında önbelleğe alma yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8023c-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="8023c-119">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve en fazla eskime durumu</span><span class="sxs-lookup"><span data-stu-id="8023c-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
