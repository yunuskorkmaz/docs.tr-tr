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
ms.openlocfilehash: e9398beee7051d88867600b79c615356c2d4cc28
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241700"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Nasıl yapılır: Uygulama için Varsayılan Saat Temelli Önbellek İlkesi Ayarlama

Varsayılan zaman tabanlı önbellek ilkesi, bir uygulamanın önbelleğe alınmış kaynakla gönderilen üstbilgiler ve [Internet Mühendisliği görev zorlaması (IETF)](https://www.ietf.org/) Web sitesinde kullanılabilir olan 2616 13. bölümlerde tanımlanan önbellek davranışı ile tanımlanan önbellek davranışını kullanmasına izin verir. Bu, çoğu uygulama için uygun önbellek davranışıdır.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Bir uygulamanın varsayılan otomatik ilkesini ayarlamak için  
  
1. Varsayılan bir zamana dayalı ilke nesnesi oluşturun.  
  
2. İlke nesnesini, uygulama etki alanı için varsayılan olarak ayarlayın.  
  
## <a name="example"></a>Örnek  

 Bu bölümdeki iki örnek özdeş ilkeler üretir.  
  
 Aşağıdaki örnek, varsayılan bir zamana dayalı ilke oluşturur ve bunu uygulama etki alanı için varsayılan olarak ayarlar.  
  
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
  
 Aşağıdaki örnekte gösterildiği gibi sınıfını kullanarak varsayılan zaman tabanlı önbellek ilkesi de oluşturabilirsiniz <xref:System.Net.Cache.RequestCachePolicy> :  
  
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
- [\<requestCaching> Öğesi (ağ ayarları)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
