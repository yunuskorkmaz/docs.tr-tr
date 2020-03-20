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
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040628"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="9c4ec-102">Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9c4ec-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="9c4ec-103">Zaman tabanlı önbellek ilkesi oluştururken, maksimum yaş, minimum tazelik, maksimum bayatlık veya önbellek eşitleme tarihi için değerler belirterek önbelleğe alma davranışını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c4ec-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="9c4ec-104">Nesne, <xref:System.Net.Cache.HttpRequestCachePolicy> bu değerlerin geçerli birleşimlerini belirtmenize olanak tanıyan birkaç oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c4ec-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="9c4ec-105">Önbellek eşitleme tarihi kullanan zaman tabanlı önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c4ec-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="9c4ec-106">Bir <xref:System.DateTime> nesneyi <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçirerek önbellek eşitleme tarihini kullanan zaman tabanlı önbellek ilkesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9c4ec-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="9c4ec-107">Çıkış aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="9c4ec-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="9c4ec-108">Minimum tazeliğe dayalı zaman tabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c4ec-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="9c4ec-109">Parametre değeri <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> olarak belirterek ve nesneyi <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçirerek minimum tazeliğe <xref:System.TimeSpan> dayalı zaman tabanlı bir önbellek ilkesi oluşturun: `cacheAgeControl`</span><span class="sxs-lookup"><span data-stu-id="9c4ec-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

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

<span data-ttu-id="9c4ec-110">Aşağıdaki çağırma için:</span><span class="sxs-lookup"><span data-stu-id="9c4ec-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="9c4ec-111">Çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="9c4ec-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="9c4ec-112">Minimum tazelik ve maksimum yaşa dayalı zamantabanlı bir önbellek ilkesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9c4ec-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="9c4ec-113">Parametre değeri olarak belirterek ve iki <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> <xref:System.TimeSpan> nesneyi <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçirerek, biri kaynaklar için maksimum yaşı belirtmek ve önbellekten döndürülen bir nesne için izin verilen minimum tazeliği belirtmek için ikinci olarak, minimum tazelik ve maksimum yaşa dayalı zaman tabanlı bir önbellek ilkesi oluşturun: `cacheAgeControl`</span><span class="sxs-lookup"><span data-stu-id="9c4ec-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

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

<span data-ttu-id="9c4ec-114">Aşağıdaki çağırma için:</span><span class="sxs-lookup"><span data-stu-id="9c4ec-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="9c4ec-115">Çıkış şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="9c4ec-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c4ec-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c4ec-116">See also</span></span>

- [<span data-ttu-id="9c4ec-117">Ağ Uygulamaları için Önbellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="9c4ec-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="9c4ec-118">Önbellek İlkesi</span><span class="sxs-lookup"><span data-stu-id="9c4ec-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="9c4ec-119">Konum Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="9c4ec-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="9c4ec-120">Saat Temelli Önbellek İlkeleri</span><span class="sxs-lookup"><span data-stu-id="9c4ec-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="9c4ec-121">\<requestCaching> Elemanı (Ağ Ayarları)</span><span class="sxs-lookup"><span data-stu-id="9c4ec-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
