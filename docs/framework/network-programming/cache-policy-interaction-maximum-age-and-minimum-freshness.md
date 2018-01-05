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
ms.workload: dotnet
ms.openlocfilehash: 689b8b2d921731ecab2be2a1aa3dee5d1928e8cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="48a58-102">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik</span><span class="sxs-lookup"><span data-stu-id="48a58-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="48a58-103">En yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulanması gereksinimleri etkileşimini her zaman en koruyucu önbellek ilkesi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="48a58-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="48a58-104">Bu konudaki tüm örneklerde, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynak için önbellek İlkesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48a58-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="48a58-105">Aşağıdaki örnekler en uzun geçerlilik süresi müdahalesini sonuçları önbellek İlkesi gösterir (`maxAge`) ve en düşük yenilik (`minFresh`) değerleri.</span><span class="sxs-lookup"><span data-stu-id="48a58-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="48a58-106">Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` belirtilmezse, içeriği yeniden doğrulanır 3 Ocak'ta.</span><span class="sxs-lookup"><span data-stu-id="48a58-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="48a58-107">Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` 1 gün = göre `maxAge`, 3 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="48a58-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="48a58-108">Göre `minFresh`, 3 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="48a58-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="48a58-109">Bu nedenle, içerik 3 Ocak'ta gerekiyor.%0.</span><span class="sxs-lookup"><span data-stu-id="48a58-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="48a58-110">Önbellek ilkesini ayarlarsa `maxAge` = 2 gün ve `minFresh` = 2 gün göre `maxAge`, 3 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="48a58-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="48a58-111">Göre `minFresh` 2 Ocak kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="48a58-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="48a58-112">Bu nedenle, içeriğin 2 Ocak'ta gerekiyor.%0.</span><span class="sxs-lookup"><span data-stu-id="48a58-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a58-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48a58-113">See Also</span></span>  
 [<span data-ttu-id="48a58-114">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="48a58-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="48a58-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="48a58-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="48a58-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="48a58-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="48a58-117">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="48a58-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="48a58-118">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48a58-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="48a58-119">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="48a58-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
