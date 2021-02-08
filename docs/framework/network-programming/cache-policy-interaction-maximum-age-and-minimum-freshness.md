---
description: Önbellek Ilkesi etkileşimi — maksimum yaş ve en düşük yeniliği hakkında daha fazla bilgi edinin
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
ms.openlocfilehash: 882df93d44c0d745fcf30a7d9be3152797df4844
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791653"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="bf5d7-103">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Az Eskime</span><span class="sxs-lookup"><span data-stu-id="bf5d7-103">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="bf5d7-104">En son içeriğin istemci uygulamasına döndürüldüğünden emin olmak için, istemci önbellek ilkesi ve sunucu yeniden doğrulama gereksinimlerinin etkileşimi her zaman en klasik önbellek ilkesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-104">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="bf5d7-105">Bu konudaki tüm örneklerde, 1 Ocak tarihinde önbelleğe alınan ve 4 Ocak tarihinde sona erecek bir kaynağın önbellek ilkesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-105">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="bf5d7-106">Aşağıdaki örneklerde, maksimum yaş ( `maxAge` ) ve en düşük yeniliği () değerlerinin etkileşimini elde eden önbellek ilkesi gösterilmektedir `minFresh` .</span><span class="sxs-lookup"><span data-stu-id="bf5d7-106">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="bf5d7-107">Önbellek ilkesi `maxAge` = 2 gün ayarlaırsa ve `minFresh` belirtilmemişse, Içerik 3 Ocak 'ta yeniden onaylanır.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-107">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="bf5d7-108">Önbellek ilkesi `maxAge` öğesine göre = 2 gün ve `minFresh` = 1 gün ayarlanırsa `maxAge` , içerik 3 ' e kadar yeni olur.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-108">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="bf5d7-109">Öğesine göre `minFresh` , içerik 3 ' e kadar yeni olur.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-109">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="bf5d7-110">Bu nedenle, içeriğin 3 Ocak tarihinde yeniden doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-110">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="bf5d7-111">Önbellek ilkesi `maxAge` = 2 gün ve `minFresh` = 2 gün, öğesine göre ayarlanırsa `maxAge` , içerik 3 ' e kadar yeni olur.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-111">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="bf5d7-112">İçeriğe göre `minFresh` 2 Ocak 'a kadar yeni bir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-112">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="bf5d7-113">Bu nedenle, içeriğin 2 Ocak 'ta yeniden doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-113">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5d7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-114">See also</span></span>

- [<span data-ttu-id="bf5d7-115">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="bf5d7-115">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="bf5d7-116">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="bf5d7-116">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="bf5d7-117">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="bf5d7-117">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="bf5d7-118">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="bf5d7-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="bf5d7-119">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bf5d7-119">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="bf5d7-120">Önbellek İlkesi Etkileşimi — Yaş Üst Sınırı ve En Fazla Eskime</span><span class="sxs-lookup"><span data-stu-id="bf5d7-120">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
