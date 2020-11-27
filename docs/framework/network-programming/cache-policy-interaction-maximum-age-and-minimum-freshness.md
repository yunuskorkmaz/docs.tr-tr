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
ms.openlocfilehash: d4182268341f4a4334a627fc8c9e24fa235f003f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287559"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="608c1-102">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="608c1-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="608c1-103">En son içeriğin istemci uygulamasına döndürüldüğünden emin olmak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="608c1-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="608c1-104">Bu konudaki tüm örneklerde, 1 Ocak tarihinde önbelleğe alınan ve 4 Ocak tarihinde sona erecek bir kaynağın önbellek ilkesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="608c1-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="608c1-105">Aşağıdaki örneklerde, maksimum yaş ( `maxAge` ) ve en düşük yeniliği () değerlerinin etkileşimini elde eden önbellek ilkesi gösterilmektedir `minFresh` .</span><span class="sxs-lookup"><span data-stu-id="608c1-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="608c1-106">Önbellek ilkesi `maxAge` = 2 gün ayarlaırsa ve `minFresh` belirtilmemişse, Içerik 3 Ocak 'ta yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="608c1-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="608c1-107">Önbellek ilkesi `maxAge` öğesine göre = 2 gün ve `minFresh` = 1 gün ayarlanırsa `maxAge` , içerik 3 ' e kadar yeni olur.</span><span class="sxs-lookup"><span data-stu-id="608c1-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="608c1-108">Öğesine göre `minFresh` , içerik 3 ' e kadar yeni olur.</span><span class="sxs-lookup"><span data-stu-id="608c1-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="608c1-109">Bu nedenle, içeriğin 3 Ocak tarihinde yeniden doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="608c1-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="608c1-110">Önbellek ilkesi `maxAge` = 2 gün ve `minFresh` = 2 gün, öğesine göre ayarlanırsa `maxAge` , içerik 3 ' e kadar yeni olur.</span><span class="sxs-lookup"><span data-stu-id="608c1-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="608c1-111">İçeriğe göre `minFresh` 2 Ocak 'a kadar yeni bir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="608c1-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="608c1-112">Bu nedenle, içeriğin 2 Ocak 'ta yeniden doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="608c1-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608c1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="608c1-113">See also</span></span>

- [<span data-ttu-id="608c1-114">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="608c1-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="608c1-115">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="608c1-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="608c1-116">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="608c1-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="608c1-117">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="608c1-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="608c1-118">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="608c1-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="608c1-119">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="608c1-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
