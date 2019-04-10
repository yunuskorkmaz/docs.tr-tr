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
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="5fb90-102">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="5fb90-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>
<span data-ttu-id="5fb90-103">İstemci uygulamayı çevrimiçiyken içeriği getirildiğinden emin olun yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulama gereksinimleri etkileşimi her zaman en koruyucu önbellek İlkesi'nde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="5fb90-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="5fb90-104">Bu konu başlığı altındaki tüm örnekler, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynağın önbellek ilkesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fb90-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="5fb90-105">Aşağıdaki örneklerde, en fazla eskime değeri (`maxStale`) en uzun bir geçerlilik süresi ile birlikte kullanılır (`maxAge`):</span><span class="sxs-lookup"><span data-stu-id="5fb90-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
-   <span data-ttu-id="5fb90-106">Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve belirttiğinde bir `maxStale` değeri, için uygun `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="5fb90-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="5fb90-107">Ancak, sunucunun yeniden doğrulama gereksinimlerine göre içeriği 4 Ocak süresi dolar.</span><span class="sxs-lookup"><span data-stu-id="5fb90-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="5fb90-108">İçerik sona erme tarihi (ER) daha pasif olduğundan, öncelikli `maxAge` ilkesi.</span><span class="sxs-lookup"><span data-stu-id="5fb90-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="5fb90-109">Bu nedenle, içerik 4 Ocak süresi dolar ve rağmen en yüksek yaşı ulaşılmadı yeniden doğrulanır gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fb90-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
-   <span data-ttu-id="5fb90-110">Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve `maxStale` = 3 gün göre `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="5fb90-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="5fb90-111">Şunlara göre `maxStale` içeriği değerdir kullanılabilir Ocak 7 kadar.</span><span class="sxs-lookup"><span data-stu-id="5fb90-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="5fb90-112">Bu nedenle, içerik 6 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5fb90-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
-   <span data-ttu-id="5fb90-113">Önbellek İlkesi ayarlarsa `maxAge` = 5 gün ve `maxStale` = 1 gün göre `maxAge` içeriği değerdir kullanılabilir 6 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="5fb90-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="5fb90-114">Şunlara göre `maxStale` içeriği değerdir kullanılabilir 5 Ocak tarihine kadar.</span><span class="sxs-lookup"><span data-stu-id="5fb90-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="5fb90-115">Bu nedenle, içerik 5 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5fb90-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="5fb90-116">En uzun geçerlilik süresi içerik sona erme tarihinden daha az olduğunda, her zaman daha pasif önbelleğe alma davranışını korunacağını ve en fazla eskime değeri etkisizdir.</span><span class="sxs-lookup"><span data-stu-id="5fb90-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="5fb90-117">Aşağıdaki örnekler en fazla eskime ayarı etkisini gösterir (`maxStale`) değeri yaş üst sınırını (`maxAge`) içerik süresi dolmadan önce ulaştı:</span><span class="sxs-lookup"><span data-stu-id="5fb90-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
-   <span data-ttu-id="5fb90-118">Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve için bir değer belirtmiyor `maxStale` değeri, içeriği yeniden doğrulanır 2 Ocak rağmen süresi geçmemiş.</span><span class="sxs-lookup"><span data-stu-id="5fb90-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
-   <span data-ttu-id="5fb90-119">Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve `maxStale` = 3 gün içeriği daha pasif ilke ayarı zorunlu tutmak için 2 Ocak'ta yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5fb90-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
-   <span data-ttu-id="5fb90-120">Önbellek İlkesi ayarlarsa `maxAge` = 1 gün ve `maxStale` = 1 gün, içeriğin 2 Ocak yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="5fb90-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb90-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fb90-121">See also</span></span>

- [<span data-ttu-id="5fb90-122">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="5fb90-122">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="5fb90-123">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="5fb90-123">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="5fb90-124">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="5fb90-124">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="5fb90-125">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="5fb90-125">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="5fb90-126">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5fb90-126">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [<span data-ttu-id="5fb90-127">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="5fb90-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)
