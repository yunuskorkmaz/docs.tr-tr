---
title: 'Nasıl yapılır: bir zamana dayalı önbellek İlkesi özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd2856ffcf6b21ba34771c231f608ad725b21763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390971"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="19bbc-102">Nasıl yapılır: bir zamana dayalı önbellek İlkesi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="19bbc-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="19bbc-103">Bir zamana dayalı önbellek ilkesi oluştururken, en uzun geçerlilik süresi, minimum yenilik, en fazla eskime durumu veya önbellek eşitleme tarihi için değerleri belirtilerek önbelleğe alma davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19bbc-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="19bbc-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Nesnesi, bu değerlerin geçerli birleşimleri belirtmenize olanak veren birkaç Oluşturucusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="19bbc-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="19bbc-105">Bir önbellek eşitleme tarihi kullanan bir zamana dayalı önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19bbc-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
-   <span data-ttu-id="19bbc-106">Bir önbellek eşitleme tarihi geçirerek kullanan bir önbellek zaman tabanlı ilke oluşturmak bir <xref:System.DateTime> nesnesine <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="19bbc-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="19bbc-107">Çıktı aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="19bbc-107">The output is similar to the following:</span></span>  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="19bbc-108">Üzerinde minimum yenilik dayalı bir zamana dayalı önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19bbc-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
-   <span data-ttu-id="19bbc-109">Üzerinde minimum yenilik belirterek dayalı bir zamana dayalı önbellek ilkesi oluşturmak <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> olarak `cacheAgeControl` parametre değeri ve geçirerek bir <xref:System.TimeSpan> nesnesine <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="19bbc-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="19bbc-110">Aşağıdaki çağırma için:</span><span class="sxs-lookup"><span data-stu-id="19bbc-110">For the following invocation:</span></span>  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="19bbc-111">Minimum yenilik ve en uzun geçerlilik süresi dayalı bir zamana dayalı önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="19bbc-111">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
-   <span data-ttu-id="19bbc-112">Belirterek minimum yenilik ve en uzun geçerlilik süresi dayanan bir zamana dayalı önbellek ilkesi oluşturmak <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> olarak `cacheAgeControl` parametre değeri ile iki geçirme <xref:System.TimeSpan> nesneleri <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusu, en fazla geçerlilik belirtmek için kaynakları ve minimum yenilik belirtmek için ikinci bir önbellekten döndürülen bir nesne için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="19bbc-112">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 <span data-ttu-id="19bbc-113">Aşağıdaki çağırma için:</span><span class="sxs-lookup"><span data-stu-id="19bbc-113">For the following invocation:</span></span>  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="19bbc-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19bbc-114">See Also</span></span>  
 [<span data-ttu-id="19bbc-115">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="19bbc-115">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="19bbc-116">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="19bbc-116">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="19bbc-117">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="19bbc-117">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="19bbc-118">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="19bbc-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="19bbc-119">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="19bbc-119">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
