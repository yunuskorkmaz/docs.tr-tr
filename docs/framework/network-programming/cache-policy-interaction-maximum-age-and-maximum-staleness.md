---
title: Önbellek İlkesi etkileşimi — yaş üst sınırı ve en fazla eskime
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c512f03cd3c0cfc4463e54538f12898fbbf45f7e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583767"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="cf9be-102">Önbellek İlkesi etkileşimi — yaş üst sınırı ve en fazla eskime</span><span class="sxs-lookup"><span data-stu-id="cf9be-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="cf9be-103">İstemci uygulamayı çevrimiçiyken içeriği getirildiğinden emin olun yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulama gereksinimleri etkileşimi her zaman en koruyucu önbellek İlkesi'nde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cf9be-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="cf9be-104">Bu konu başlığı altındaki tüm örnekler, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynağın önbellek ilkesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf9be-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="cf9be-105">Aşağıdaki örneklerde, en fazla eskime değeri (`maxStale`) en uzun bir geçerlilik süresi ile birlikte kullanılır (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="cf9be-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="cf9be-106">Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve belirttiğinde bir `maxStale` değeri, için uygun `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="cf9be-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="cf9be-107">Ancak, sunucunun yeniden doğrulama gereksinimlerine göre içeriği 4 Ocak süresi dolar.</span><span class="sxs-lookup"><span data-stu-id="cf9be-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="cf9be-108">İçerik sona erme tarihi (ER) daha pasif olduğundan, öncelikli `maxAge` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="cf9be-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="cf9be-109">Bu nedenle, içerik 4 Ocak süresi dolar ve rağmen en yüksek yaşı ulaşılmadı yeniden doğrulanır gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf9be-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="cf9be-110">Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve `maxStale` = 3 gün göre `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="cf9be-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="cf9be-111">Şunlara göre `maxStale` içeriği değerdir kullanılabilir Ocak 7 kadar.</span><span class="sxs-lookup"><span data-stu-id="cf9be-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="cf9be-112">Bu nedenle, içerik 6 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="cf9be-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="cf9be-113">Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve `maxStale` = 1 gün göre `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="cf9be-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="cf9be-114">Şunlara göre `maxStale` içeriği değerdir kullanılabilir 5 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="cf9be-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="cf9be-115">Bu nedenle, içerik 5 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="cf9be-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="cf9be-116">En uzun geçerlilik süresi içerik sona erme tarihinden daha az olduğunda, her zaman daha pasif önbelleğe alma davranışını korunacağını ve en fazla eskime değeri etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="cf9be-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="cf9be-117">Aşağıdaki örnekler en fazla eskime ayarı etkisini gösterir (`maxStale`) değeri yaş üst sınırını (`maxAge`) içerik süresi dolmadan önce ulaştı:</span><span class="sxs-lookup"><span data-stu-id="cf9be-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="cf9be-118">Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve için bir değer belirtmiyor `maxStale` değeri, içeriği yeniden doğrulanır 2 Ocak rağmen süresi geçmemiş.</span><span class="sxs-lookup"><span data-stu-id="cf9be-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="cf9be-119">Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve `maxStale` = 3 gün içeriği daha pasif ilke ayarı zorunlu tutmak için 2 Ocak'ta yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="cf9be-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="cf9be-120">Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve `maxStale` = 1 gün, içeriğin 2 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="cf9be-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9be-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf9be-121">See Also</span></span>  
 [<span data-ttu-id="cf9be-122">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="cf9be-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="cf9be-123">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="cf9be-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="cf9be-124">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="cf9be-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="cf9be-125">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="cf9be-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="cf9be-126">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cf9be-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="cf9be-127">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="cf9be-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
