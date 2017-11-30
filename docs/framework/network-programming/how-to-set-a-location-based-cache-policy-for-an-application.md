---
title: "Nasıl yapılır: bir uygulama için bir konum temelli önbellek İlkesi ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a145bf30930c9be81dc92f3a9f1eebda046b7e8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="d6e66-102">Nasıl yapılır: bir uygulama için bir konum temelli önbellek İlkesi ayarlama</span><span class="sxs-lookup"><span data-stu-id="d6e66-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="d6e66-103">Konum temelli önbellek ilkeleri açıkça istenen kaynak konumunu temelinde önbelleğe alma davranışını tanımlamak bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e66-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="d6e66-104">Bu konuda, önbellek ilkesini programlı olarak ayarlama gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d6e66-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="d6e66-105">Yapılandırma dosyalarını kullanarak bir uygulama için ilke ayarlama hakkında daha fazla bilgi için bkz: [ \<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="d6e66-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="d6e66-106">Bir uygulama için bir konum temelli önbellek ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6e66-106">To set a location-based cache policy for an application</span></span>  
  
1.  <span data-ttu-id="d6e66-107">Oluşturma bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d6e66-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2.  <span data-ttu-id="d6e66-108">Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d6e66-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="d6e66-109">İstenen kaynaklar bir önbellekten alır ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6e66-109">To set a policy that takes requested resources from a cache</span></span>  
  
-   <span data-ttu-id="d6e66-110">İstenen kaynaklar kullanılabiliyorsa bir önbellekten alır ve aksi durumda, önbelleği düzeyini ayarlayarak istekleri sunucuya gönderir bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="d6e66-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="d6e66-111">Uzak önbellekleri da dahil, sunucu ve istemci arasındaki tüm önbelleği tarafından bir istek yerine getirilmesi.</span><span class="sxs-lookup"><span data-stu-id="d6e66-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="d6e66-112">Kaynak sağlama tüm önbellek önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6e66-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
-   <span data-ttu-id="d6e66-113">Önbelleği düzeyini ayarlayarak istenen kaynaklar sağladığını herhangi önbellek engelleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="d6e66-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="d6e66-114">Bu ilke düzeyi varsa ve bunlar da kaynak kaldırmalısınız uzak önbellekleri gösterir kaynak yerel önbellekten kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d6e66-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="d6e66-115">İstenen kaynaklar yalnızca yerel önbellekte varsa döndüren bir ilkesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6e66-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
-   <span data-ttu-id="d6e66-116">İstenen kaynaklar yalnızca yerel önbellekteki önbelleği düzeyini ayarlayarak olmaları durumunda döndüren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="d6e66-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="d6e66-117">İstenen kaynak önbelleğinde değilse, bir <xref:System.Net.WebException> özel durumu oluşur.</span><span class="sxs-lookup"><span data-stu-id="d6e66-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="d6e66-118">Yerel önbelleğe kaynakları sağladığını önleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6e66-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
-   <span data-ttu-id="d6e66-119">Önbelleği düzeyini ayarlayarak istenen kaynaklar sağladığını yerel önbelleği engelleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="d6e66-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="d6e66-120">İstenen kaynak Ara cache içinde olduğundan ve başarıyla yeniden doğrulanır, Ara önbelleği istenen kaynak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6e66-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="d6e66-121">İstenen kaynakları sağladığını gelen tüm önbellek önleyen bir ilke ayarlayın</span><span class="sxs-lookup"><span data-stu-id="d6e66-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
-   <span data-ttu-id="d6e66-122">Önbelleği düzeyini ayarlayarak istenen kaynaklar sağladığını herhangi önbellek engelleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="d6e66-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="d6e66-123">Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="d6e66-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="d6e66-124">Kaynak sunucuda önbelleğe alınmış kopyadan yeni değilse, istenen kaynak sağlamak bir önbellek izin veren bir İlkesi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d6e66-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
-   <span data-ttu-id="d6e66-125">Kaynak sunucuda önbelleği düzeyini ayarlayarak önbelleğe alınmış kopyadan yeni değilse, istenen kaynak sağlamak tüm önbellek izin veren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="d6e66-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6e66-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6e66-126">See Also</span></span>  
 [<span data-ttu-id="d6e66-127">Ağ uygulamaları için önbellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="d6e66-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="d6e66-128">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="d6e66-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="d6e66-129">Konum temelli önbellek ilkeleri</span><span class="sxs-lookup"><span data-stu-id="d6e66-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="d6e66-130">Önbellek zaman tabanlı ilkeleri</span><span class="sxs-lookup"><span data-stu-id="d6e66-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="d6e66-131">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d6e66-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
