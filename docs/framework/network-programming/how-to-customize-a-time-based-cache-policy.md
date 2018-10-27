---
title: 'Nasıl yapılır: saat temelli önbellek ilkesini özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a9e0d3197dcba63ef5497613e216a96868a03da
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182456"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Nasıl yapılır: saat temelli önbellek ilkesini özelleştirme
Bir saat temelli önbellek ilkesi oluştururken en uzun geçerlilik süresi, en az eskime, en fazla eskime veya önbellek eşitleme tarih değerleri belirtilerek, önbelleğe alma davranışını özelleştirebilirsiniz. <xref:System.Net.Cache.HttpRequestCachePolicy> Nesnesi, bu değerleri geçerli birleşimleri belirtmek olanak tanıyan birkaç Oluşturucusu sağlar.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Bir önbellek eşitleme tarihi kullanan bir saat temelli önbellek ilkesi oluşturmak için  
  
-   Bir önbellek eşitleme tarihi geçirerek kullanan bir saat temelli önbellek ilkesi oluşturma bir <xref:System.DateTime> nesnesini <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.  
  
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
  
 Çıktı aşağıdakine benzer olacaktır:  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Üzerinde en az eskime dayalı olarak bir saat temelli önbellek ilkesi oluşturmak için  
  
-   Üzerinde en az eskime belirterek temel bir saat temelli önbellek İlkesi <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> olarak `cacheAgeControl` parametre değeri ve geçirme bir <xref:System.TimeSpan> nesnesini <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.  
  
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
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>En az eskime ve en yüksek yaşı dayalı olarak bir saat temelli önbellek ilkesi oluşturmak için  
  
-   En az eskime ve en uzun geçerlilik süresi, belirterek dayalı olarak bir saat temelli önbellek İlkesi <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> olarak `cacheAgeControl` parametre değeri ve iki geçirme <xref:System.TimeSpan> nesneleri için <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusu, en fazla geçerlilik süresini belirtmek için Kaynaklar ve en az eskime belirtmek için ikinci bir önbellekten döndürülen bir nesne için izin verilir.  
  
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
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
