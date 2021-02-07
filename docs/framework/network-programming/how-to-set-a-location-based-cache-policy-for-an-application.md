---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bir uygulama için Location-Based önbellek Ilkesi ayarlama'
title: 'Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: d86e40e24eacb6ce3107e50213941c1169191943
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662786"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="87c52-103">Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="87c52-103">How to: Set a Location-Based Cache Policy for an Application</span></span>

<span data-ttu-id="87c52-104">Konum tabanlı önbellek ilkeleri, bir uygulamanın, istenen kaynağın konumuna göre önbelleğe alma davranışını açıkça tanımlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="87c52-104">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="87c52-105">Bu konuda, önbellek ilkesinin programlı olarak ayarlanması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="87c52-105">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="87c52-106">Yapılandırma dosyalarını kullanarak bir uygulama için ilke ayarlama hakkında daha fazla bilgi için bkz. [ \<requestCaching> öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="87c52-106">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="87c52-107">Bir uygulama için konum tabanlı önbellek ilkesi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-107">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="87c52-108">Bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87c52-108">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="87c52-109">İlke nesnesini, uygulama etki alanı için varsayılan olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87c52-109">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="87c52-110">Bir önbellekten istenen kaynakları alan bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-110">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="87c52-111">Varsa, bir önbellekten istenen kaynakları alan bir ilke oluşturun ve aksi takdirde, önbellek düzeyini olarak ayarlayarak sunucuya istek gönderir <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> .</span><span class="sxs-lookup"><span data-stu-id="87c52-111">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="87c52-112">İstek, uzak önbellekler dahil olmak üzere istemci ve sunucu arasındaki herhangi bir önbellekte yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87c52-112">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="87c52-113">Herhangi bir önbelleğin kaynakları almasını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-113">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="87c52-114">Önbellek düzeyini olarak ayarlayarak herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore> .</span><span class="sxs-lookup"><span data-stu-id="87c52-114">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="87c52-115">Bu ilke düzeyi, varsa kaynağı yerel önbellekten kaldırır ve ayrıca uzak önbelleklerin kaynağı kaldırması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="87c52-115">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="87c52-116">Yalnızca yerel önbellekte olduklarında, istenen kaynakları döndüren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-116">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="87c52-117">İstenen kaynakları, yalnızca önbellek düzeyini olarak ayarlayarak yerel önbellekte olduklarında döndüren bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly> .</span><span class="sxs-lookup"><span data-stu-id="87c52-117">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="87c52-118">İstenen kaynak önbellekte değilse, bir <xref:System.Net.WebException> özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="87c52-118">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="87c52-119">Yerel önbelleğin kaynakları almasını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-119">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="87c52-120">Önbellek düzeyini olarak ayarlayarak yerel önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh> .</span><span class="sxs-lookup"><span data-stu-id="87c52-120">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="87c52-121">İstenen kaynak bir ara önbellekte ise ve başarıyla yeniden doğrulandıktan sonra, ara önbellek istenen kaynağı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="87c52-121">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="87c52-122">Herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-122">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="87c52-123">Önbellek düzeyini olarak ayarlayarak herhangi bir önbelleğin istenen kaynakları almasını önleyen bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Reload> .</span><span class="sxs-lookup"><span data-stu-id="87c52-123">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="87c52-124">Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="87c52-124">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="87c52-125">Sunucudaki kaynak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına izin veren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="87c52-125">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="87c52-126">Sunucudaki kaynak önbellek düzeyini olarak ayarlayarak, sunucudaki kaynağın önbelleğe alınmış kopyadan daha yeni olmaması durumunda, istenen kaynakları sağlamasına izin veren bir ilke oluşturun <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate> .</span><span class="sxs-lookup"><span data-stu-id="87c52-126">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="87c52-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87c52-127">See also</span></span>

- [<span data-ttu-id="87c52-128">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="87c52-128">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="87c52-129">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="87c52-129">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="87c52-130">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="87c52-130">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="87c52-131">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="87c52-131">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="87c52-132">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="87c52-132">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
