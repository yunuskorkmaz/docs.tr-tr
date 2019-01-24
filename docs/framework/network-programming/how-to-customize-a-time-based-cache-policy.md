---
title: 'Nasıl yapılır: Bir saat temelli önbellek ilkesini özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 9d1eef073588f45e70170fcf46766b53f99bed8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505815"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="d7e8e-102">Nasıl yapılır: Bir saat temelli önbellek ilkesini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d7e8e-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="d7e8e-103">Bir saat temelli önbellek ilkesi oluştururken en uzun geçerlilik süresi, en az eskime, en fazla eskime veya önbellek eşitleme tarih değerleri belirtilerek, önbelleğe alma davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7e8e-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="d7e8e-104"><xref:System.Net.Cache.HttpRequestCachePolicy> Nesnesi, bu değerleri geçerli birleşimleri belirtmek olanak tanıyan birkaç Oluşturucusu sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7e8e-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="d7e8e-105">Bir önbellek eşitleme tarihi kullanan bir saat temelli önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7e8e-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
-   <span data-ttu-id="d7e8e-106">Bir önbellek eşitleme tarihi geçirerek kullanan bir saat temelli önbellek ilkesi oluşturma bir <xref:System.DateTime> nesnesini <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="d7e8e-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="d7e8e-107">Çıktı aşağıdakine benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d7e8e-107">The output is similar to the following:</span></span>  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="d7e8e-108">Üzerinde en az eskime dayalı olarak bir saat temelli önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7e8e-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
-   <span data-ttu-id="d7e8e-109">Üzerinde en az eskime belirterek temel bir saat temelli önbellek İlkesi <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> olarak `cacheAgeControl` parametre değeri ve geçirme bir <xref:System.TimeSpan> nesnesini <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="d7e8e-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="d7e8e-110">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="d7e8e-110">For the following invocation:</span></span>  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="d7e8e-111">En az eskime ve en yüksek yaşı dayalı olarak bir saat temelli önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d7e8e-111">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
-   <span data-ttu-id="d7e8e-112">En az eskime ve en uzun geçerlilik süresi, belirterek dayalı olarak bir saat temelli önbellek İlkesi <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> olarak `cacheAgeControl` parametre değeri ve iki geçirme <xref:System.TimeSpan> nesneleri için <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusu, en fazla geçerlilik süresini belirtmek için Kaynaklar ve en az eskime belirtmek için ikinci bir önbellekten döndürülen bir nesne için izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d7e8e-112">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
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
  
 <span data-ttu-id="d7e8e-113">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="d7e8e-113">For the following invocation:</span></span>  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7e8e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e8e-114">See also</span></span>
- [<span data-ttu-id="d7e8e-115">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="d7e8e-115">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="d7e8e-116">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="d7e8e-116">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="d7e8e-117">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="d7e8e-117">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="d7e8e-118">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="d7e8e-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="d7e8e-119">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="d7e8e-119">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
