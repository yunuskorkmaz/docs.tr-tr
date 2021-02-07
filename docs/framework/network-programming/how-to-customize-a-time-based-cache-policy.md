---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: zaman tabanlı önbellek ilkesini özelleştirme'
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
ms.openlocfilehash: bb00faa5c2cd3170a0f56b74032867d489c1fb8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747458"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="0f6c5-103">Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0f6c5-103">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="0f6c5-104">Zaman tabanlı önbellek ilkesi oluştururken, en yüksek yaş, en düşük yenilik, en yüksek eskime veya önbellek eşitleme tarihi değerlerini belirterek önbelleğe alma davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f6c5-104">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="0f6c5-105"><xref:System.Net.Cache.HttpRequestCachePolicy>Nesnesi, bu değerlerin geçerli birleşimlerini belirtmenize izin veren çeşitli oluşturucular sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f6c5-105">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="0f6c5-106">Önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0f6c5-106">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="0f6c5-107">Oluşturucuya bir nesne geçirerek önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturun <xref:System.DateTime> <xref:System.Net.Cache.HttpRequestCachePolicy> :</span><span class="sxs-lookup"><span data-stu-id="0f6c5-107">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="0f6c5-108">Çıkış aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="0f6c5-108">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="0f6c5-109">En düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0f6c5-109">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="0f6c5-110"><xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> `cacheAgeControl` Parametre değeri olarak belirterek ve oluşturucuya bir nesne geçirerek en düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturun <xref:System.TimeSpan> <xref:System.Net.Cache.HttpRequestCachePolicy> :</span><span class="sxs-lookup"><span data-stu-id="0f6c5-110">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="0f6c5-111">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="0f6c5-111">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="0f6c5-112">Çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="0f6c5-112">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="0f6c5-113">En düşük yeniliği ve en yüksek kullanım süresini temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0f6c5-113">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="0f6c5-114">Parametre değeri olarak belirterek en düşük yeniliği ve maksimum yaşı temel alan zaman tabanlı bir önbellek ilkesi oluşturun <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> `cacheAgeControl` ve iki <xref:System.TimeSpan> nesneyi oluşturucuya geçirerek <xref:System.Net.Cache.HttpRequestCachePolicy> bir tane, kaynak için en yüksek yaş değerini belirtip, önbellekten döndürülen bir nesne için izin verilen en düşük yeniliği belirtmek için bir ikinci değeri belirtin:</span><span class="sxs-lookup"><span data-stu-id="0f6c5-114">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

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

<span data-ttu-id="0f6c5-115">Aşağıdaki çağrı için:</span><span class="sxs-lookup"><span data-stu-id="0f6c5-115">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="0f6c5-116">Çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="0f6c5-116">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f6c5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f6c5-117">See also</span></span>

- [<span data-ttu-id="0f6c5-118">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="0f6c5-118">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="0f6c5-119">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="0f6c5-119">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="0f6c5-120">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="0f6c5-120">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="0f6c5-121">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="0f6c5-121">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="0f6c5-122">\<requestCaching> Öğesi (ağ ayarları)</span><span class="sxs-lookup"><span data-stu-id="0f6c5-122">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
