---
title: 'Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 5df070bb2cfef42d60247cad39f2a2f76963bae8
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894737"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="8272e-102">Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8272e-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="8272e-103">Zaman tabanlı önbellek ilkesi oluştururken, en yüksek yaş, en düşük yenilik, en yüksek eskime veya önbellek eşitleme tarihi değerlerini belirterek önbelleğe alma davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8272e-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="8272e-104">Nesnesi <xref:System.Net.Cache.HttpRequestCachePolicy> , bu değerlerin geçerli birleşimlerini belirtmenize izin veren çeşitli oluşturucular sağlar.</span><span class="sxs-lookup"><span data-stu-id="8272e-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="8272e-105">Önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8272e-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="8272e-106"><xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucuya bir <xref:System.DateTime> nesne geçirerek önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8272e-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="8272e-107">Çıktı aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="8272e-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="8272e-108">En düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8272e-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="8272e-109">Parametre değeri <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> <xref:System.TimeSpan> olarak belirterek ve <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya bir nesne geçirerek en düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturun. `cacheAgeControl`</span><span class="sxs-lookup"><span data-stu-id="8272e-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="8272e-110">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="8272e-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="8272e-111">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="8272e-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="8272e-112">En düşük yeniliği ve en yüksek kullanım süresini temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8272e-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="8272e-113">Parametre değeri <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> <xref:System.TimeSpan> olarak belirtip en yüksek yaş ve maksimum yaş temelinde bir zaman tabanlı önbellek ilkesi oluşturun ve biri için en fazla yaşı belirtmek üzere iki nesne <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçiş yapın `cacheAgeControl` önbellekten döndürülen bir nesne için izin verilen en düşük yeniliği belirlemek için kaynak ve saniye.</span><span class="sxs-lookup"><span data-stu-id="8272e-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
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
  
 <span data-ttu-id="8272e-114">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="8272e-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="8272e-115">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="8272e-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="8272e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8272e-116">See also</span></span>

- [<span data-ttu-id="8272e-117">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="8272e-117">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="8272e-118">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="8272e-118">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="8272e-119">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="8272e-119">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="8272e-120">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="8272e-120">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="8272e-121">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="8272e-121">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
