---
title: 'Nasıl yapılır: Uygulama için Varsayılan Saat Temelli Önbellek İlkesi Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 0aaa26f67ef1ef191060e682690fa14de328b812
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048101"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Nasıl yapılır: Uygulama için Varsayılan Saat Temelli Önbellek İlkesi Ayarlama
Varsayılan zaman tabanlı önbellek ilkesi, önbelleğe alınmış kaynakla önbelleğe alınmış kaynak ve [Internet Engineering Task Force (IETF)](https://www.ietf.org/) web sitesinde bulunan RFC 2616'nın 13 ve 14 bölümlerinde tanımlanan önbellek davranışıyla bir uygulamanın önbellek davranışıtarafından tanımlanmasını sağlar. Bu, çoğu uygulama için uygun önbellek davranışıdır.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Bir uygulama için varsayılan otomatik ilkeyi ayarlamak için  
  
1. Varsayılan zaman tabanlı ilke nesnesi oluşturun.  
  
2. İlke nesnesini uygulama etki alanı için varsayılan olarak ayarlayın.  
  
## <a name="example"></a>Örnek  
 Bu bölümdeki iki örnek aynı ilkeleri üretir.  
  
 Aşağıdaki örnekte varsayılan zaman tabanlı bir ilke oluşturulur ve uygulama etki alanı için varsayılan olarak ayarlar.  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 Aşağıdaki örnekte gösterildiği gibi <xref:System.Net.Cache.RequestCachePolicy> sınıfı kullanarak varsayılan zaman tabanlı önbellek ilkesini de oluşturabilirsiniz:  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Uygulamaları için Önbellek Yönetimi](cache-management-for-network-applications.md)
- [Önbellek İlkesi](cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](time-based-cache-policies.md)
- [\<requestCaching> Elemanı (Ağ Ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
