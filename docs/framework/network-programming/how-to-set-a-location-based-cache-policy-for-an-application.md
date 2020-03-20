---
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
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180775"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="848c8-102">Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="848c8-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="848c8-103">Konum tabanlı önbellek ilkeleri, bir uygulamanın istenen kaynağın konumuna bağlı olarak önbelleğe alma davranışını açıkça tanımlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="848c8-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="848c8-104">Bu konu, önbellek ilkesini programlı bir şekilde ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="848c8-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="848c8-105">Yapılandırma dosyalarını kullanarak bir uygulama nın ilkesini ayarlama hakkında bilgi için isteğe> [ \<Öğesi (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="848c8-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="848c8-106">Bir uygulama için konum tabanlı önbellek ilkesi ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="848c8-107">Bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="848c8-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="848c8-108">İlke nesnesini uygulama etki alanı için varsayılan olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="848c8-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="848c8-109">Önbellekten istenen kaynakları alan bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="848c8-110">Varsa önbellekten istenen kaynakları alan ve aksi takdirde önbellek düzeyini ayarlayarak istekleri sunucuya <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>gönderen bir ilke oluşturun.</span><span class="sxs-lookup"><span data-stu-id="848c8-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="848c8-111">İstek, istemci ve sunucu arasındaki uzak önbellekler de dahil olmak üzere herhangi bir önbellek tarafından yerine getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="848c8-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="848c8-112">Önbelleğin kaynak sağlamasını engelleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="848c8-113">Önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>'ye ayarlayarak herhangi bir önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke oluşturun</span><span class="sxs-lookup"><span data-stu-id="848c8-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="848c8-114">Bu ilke düzeyi, varsa kaynağı yerel önbellekten kaldırır ve uzak önbelleğe almalarına da kaynak kaldırmaları gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="848c8-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="848c8-115">İstenen kaynakları yalnızca yerel önbellekteyse döndüren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="848c8-116">İstenen kaynakları yalnızca önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>'ne ayarlayarak yerel önbellekteyse döndüren bir ilke oluşturun</span><span class="sxs-lookup"><span data-stu-id="848c8-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="848c8-117">İstenen kaynak önbellekte değilse, <xref:System.Net.WebException> bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="848c8-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="848c8-118">Yerel önbelleğin kaynak sağlamasını engelleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="848c8-119">Önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>'ye ayarlayarak yerel önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke oluşturun</span><span class="sxs-lookup"><span data-stu-id="848c8-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="848c8-120">İstenen kaynak ara önbellekteyse ve başarıyla yeniden doğrulanırsa, ara önbellek istenen kaynağı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="848c8-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="848c8-121">Herhangi bir önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="848c8-122">Önbellek düzeyini <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>'ye ayarlayarak herhangi bir önbelleğin istenen kaynakları sağlamasını engelleyen bir ilke oluşturun</span><span class="sxs-lookup"><span data-stu-id="848c8-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="848c8-123">Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="848c8-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="848c8-124">Sunucudaki kaynak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına izin veren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="848c8-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="848c8-125">Sunucudaki kaynak önbellek düzeyini ayarlayarak önbelleğe alınmış kopyadan daha yeni değilse, herhangi bir önbelleğin istenen kaynakları sağlamasına <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>izin veren bir ilke oluşturun.</span><span class="sxs-lookup"><span data-stu-id="848c8-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="848c8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="848c8-126">See also</span></span>

- [<span data-ttu-id="848c8-127">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="848c8-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="848c8-128">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="848c8-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="848c8-129">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="848c8-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="848c8-130">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="848c8-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="848c8-131">\<requestCaching> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="848c8-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
