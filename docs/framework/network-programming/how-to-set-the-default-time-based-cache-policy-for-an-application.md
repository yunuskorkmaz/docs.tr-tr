---
title: "Nasıl yapılır: bir uygulama için varsayılan zaman tabanlı önbellek İlkesi ayarlama"
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
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d5166090a0682b71f74565e666c96ddadb7c6c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Nasıl yapılır: bir uygulama için varsayılan zaman tabanlı önbellek İlkesi ayarlama
Önbelleğe alınan kaynakla gönderilen üstbilgiler ve 13 ve RFC 2616, adresinde 14 bölümlerde tanımlanan önbellek davranışını tarafından tanımlanan önbellek davranışını sağlamak bir uygulamanın varsayılan zamana dayalı önbellek İlkesi sağlayan [http://www.ietf.org](http://www.ietf.org/). Çoğu uygulama için uygun önbellek davranış budur.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Bir uygulama için varsayılan otomatik ilkesini ayarlamak için  
  
1.  Varsayılan zaman tabanlı ilke nesnesi oluşturun.  
  
2.  Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.  
  
## <a name="example"></a>Örnek  
 Bu bölümdeki iki örnekleri aynı ilkeler üretir.  
  
 Aşağıdaki örnekte, varsayılan zaman tabanlı bir ilke oluşturulur ve uygulama etki alanı için varsayılan olarak ayarlar.  
  
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
  
 Varsayılan zamana dayalı önbellek İlkesi kullanarak da oluşturabilirsiniz <xref:System.Net.Cache.RequestCachePolicy> sınıfı aşağıdaki örnekte gösterildiği gibi:  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)  
 [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
