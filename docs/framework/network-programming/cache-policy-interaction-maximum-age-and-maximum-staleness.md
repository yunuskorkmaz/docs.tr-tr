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
ms.openlocfilehash: bdfa608b5169755b2b4daaaa26e562308ae2be01
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250612"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="aa076-102">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="aa076-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>

<span data-ttu-id="aa076-103">En son içeriğin istemci uygulamasına döndürüldüğünden emin olmak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="aa076-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="aa076-104">Bu konudaki tüm örneklerde, 1 Ocak tarihinde önbelleğe alınan ve 4 Ocak tarihinde sona erecek bir kaynağın önbellek ilkesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa076-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="aa076-105">Aşağıdaki örneklerde, en yüksek stalet değeri ( `maxStale` ) en fazla Age () ile birlikte kullanılır `maxAge` :</span><span class="sxs-lookup"><span data-stu-id="aa076-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="aa076-106">Önbellek ilkesi `maxAge` = 5 gün ayarlar ve `maxStale` değere göre değer belirtmezse `maxAge` , içerik 6 Ocak 'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa076-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="aa076-107">Ancak, sunucunun yeniden doğrulama gereksinimlerine göre, içerik 4 Ocak tarihinde sona erer.</span><span class="sxs-lookup"><span data-stu-id="aa076-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="aa076-108">İçerik sona erme tarihi daha pasif (daha önce) olduğundan, ilkeye göre önceliklidir `maxAge` .</span><span class="sxs-lookup"><span data-stu-id="aa076-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="aa076-109">Bu nedenle, içerik 4 Ocak tarihinde sona erer ve en yüksek yaşına ulaşılmasa bile yeniden doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aa076-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="aa076-110">Önbellek ilkesi `maxAge` değere göre = 5 gün ve `maxStale` = 3 gün ayarladıysanız `maxAge` , içerik 6 Ocak 'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa076-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="aa076-111">`maxStale`Değere göre, içerik 7 Ocak tarihine kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa076-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="aa076-112">Bu nedenle, içerik 6 Ocak 'ta yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="aa076-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="aa076-113">Önbellek ilkesi `maxAge` değere göre = 5 gün ve `maxStale` = 1 gün ayarladıysanız `maxAge` , içerik 6 Ocak 'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa076-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="aa076-114">`maxStale`Değere göre, içerik 5 Ocak 'a kadar kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa076-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="aa076-115">Bu nedenle, içerik 5 Ocak 'ta yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="aa076-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="aa076-116">Maksimum yaş, içerik sona erme tarihinden daha az olduğunda, daha fazla koruyucu önbelleğe alma davranışı her zaman korunur ve en yüksek stalet değeri bir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="aa076-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="aa076-117">Aşağıdaki örneklerde, `maxStale` en yüksek yaş () değerinin, `maxAge` içeriğin süresi dolmadan önce ne kadar dolacağını gösteren en yüksek bir stalet () değeri ayarlamanın etkisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aa076-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="aa076-118">Önbellek ilkesi `maxAge` = 1 gün ayarlıyor ve değer için değer belirtmezse `maxStale` , süresi dolmasa bile 2 Ocak 'ta içerik yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="aa076-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="aa076-119">Önbellek ilkesi `maxAge` = 1 gün ve `maxStale` = 3 gün ayarlaırsa, daha koruyucu ilke ayarını zorlamak için Içerik 2 Ocak 'ta yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="aa076-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="aa076-120">Önbellek ilkesi `maxAge` = 1 gün ve `maxStale` = 1 gün ise, Içerik 2 Ocak 'ta yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="aa076-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa076-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa076-121">See also</span></span>

- [<span data-ttu-id="aa076-122">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="aa076-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="aa076-123">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="aa076-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="aa076-124">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="aa076-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="aa076-125">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="aa076-125">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="aa076-126">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aa076-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="aa076-127">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="aa076-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
