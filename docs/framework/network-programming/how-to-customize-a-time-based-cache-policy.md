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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme

Zaman tabanlı önbellek ilkesi oluştururken, maksimum yaş, minimum tazelik, maksimum bayatlık veya önbellek eşitleme tarihi için değerler belirterek önbelleğe alma davranışını özelleştirebilirsiniz. Nesne, <xref:System.Net.Cache.HttpRequestCachePolicy> bu değerlerin geçerli birleşimlerini belirtmenize olanak tanıyan birkaç oluşturucu sağlar.

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Önbellek eşitleme tarihi kullanan zaman tabanlı önbellek ilkesi oluşturmak için

Bir <xref:System.DateTime> nesneyi <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçirerek önbellek eşitleme tarihini kullanan zaman tabanlı önbellek ilkesi oluşturun:

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

Çıkış aşağıdakine benzer:

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Minimum tazeliğe dayalı zaman tabanlı bir önbellek ilkesi oluşturmak için

Parametre değeri <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> olarak belirterek ve nesneyi <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçirerek minimum tazeliğe <xref:System.TimeSpan> dayalı zaman tabanlı bir önbellek ilkesi oluşturun: `cacheAgeControl`

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

Aşağıdaki çağırma için:

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

Çıkış şöyle olur:

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Minimum tazelik ve maksimum yaşa dayalı zamantabanlı bir önbellek ilkesi oluşturmak için

Parametre değeri olarak belirterek ve iki <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> <xref:System.TimeSpan> nesneyi <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçirerek, biri kaynaklar için maksimum yaşı belirtmek ve önbellekten döndürülen bir nesne için izin verilen minimum tazeliği belirtmek için ikinci olarak, minimum tazelik ve maksimum yaşa dayalı zaman tabanlı bir önbellek ilkesi oluşturun: `cacheAgeControl`

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

Aşağıdaki çağırma için:
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Çıkış şöyle olur:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
