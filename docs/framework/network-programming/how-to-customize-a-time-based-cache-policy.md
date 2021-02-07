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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme

Zaman tabanlı önbellek ilkesi oluştururken, en yüksek yaş, en düşük yenilik, en yüksek eskime veya önbellek eşitleme tarihi değerlerini belirterek önbelleğe alma davranışını özelleştirebilirsiniz. <xref:System.Net.Cache.HttpRequestCachePolicy>Nesnesi, bu değerlerin geçerli birleşimlerini belirtmenize izin veren çeşitli oluşturucular sağlar.

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturmak için

Oluşturucuya bir nesne geçirerek önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturun <xref:System.DateTime> <xref:System.Net.Cache.HttpRequestCachePolicy> :

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

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>En düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için

<xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> `cacheAgeControl` Parametre değeri olarak belirterek ve oluşturucuya bir nesne geçirerek en düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturun <xref:System.TimeSpan> <xref:System.Net.Cache.HttpRequestCachePolicy> :

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

Çıkış şöyle olur:

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>En düşük yeniliği ve en yüksek kullanım süresini temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için

Parametre değeri olarak belirterek en düşük yeniliği ve maksimum yaşı temel alan zaman tabanlı bir önbellek ilkesi oluşturun <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> `cacheAgeControl` ve iki <xref:System.TimeSpan> nesneyi oluşturucuya geçirerek <xref:System.Net.Cache.HttpRequestCachePolicy> bir tane, kaynak için en yüksek yaş değerini belirtip, önbellekten döndürülen bir nesne için izin verilen en düşük yeniliği belirtmek için bir ikinci değeri belirtin:

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

Çıkış şöyle olur:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
