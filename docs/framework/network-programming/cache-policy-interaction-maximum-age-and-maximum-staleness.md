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
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="bc983-102">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve en fazla eskime durumu</span><span class="sxs-lookup"><span data-stu-id="bc983-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="bc983-103">En yeni içerik istemci uygulamaya döndürülür sağlamaya yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulanması gereksinimleri etkileşimini her zaman en koruyucu önbellek ilkesi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="bc983-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="bc983-104">Bu konudaki tüm örneklerde, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynak için önbellek İlkesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bc983-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="bc983-105">Aşağıdaki örneklerde, en fazla eskime durumu değeri (`maxStale`) en uzun geçerlilik süresi ile birlikte kullanılır (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="bc983-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="bc983-106">Önbellek ilkesini ayarlarsa `maxAge` = 5 gün ve belirtmediği bir `maxStale` değeri, için according `maxAge` değeri, içeriği kullanılabilir Ocak 6 kadar.</span><span class="sxs-lookup"><span data-stu-id="bc983-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="bc983-107">Ancak, sunucunun yeniden doğrulanması gereksinimlerine göre içeriğin 4 Ocak süresi dolar.</span><span class="sxs-lookup"><span data-stu-id="bc983-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="bc983-108">İçerik sona erme tarihi (ER) daha pasif olduğundan bu önceliklidir `maxAge` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="bc983-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="bc983-109">Bu nedenle, içerik 4 Ocak süresi dolar ve onun Maksimum yaş ulaşılana olsa bile gerekiyor.%0.</span><span class="sxs-lookup"><span data-stu-id="bc983-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="bc983-110">Önbellek ilkesini ayarlarsa `maxAge` = 5 gün ve `maxStale` = 3 gün göre `maxAge` değeri, içeriği kullanılabilir Ocak 6 kadar.</span><span class="sxs-lookup"><span data-stu-id="bc983-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="bc983-111">Göre `maxStale` değeri, içeriği kullanılabilir Ocak 7 kadar.</span><span class="sxs-lookup"><span data-stu-id="bc983-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="bc983-112">Bu nedenle, içerik 6 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="bc983-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="bc983-113">Önbellek ilkesini ayarlarsa `maxAge` = 5 gün ve `maxStale` 1 gün = göre `maxAge` değeri, içeriği kullanılabilir Ocak 6 kadar.</span><span class="sxs-lookup"><span data-stu-id="bc983-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="bc983-114">Göre `maxStale` değeri, içeriği kullanılabilir 5 Ocak kadar.</span><span class="sxs-lookup"><span data-stu-id="bc983-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="bc983-115">Bu nedenle, içerik 5 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="bc983-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="bc983-116">En uzun geçerlilik süresi içerik sona erme tarihinden daha küçük olduğunda, her zaman daha pasif önbelleğe alma davranışını korunacağını ve en fazla eskime durumu değerinin hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="bc983-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="bc983-117">Aşağıdaki örnekler maksimum eskime durumu ayarı etkisini gösterir (`maxStale`) değeri en uzun geçerlilik süresi (`maxAge`) içerik süresi dolmadan önce ulaştı:</span><span class="sxs-lookup"><span data-stu-id="bc983-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="bc983-118">Önbellek ilkesini ayarlarsa `maxAge` = 1 gün ve için bir değer belirtmiyor `maxStale` değer, içeriğin yeniden doğrulanır 2 Ocak'ta rağmen süresi geçmemiş.</span><span class="sxs-lookup"><span data-stu-id="bc983-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="bc983-119">Önbellek ilkesini ayarlarsa `maxAge` = 1 gün ve `maxStale` = 3 gün içeriği daha pasif ilke ayarı zorunlu kılmak için 2 Ocak'ta yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="bc983-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="bc983-120">Önbellek ilkesini ayarlarsa `maxAge` = 1 gün ve `maxStale` = 1 gün, içeriğin 2 Ocak'ta yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="bc983-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc983-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc983-121">See Also</span></span>  
 [<span data-ttu-id="bc983-122">Ağ uygulamaları için önbellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="bc983-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="bc983-123">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="bc983-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="bc983-124">Konum temelli önbellek ilkeleri</span><span class="sxs-lookup"><span data-stu-id="bc983-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="bc983-125">Önbellek zaman tabanlı ilkeleri</span><span class="sxs-lookup"><span data-stu-id="bc983-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="bc983-126">Ağ uygulamalarında önbelleğe alma yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bc983-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="bc983-127">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik</span><span class="sxs-lookup"><span data-stu-id="bc983-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
