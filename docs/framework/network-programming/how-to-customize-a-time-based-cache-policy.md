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
# <a name="how-to-customize-a-time-based-cache-policy"></a>Nasıl yapılır: Saat Temelli Önbellek İlkesini Özelleştirme
Zaman tabanlı önbellek ilkesi oluştururken, en yüksek yaş, en düşük yenilik, en yüksek eskime veya önbellek eşitleme tarihi değerlerini belirterek önbelleğe alma davranışını özelleştirebilirsiniz. Nesnesi <xref:System.Net.Cache.HttpRequestCachePolicy> , bu değerlerin geçerli birleşimlerini belirtmenize izin veren çeşitli oluşturucular sağlar.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturmak için  
  
- <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucuya bir <xref:System.DateTime> nesne geçirerek önbellek eşitleme tarihi kullanan zaman tabanlı bir önbellek ilkesi oluşturun.  
  
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
  
 Çıktı aşağıdakine benzer:  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>En düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için  
  
- Parametre değeri <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> <xref:System.TimeSpan> olarak belirterek ve <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya bir nesne geçirerek en düşük yeniliği temel alan zaman tabanlı bir önbellek ilkesi oluşturun. `cacheAgeControl`  
  
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
  
 Aşağıdaki çağrı için:  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 Çıktı:
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>En düşük yeniliği ve en yüksek kullanım süresini temel alan zaman tabanlı bir önbellek ilkesi oluşturmak için  
  
- Parametre değeri <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> <xref:System.TimeSpan> olarak belirtip en yüksek yaş ve maksimum yaş temelinde bir zaman tabanlı önbellek ilkesi oluşturun ve biri için en fazla yaşı belirtmek üzere iki nesne <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucuya geçiş yapın `cacheAgeControl` önbellekten döndürülen bir nesne için izin verilen en düşük yeniliği belirlemek için kaynak ve saniye.  
  
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
  
 Aşağıdaki çağrı için:  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

Çıktı:
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
