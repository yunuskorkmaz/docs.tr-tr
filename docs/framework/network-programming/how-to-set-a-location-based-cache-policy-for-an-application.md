---
title: 'Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1bbbb558134e5f11537de0efef594be2b964cdcb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647380"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="39580-102">Nasıl yapılır: Uygulama için Konum Temelli Önbellek İlkesi Ayarlama</span><span class="sxs-lookup"><span data-stu-id="39580-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="39580-103">Konum temelli önbellek ilkeleri açıkça istenen kaynak konumunu temel alarak önbelleğe alma davranışını tanımlamak bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="39580-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="39580-104">Bu konuda önbellek ilkesini programlı olarak ayarlama gösterilir.</span><span class="sxs-lookup"><span data-stu-id="39580-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="39580-105">Yapılandırma dosyalarını kullanarak bir uygulama için bir ilke ayarlama hakkında daha fazla bilgi için bkz. [ \<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="39580-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="39580-106">Bir uygulama için bir konum temelli önbellek İlkesi ayarlama</span><span class="sxs-lookup"><span data-stu-id="39580-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="39580-107">Oluşturma bir <xref:System.Net.Cache.RequestCachePolicy> veya <xref:System.Net.Cache.HttpRequestCachePolicy> nesne.</span><span class="sxs-lookup"><span data-stu-id="39580-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="39580-108">Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="39580-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="39580-109">Bir önbellekten istenen kaynaklara götüren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39580-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="39580-110">Bir önbellekten kullanılabilir durumdaysa istenen kaynakları alır ve aksi takdirde, önbelleği düzeyini ayarlayarak istekleri sunucuya gönderir, bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="39580-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="39580-111">Bir istek istemci ve uzak önbellekler dahil sunucusu arasındaki tüm önbelleği tarafından getirilmesi.</span><span class="sxs-lookup"><span data-stu-id="39580-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="39580-112">Tüm önbelleği kaynakları sağlama dan engelleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39580-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="39580-113">Önbelleği düzeyini ayarlayarak istenen kaynaklara sağladığı tüm önbelleği önleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="39580-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="39580-114">Varsa ve bunlar da kaynak kaldırmalısınız uzak önbelleklere gösterir. Bu ilke düzeyi kaynak yerel önbellekten kaldırır.</span><span class="sxs-lookup"><span data-stu-id="39580-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="39580-115">İstenen kaynaklara yalnızca yerel önbellek üzerinde olduklarında döndüren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39580-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="39580-116">İstenen kaynaklara yalnızca yerel önbellek üzerinde önbelleği düzeyini ayarlayarak olmaları durumunda döndüren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="39580-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="39580-117">İstenen kaynak önbellekte değilse bir <xref:System.Net.WebException> özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39580-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="39580-118">Yerel önbellek kaynakları sağlama dan engelleyen bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39580-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="39580-119">Yerel önbellek, önbellek düzeyini ayarlayarak istenen kaynaklara sağlama önleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="39580-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="39580-120">İstenen kaynak Ara bir önbellekte ve başarıyla yeniden doğrulanır, istenen kaynak Ara önbellek sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39580-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="39580-121">Kaynaklar istenen tüm önbelleği sağlayarak dan engelleyen bir ilke ayarlama</span><span class="sxs-lookup"><span data-stu-id="39580-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="39580-122">Önbelleği düzeyini ayarlayarak istenen kaynaklara sağladığı tüm önbelleği önleyen bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="39580-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="39580-123">Sunucu tarafından döndürülen kaynak önbellekte depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="39580-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="39580-124">Kaynak sunucuda önbelleğe alınmış kopyayı yeni değil, istenen kaynakları sağlamak tüm önbelleği izin veren bir ilke ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="39580-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="39580-125">Kaynak sunucuda önbelleği düzeyini ayarlayarak önbelleğe alınmış kopyayı yeni değil, istenen kaynakları sağlamak tüm önbelleği izin veren bir ilke oluşturmak <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="39580-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39580-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39580-126">See also</span></span>

- [<span data-ttu-id="39580-127">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="39580-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="39580-128">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="39580-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="39580-129">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="39580-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="39580-130">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="39580-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="39580-131">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="39580-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
