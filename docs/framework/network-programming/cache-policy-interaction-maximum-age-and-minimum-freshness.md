---
title: Önbellek İlkesi etkileşimi — yaş üst sınırı ve en az eskime
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
ms.openlocfilehash: eab50c308441ce73e994313d009588559302671e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199324"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="29337-102">Önbellek İlkesi etkileşimi — yaş üst sınırı ve en az eskime</span><span class="sxs-lookup"><span data-stu-id="29337-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="29337-103">İstemci uygulamayı çevrimiçiyken içeriği getirildiğinden emin olun yardımcı olmak için istemci önbellek İlkesi ve sunucu yeniden doğrulama gereksinimleri etkileşimi her zaman en koruyucu önbellek İlkesi'nde sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="29337-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="29337-104">Bu konu başlığı altındaki tüm örnekler, 1 Ocak önbelleğe alınır ve 4 Ocak süresi bir kaynağın önbellek ilkesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="29337-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="29337-105">Aşağıdaki örnekler yaş üst sınırını müdahalesini sonuçları önbellek İlkesi gösterir (`maxAge`) ve en az eskime (`minFresh`) değerleri.</span><span class="sxs-lookup"><span data-stu-id="29337-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
-   <span data-ttu-id="29337-106">Önbellek İlkesi ayarlarsa `maxAge` = 2 gün ve `minFresh` belirtilmemişse, içeriği yeniden doğrulanır 3 Ocak'ta.</span><span class="sxs-lookup"><span data-stu-id="29337-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="29337-107">Önbellek İlkesi ayarlarsa `maxAge` = 2 gün ve `minFresh` = 1 gün göre `maxAge`, içeriği 3 Ocak tarihine kadar yeni.</span><span class="sxs-lookup"><span data-stu-id="29337-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="29337-108">Şunlara göre `minFresh`, içeriği 3 Ocak tarihine kadar yeni.</span><span class="sxs-lookup"><span data-stu-id="29337-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="29337-109">Bu nedenle, içerik 3 Ocak'ta yeniden doğrulanır gerekir.</span><span class="sxs-lookup"><span data-stu-id="29337-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
-   <span data-ttu-id="29337-110">Önbellek İlkesi ayarlarsa `maxAge` = 2 gün ve `minFresh` = 2 gün göre `maxAge`, içeriği 3 Ocak tarihine kadar yeni.</span><span class="sxs-lookup"><span data-stu-id="29337-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="29337-111">Şunlara göre `minFresh` 2 Ocak tarihine kadar yeni içeriktir.</span><span class="sxs-lookup"><span data-stu-id="29337-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="29337-112">Bu nedenle, içeriğin 2 Ocak yeniden doğrulanır gerekir.</span><span class="sxs-lookup"><span data-stu-id="29337-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29337-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29337-113">See Also</span></span>  
 [<span data-ttu-id="29337-114">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="29337-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="29337-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="29337-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="29337-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="29337-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="29337-117">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="29337-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="29337-118">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="29337-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="29337-119">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="29337-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)
