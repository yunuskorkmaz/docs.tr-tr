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
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="cd053-102">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="cd053-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="cd053-103">En yeni içeriğin istemci uygulamasına döndürülmesini sağlamak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en tutucu önbellek ilkesiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cd053-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="cd053-104">Bu konudaki tüm örnekler, 1 Ocak'ta önbelleğe alınmış ve 4 Ocak'ta süresi dolan bir kaynağın önbellek ilkesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd053-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="cd053-105">Aşağıdaki örneklerde, maksimum bayatlık`maxStale`değeri ( ) maksimum yaş`maxAge`( ):</span><span class="sxs-lookup"><span data-stu-id="cd053-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="cd053-106">Önbellek ilkesi = `maxAge` 5 gün belirler ve `maxStale` `maxAge` değere göre bir değer belirtmezse, içerik 6 Ocak'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd053-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="cd053-107">Ancak, sunucunun yeniden doğrulama gereksinimlerine göre, içeriğin süresi 4 Ocak'ta sona erer.</span><span class="sxs-lookup"><span data-stu-id="cd053-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="cd053-108">İçerik son kullanma tarihi daha tutucu (daha erken) `maxAge` olduğundan, ilkeden önce gelir.</span><span class="sxs-lookup"><span data-stu-id="cd053-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="cd053-109">Bu nedenle, içerik 4 Ocak'ta sona erer ve maksimum yaşına ulaşılamamasına rağmen yeniden geçersiz kılınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cd053-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="cd053-110">Önbellek ilkesi değerine göre `maxStale` = 5 gün ve `maxAge` = 3 gün belirlerse, `maxAge` içerik 6 Ocak'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd053-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="cd053-111">Değerine `maxStale` göre, içerik 7 Ocak'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd053-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="cd053-112">Bu nedenle, içerik 6 Ocak'ta yeniden geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cd053-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="cd053-113">Önbellek ilkesi değerine göre `maxStale` = 5 gün ve `maxAge` = 1 gün belirlerse, `maxAge` içerik 6 Ocak'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd053-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="cd053-114">Değere `maxStale` göre, içerik 5 Ocak'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd053-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="cd053-115">Bu nedenle, içerik 5 Ocak'ta yeniden geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cd053-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="cd053-116">Maksimum yaş içeriğin son kullanma tarihinden daha az olduğunda, daha konservatif önbelleğe alma davranışı her zaman geçerli olur ve maksimum bayatlık değerinin hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cd053-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="cd053-117">Aşağıdaki örnekler, içeriğin süresi dolmadan önce`maxStale`maksimum yaş (`maxAge`) erişildiğinde maksimum bayatlık ( ) değerini ayarlamanın etkisini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cd053-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="cd053-118">Önbellek ilkesi = `maxAge` 1 gün belirler ve değer `maxStale` için bir değer belirtmezse, süresi dolmamış olsa bile içerik 2 Ocak'ta yeniden geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cd053-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="cd053-119">Önbellek ilkesi = `maxAge` 1 gün `maxStale` ve = 3 gün belirlerse, içerik daha tutucu ilke ayarını zorlamak için 2 Ocak'ta yeniden geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cd053-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="cd053-120">Önbellek ilkesi = `maxAge` 1 gün `maxStale` ve = 1 gün belirlerse, içerik 2 Ocak'ta yeniden geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cd053-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd053-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd053-121">See also</span></span>

- [<span data-ttu-id="cd053-122">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="cd053-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="cd053-123">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="cd053-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="cd053-124">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="cd053-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="cd053-125">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="cd053-125">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="cd053-126">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cd053-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="cd053-127">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="cd053-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
