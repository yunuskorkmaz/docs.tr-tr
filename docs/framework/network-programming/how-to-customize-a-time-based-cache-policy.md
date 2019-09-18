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
ms.openlocfilehash: c28c6daf9b873a19291b1636112eae6546412be2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048325"
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

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching > öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
