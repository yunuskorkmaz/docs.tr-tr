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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Nasıl yapılır: zaman tabanlı önbellek ilkesini özelleştirme

Zaman tabanlı önbellek ilkesi oluştururken, en yüksek yaş, en düşük yenilik, en yüksek eskime veya önbellek eşitleme tarihi değerlerini belirterek önbelleğe alma davranışını özelleştirebilirsiniz. <xref:System.Net.Cache.HttpRequestCachePolicy> nesnesi, bu değerlerin geçerli birleşimlerini belirtmenize izin veren çeşitli oluşturucular sağlar.

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturmak için

Bir <xref:System.DateTime> nesnesini <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusuna geçirerek önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturun:

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

Çıktı aşağıdakine benzer:

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>En düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için

`cacheAgeControl` parametresi değeri olarak <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> belirterek ve <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusuna bir <xref:System.TimeSpan> nesnesi geçirerek en düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturun:

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

Aşağıdaki çağrı için:

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

Çıktı:

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>En düşük yeniliği ve en yüksek kullanım süresini temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için

`cacheAgeControl` parametresi değeri olarak <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> belirtip en yüksek yaşına dayalı bir zaman tabanlı önbellek ilkesi oluşturun ve <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusuna iki <xref:System.TimeSpan> nesnesi geçirerek, biri kaynaklar için maksimum yaş değerini ve ikincisi önbellekten döndürülen bir nesne için izin verilen en düşük yeniliği belirtin:

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

Aşağıdaki çağrı için:
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Çıktı:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching > öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
