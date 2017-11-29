---
title: "Nasıl yapılır: bir zamana dayalı önbellek İlkesi özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 58fa5c71bc459b65d35f9a59bdddccab9a0f5e56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Nasıl yapılır: bir zamana dayalı önbellek İlkesi özelleştirme
Bir zamana dayalı önbellek ilkesi oluştururken, en uzun geçerlilik süresi, minimum yenilik, en fazla eskime durumu veya önbellek eşitleme tarihi için değerleri belirtilerek önbelleğe alma davranışını özelleştirebilirsiniz. <xref:System.Net.Cache.HttpRequestCachePolicy> Nesnesi, bu değerlerin geçerli birleşimleri belirtmenize olanak veren birkaç Oluşturucusu sağlar.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Bir önbellek eşitleme tarihi kullanan bir zamana dayalı önbellek ilkesi oluşturmak için  
  
-   Bir önbellek eşitleme tarihi geçirerek kullanan bir önbellek zaman tabanlı ilke oluşturmak bir <xref:System.DateTime> nesnesine <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.  
  
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
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Üzerinde minimum yenilik dayalı bir zamana dayalı önbellek ilkesi oluşturmak için  
  
-   Üzerinde minimum yenilik belirterek dayalı bir zamana dayalı önbellek ilkesi oluşturmak <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> olarak `cacheAgeControl` parametre değeri ve geçirerek bir <xref:System.TimeSpan> nesnesine <xref:System.Net.Cache.HttpRequestCachePolicy> Oluşturucusu.  
  
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
  
 Aşağıdaki çağırma için:  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Minimum yenilik ve en uzun geçerlilik süresi dayalı bir zamana dayalı önbellek ilkesi oluşturmak için  
  
-   Belirterek minimum yenilik ve en uzun geçerlilik süresi dayanan bir zamana dayalı önbellek ilkesi oluşturmak <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> olarak `cacheAgeControl` parametre değeri ile iki geçirme <xref:System.TimeSpan> nesneleri <xref:System.Net.Cache.HttpRequestCachePolicy> oluşturucusu, en fazla geçerlilik belirtmek için kaynakları ve minimum yenilik belirtmek için ikinci bir önbellekten döndürülen bir nesne için izin verilir.  
  
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
  
 Aşağıdaki çağırma için:  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ uygulamaları için önbellek yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum temelli önbellek ilkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Önbellek zaman tabanlı ilkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
