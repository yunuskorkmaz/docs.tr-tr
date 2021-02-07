---
description: 'Daha fazla bilgi edinin: Location-Based önbellek Ilkeleri'
title: Konum Temelli Önbellek İlkeleri
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: ef770b45f173fee66c80d721766a0be6244bbeb9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662721"
---
# <a name="location-based-cache-policies"></a><span data-ttu-id="2c624-103">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="2c624-103">Location-Based Cache Policies</span></span>

<span data-ttu-id="2c624-104">Konum tabanlı önbellek ilkesi, istenen kaynağın nereden alınabileceğini temel alarak geçerli önbelleğe alınmış girişlerin yeniliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c624-104">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="2c624-105">Önbelleğe alınmış bir kaynak, kullanılması durumunda sunucu tarafından belirtilen yeniden doğrulama gereksinimlerini ihlal etmezse geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="2c624-105">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="2c624-106">Konum tabanlı önbellek ilkesi, <xref:System.Net.Cache.RequestCachePolicy> veya sınıf oluşturucusu kullanılarak programlı bir şekilde oluşturulur <xref:System.Net.Cache.HttpRequestCachePolicy> .</span><span class="sxs-lookup"><span data-stu-id="2c624-106">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="2c624-107">Konum tabanlı ilke türü, bir <xref:System.Net.Cache.RequestCacheLevel> veya numaralandırma değeri kullanılarak oluşturucuya geçirilir <xref:System.Net.Cache.HttpRequestCacheLevel> .</span><span class="sxs-lookup"><span data-stu-id="2c624-107">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="2c624-108">Konum tabanlı önbellek ilkeleri oluşturan kod örnekleri için bkz. [nasıl yapılır: bir uygulama için Location-Based önbellek Ilkesi ayarlama](how-to-set-a-location-based-cache-policy-for-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="2c624-108">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="2c624-109">Aşağıdaki bölümlerde, Köprü Metni Aktarım Protokolü (http ve https) kaynakları için her konum tabanlı önbellek ilkesi türü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c624-109">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="2c624-110">Kullanılabilir Ilke varsa önbelleğe al</span><span class="sxs-lookup"><span data-stu-id="2c624-110">Cache If Available Policy</span></span>  

 <span data-ttu-id="2c624-111">Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır; Aksi takdirde, kaynak isteği sunucuya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-111">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="2c624-112">İstenen kaynak, istemci ve sunucu arasındaki herhangi bir önbellekte kullanılabiliyorsa, istek bir ara önbellek tarafından karşılanabilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-112">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="2c624-113">Yalnızca önbellek Ilkesi</span><span class="sxs-lookup"><span data-stu-id="2c624-113">Cache Only Policy</span></span>  

 <span data-ttu-id="2c624-114">Geçerli bir istenen kaynak yerel önbellekte ise, önbelleğe alınmış kaynak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c624-114">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="2c624-115">Bu önbellek ilkesi düzeyi belirtildiğinde, <xref:System.Net.WebException> öğe yerel önbellekte değilse bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c624-115">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="2c624-116">Yalnızca önbellek veya sonraki önbellek Ilkesi</span><span class="sxs-lookup"><span data-stu-id="2c624-116">Cache Or Next Cache Only Policy</span></span>  

 <span data-ttu-id="2c624-117">Geçerli bir istenen kaynak yerel önbellekte veya yerel alan ağı üzerindeki ara önbellekte ise, önbelleğe alınmış kaynak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c624-117">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="2c624-118">Aksi takdirde, bir <xref:System.Net.WebException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c624-118">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="2c624-119">HTTP önbelleğe alma protokolünde, bu, tek-if-önbelleğe alınmış önbellek denetim yönergesi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-119">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="2c624-120">Önbellekte depolama Ilkesi yok</span><span class="sxs-lookup"><span data-stu-id="2c624-120">No Cache No Store Policy</span></span>  

 <span data-ttu-id="2c624-121">İstenen bir kaynak herhangi bir önbellekten hiçbir şekilde kullanılmaz ve hiçbir şekilde hiçbir önbelleğe yerleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="2c624-121">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="2c624-122">İstenen bir kaynak yerel önbellekte mevcutsa, kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="2c624-122">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="2c624-123">Bu ilke düzeyi ara önbelleklerin kaynağı kaldırması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c624-123">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="2c624-124">HTTP önbelleğe alma protokolünde, bu, depolama önbelleği denetim yönergesi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-124">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="2c624-125">Ilkeyi Yenile</span><span class="sxs-lookup"><span data-stu-id="2c624-125">Refresh Policy</span></span>  

 <span data-ttu-id="2c624-126">İstenen kaynak, sunucudan elde edilmişse veya yerel önbellek dışında bir önbellekte bulunursa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-126">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="2c624-127">İstek bir ara önbellek tarafından karşılanmadan önce, bu önbelleğin sunucu ile önbelleğe alınmış girişini yeniden doğrulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2c624-127">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="2c624-128">HTTP önbelleğe alma protokolünde, bu, maksimum yaş = 0 önbellek denetim yönergesi ve No-Cache pragma üst bilgisi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-128">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="2c624-129">Ilkeyi yeniden yükle</span><span class="sxs-lookup"><span data-stu-id="2c624-129">Reload Policy</span></span>  

 <span data-ttu-id="2c624-130">İstenen kaynaklar sunucudan alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c624-130">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="2c624-131">Yanıt, yerel önbellekte kaydedilmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-131">The response might be saved in the local cache.</span></span> <span data-ttu-id="2c624-132">HTTP önbelleğe alma protokolünde, bu, önbellek önbelleği denetim yönergesi ve No-Cache pragma üst bilgisi kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-132">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="2c624-133">Ilkeyi yeniden doğrula</span><span class="sxs-lookup"><span data-stu-id="2c624-133">Revalidate Policy</span></span>  

 <span data-ttu-id="2c624-134">Önbellekteki kaynağın kopyasını sunucudaki kopyayla karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="2c624-134">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="2c624-135">Sunucu üzerindeki kopya yeniyse, isteği karşılamak için kullanılır ve önbellekteki kopyayı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2c624-135">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="2c624-136">Önbellekteki kopya sunucu kopyasıyla aynıysa, önbelleğe alınan kopya kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2c624-136">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="2c624-137">HTTP önbelleğe alma protokolünde bu, koşullu bir istek kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2c624-137">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c624-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c624-138">See also</span></span>

- [<span data-ttu-id="2c624-139">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="2c624-139">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="2c624-140">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="2c624-140">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="2c624-141">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="2c624-141">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="2c624-142">Ağ Uygulamalarında Önbelleğe Almayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2c624-142">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="2c624-143">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="2c624-143">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
