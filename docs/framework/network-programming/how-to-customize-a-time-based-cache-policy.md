---
title: 'Nasıl yapılır: zaman tabanlı önbellek ilkesini özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040628"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="9f36b-102">Nasıl yapılır: zaman tabanlı önbellek ilkesini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9f36b-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="9f36b-103">Zaman tabanlı önbellek ilkesi oluştururken, en yüksek yaş, en düşük yenilik, en yüksek eskime veya önbellek eşitleme tarihi değerlerini belirterek önbelleğe alma davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f36b-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="9f36b-104"><xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi, bu değerlerin geçerli birleşimlerini belirtmenize izin veren çeşitli oluşturucular sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f36b-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="9f36b-105">Önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9f36b-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="9f36b-106">Bir <xref:System.DateTime> nesnesini <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusuna geçirerek önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9f36b-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
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

<span data-ttu-id="9f36b-107">Çıktı aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="9f36b-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="9f36b-108">En düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9f36b-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="9f36b-109">`cacheAgeControl` parametresi değeri olarak <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> belirterek ve <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusuna bir <xref:System.TimeSpan> nesnesi geçirerek en düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9f36b-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
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

<span data-ttu-id="9f36b-110">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="9f36b-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="9f36b-111">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="9f36b-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="9f36b-112">En düşük yeniliği ve en yüksek kullanım süresini temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9f36b-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="9f36b-113">`cacheAgeControl` parametresi değeri olarak <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> belirtip en yüksek yaşına dayalı bir zaman tabanlı önbellek ilkesi oluşturun ve <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusuna iki <xref:System.TimeSpan> nesnesi geçirerek, biri kaynaklar için maksimum yaş değerini ve ikincisi önbellekten döndürülen bir nesne için izin verilen en düşük yeniliği belirtin:</span><span class="sxs-lookup"><span data-stu-id="9f36b-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
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

<span data-ttu-id="9f36b-114">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="9f36b-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="9f36b-115">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="9f36b-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f36b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f36b-116">See also</span></span>

- [<span data-ttu-id="9f36b-117">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="9f36b-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="9f36b-118">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="9f36b-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="9f36b-119">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="9f36b-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="9f36b-120">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="9f36b-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="9f36b-121">\<requestCaching > öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="9f36b-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
