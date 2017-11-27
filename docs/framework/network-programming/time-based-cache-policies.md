---
title: "Önbellek zaman tabanlı ilkeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d4cfa67d7fba06140838e04bdbff71102a2a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="time-based-cache-policies"></a><span data-ttu-id="17d6f-102">Önbellek zaman tabanlı ilkeleri</span><span class="sxs-lookup"><span data-stu-id="17d6f-102">Time-Based Cache Policies</span></span>
<span data-ttu-id="17d6f-103">Bir zamana dayalı önbellek İlkesi üstbilgileri kaynakla döndürülen kaynak alınan saati ve geçerli saati kullanarak önbelleğe alınmış girişleri yenilik tanımlar.</span><span class="sxs-lookup"><span data-stu-id="17d6f-103">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, the headers returned with the resource, and the current time.</span></span> <span data-ttu-id="17d6f-104">Önbellek zaman tabanlı ilke ayarı, kullanabilir <xref:System.Net.Cache.HttpRequestCacheLevel.Default> zaman tabanlı ilke veya özelleştirilmiş bir zamana dayalı ilkesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17d6f-104">When setting a time-based cache policy, you can either use the <xref:System.Net.Cache.HttpRequestCacheLevel.Default> time-based policy or create a customized time-based policy.</span></span> <span data-ttu-id="17d6f-105">Varsayılan zaman tabanlı ilke için Köprü Metni Aktarım Protokolü (HTTP) kullanarak elde kaynaklar kullanırken, tam önbellek davranışını 13 ve RFC 2616 14 bölümlerinde belirtilen davranışları ve önbelleğe alınan yanıta dahil üstbilgileri tarafından belirlenir, adresinde [http://www.ietf.org](http://www.ietf.org/). HTTP kaynaklar için varsayılan zaman tabanlı ilke ayarı gösteren kod örneği için bkz: [nasıl yapılır: bir uygulama Default Time-Based önbellek İlkesi ayarlama](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="17d6f-105">When using the default time-based policy for resources obtained using Hypertext Transfer Protocol (HTTP), the exact cache behavior is determined by the headers included in the cached response and by the behaviors specified in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). For a code example that demonstrates setting the default time-based policy for HTTP resources, see [How to: Set the Default Time-Based Cache Policy for an Application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="17d6f-106">Önbellek ilkeleri oluşturma ve kullanma gösteren kod örnekleri için bkz: [yapılandırma önbelleği ağ uygulamalarda](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span><span class="sxs-lookup"><span data-stu-id="17d6f-106">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a><span data-ttu-id="17d6f-107">Önbelleğe alınan girişlerinin yenilik belirlemek için ölçütü</span><span class="sxs-lookup"><span data-stu-id="17d6f-107">Criteria to Determine Freshness of Cached Entries</span></span>  
 <span data-ttu-id="17d6f-108">Bir zamana dayalı önbellek İlkesi özelleştirmek için bir veya daha fazla aşağıdaki ölçütleri önbelleğe alınan girdileri yenilik belirlemek için kullanılabilir belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17d6f-108">To customize a time-based cache policy, you can specify that one or more of the following criteria be used to determine the freshness of cached entries:</span></span>  
  
-   <span data-ttu-id="17d6f-109">En uzun geçerlilik süresi</span><span class="sxs-lookup"><span data-stu-id="17d6f-109">Maximum age</span></span>  
  
-   <span data-ttu-id="17d6f-110">En fazla eskime durumu</span><span class="sxs-lookup"><span data-stu-id="17d6f-110">Maximum staleness</span></span>  
  
-   <span data-ttu-id="17d6f-111">Minimum yenilik</span><span class="sxs-lookup"><span data-stu-id="17d6f-111">Minimum freshness</span></span>  
  
-   <span data-ttu-id="17d6f-112">Önbellek eşitleme tarihi</span><span class="sxs-lookup"><span data-stu-id="17d6f-112">Cache synchronization date</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17d6f-113">Varsayılan zamana dayalı önbellek İlkesi'ni kullanarak uygulamanız için bir varsayılan önbellek İlkesi ayarı ile karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="17d6f-113">Using the default time-based cache policy should not be confused with setting a default cache policy for your application.</span></span> <span data-ttu-id="17d6f-114">Varsayılan zaman tabanlı ilke isteği veya uygulama düzeyinde kullanılabilen belirli bir ilkedir.</span><span class="sxs-lookup"><span data-stu-id="17d6f-114">The default time-based policy is a specific policy that can be used at the request or application level.</span></span> <span data-ttu-id="17d6f-115">Varsayılan önbellek İlkesi uygulamanız için bir istekte hiçbir ilkeyi ayarladığınızda, etkinleşir bir (konum temelli veya zamana dayalı) ilkesidir.</span><span class="sxs-lookup"><span data-stu-id="17d6f-115">The default cache policy for your application is a policy (location-based or time-based) that takes effect when no policy is set on a request.</span></span> <span data-ttu-id="17d6f-116">Uygulamanız için varsayılan bir önbellek ilkesini ayarlama hakkında daha fazla bilgi için bkz: <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span><span class="sxs-lookup"><span data-stu-id="17d6f-116">For details on setting a default cache policy for your application, see <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.</span></span>  
  
### <a name="maximum-age"></a><span data-ttu-id="17d6f-117">En uzun geçerlilik süresi</span><span class="sxs-lookup"><span data-stu-id="17d6f-117">Maximum Age</span></span>  
 <span data-ttu-id="17d6f-118">En uzun geçerlilik süresi İlkesi ölçüt bir kaynağın önbelleğe alınmış bir kopyasını kullanılabilir süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="17d6f-118">The maximum age policy criterion specifies the amount of time a cached copy of a resource can be used.</span></span> <span data-ttu-id="17d6f-119">Kaynağın önbelleğe alınmış kopyasını belirtilen süre miktarını eski ise, kaynak sunucunuzdaki içeriğe karşı denetleyerek gerekiyor.%0.</span><span class="sxs-lookup"><span data-stu-id="17d6f-119">If the cached copy of the resource is older than the amount of time specified, the resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="17d6f-120">En uzun geçerlilik süresi sona ermeden sonra kullanılmak üzere kaynak olanak tanır, bu ölçütü değil dikkate alınır maksimum eskime durumu değeri de belirtilmedikçe.</span><span class="sxs-lookup"><span data-stu-id="17d6f-120">If the maximum age would allow the resource to be used after it expires, this criteria is not honored unless a maximum staleness value is also specified.</span></span>  
  
### <a name="maximum-staleness"></a><span data-ttu-id="17d6f-121">En fazla eskime durumu</span><span class="sxs-lookup"><span data-stu-id="17d6f-121">Maximum Staleness</span></span>  
 <span data-ttu-id="17d6f-122">En fazla eskime durumu ilkesi ölçüt kaynağın önbelleğe alınmış kopyasını kullanılabilir içerik sona erme sonra geçen süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="17d6f-122">The maximum staleness policy criterion specifies the length of time after content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="17d6f-123">Bu kaynaklar süresi dolduktan sonra kullanılacak veren yalnızca önbellek İlkesi ölçüttür.</span><span class="sxs-lookup"><span data-stu-id="17d6f-123">This is the only cache policy criterion that permits resources to be used after they have expired.</span></span>  
  
### <a name="minimum-freshness"></a><span data-ttu-id="17d6f-124">Minimum yenilik</span><span class="sxs-lookup"><span data-stu-id="17d6f-124">Minimum Freshness</span></span>  
 <span data-ttu-id="17d6f-125">Minimum yenilik İlkesi ölçüt kaynağın önbelleğe alınmış kopyasını kullanılabilir içerik geçerliliği sona ermeden önce geçen süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="17d6f-125">The minimum freshness policy criterion specifies the length of time before content expiration that the cached copy of the resource can be used.</span></span> <span data-ttu-id="17d6f-126">Bu ilke, sona erme tarihinden önce süresi dolacak şekilde bir önbellek girişi neden etkisi vardır; Bu nedenle, en fazla eskime durumu ayarlarını ve minimum yenilik karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="17d6f-126">This policy has the effect of causing a cache entry to expire before its expiration date; therefore, the minimum freshness and maximum staleness settings are mutually exclusive.</span></span>  
  
## <a name="cache-synchronization-date"></a><span data-ttu-id="17d6f-127">Önbellek eşitleme tarihi</span><span class="sxs-lookup"><span data-stu-id="17d6f-127">Cache Synchronization Date</span></span>  
 <span data-ttu-id="17d6f-128">Önbellek eşitleme tarih ilkesi ölçütü, sunucunuzdaki içeriğe karşı denetleyerek bir kaynağın önbelleğe alınmış bir kopyasını zaman gerekiyor.%0 belirler.</span><span class="sxs-lookup"><span data-stu-id="17d6f-128">The cache synchronization date policy criterion determines when a cached copy of a resource must be revalidated by checking it against the content on the server.</span></span> <span data-ttu-id="17d6f-129">İçeriği, öğenin önbelleğe oluşturulmasından sonra değiştirilmişse, sunucudan alınan, önbellekte saklanan ve uygulamaya döndürdü.</span><span class="sxs-lookup"><span data-stu-id="17d6f-129">If the content has changed since the item was cached, it is retrieved from the server, stored in the cache, and returned to the application.</span></span> <span data-ttu-id="17d6f-130">İçerik değişmemişse, zaman damgası güncelleştirilir ve uygulama önbelleğe alınmış içeriği alır.</span><span class="sxs-lookup"><span data-stu-id="17d6f-130">If the content has not changed, its timestamp is updated and the application gets the cached content.</span></span>  
  
 <span data-ttu-id="17d6f-131">Önbellek eşitleme tarihi ne zaman önbelleğe alınmış içeriği gerekiyor.%0 mutlak bir tarih belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="17d6f-131">The cache synchronization date allows you to specify an absolute date when cached contents must be revalidated.</span></span> <span data-ttu-id="17d6f-132">Yeni bir önbellek girişi önbellek eşitleme tarihinden önce en son yeniden doğrulanır, sunucu ile yeniden doğrulanması oluşmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="17d6f-132">If a fresh cache entry was last revalidated prior to the cache synchronization date, revalidation with the server still occurs.</span></span> <span data-ttu-id="17d6f-133">Önbellek girişi önbellek eşitleme tarihinden sonra yeniden doğrulanır ve ek yenilik veya önbelleğe alınan girdinin geçersiz sunucu yeniden doğrulanması gereksinimleri yoktur, önbellek girişi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17d6f-133">If the cache entry was revalidated after the cache synchronization date and there are no additional freshness or server revalidation requirements that invalidate the cached entry, the entry from the cache is used.</span></span> <span data-ttu-id="17d6f-134">Önbellek eşitleme tarihi gelecekteki bir tarih olarak ayarlanırsa, giriş önbellek eşitleme tarihini geçerse kadar her istendiğinde yeniden doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="17d6f-134">If the cache synchronization date is set to a future date, the entry is revalidated every time it is requested, until the cache synchronization date passes.</span></span>  
  
 <span data-ttu-id="17d6f-135">Aşağıdaki konular zamana dayalı önbellek İlkesi ölçütlerini birleştirmenin etkileri hakkında bilgi sağlar:</span><span class="sxs-lookup"><span data-stu-id="17d6f-135">The following topics provide information about the effects of combining time-based cache policy criteria:</span></span>  
  
-   [<span data-ttu-id="17d6f-136">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve en fazla eskime durumu</span><span class="sxs-lookup"><span data-stu-id="17d6f-136">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [<span data-ttu-id="17d6f-137">Önbellek İlkesi etkileşim — en uzun geçerlilik süresi ve Minimum yenilik</span><span class="sxs-lookup"><span data-stu-id="17d6f-137">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a><span data-ttu-id="17d6f-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17d6f-138">See Also</span></span>  
 [<span data-ttu-id="17d6f-139">Ağ uygulamaları için önbellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="17d6f-139">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="17d6f-140">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="17d6f-140">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="17d6f-141">Konum temelli önbellek ilkeleri</span><span class="sxs-lookup"><span data-stu-id="17d6f-141">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="17d6f-142">Ağ uygulamalarında önbelleğe alma yapılandırma</span><span class="sxs-lookup"><span data-stu-id="17d6f-142">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [<span data-ttu-id="17d6f-143">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="17d6f-143">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
