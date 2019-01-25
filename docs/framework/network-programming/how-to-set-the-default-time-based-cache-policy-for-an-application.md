---
title: 'Nasıl yapılır: Uygulama için varsayılan saat temelli önbellek İlkesi ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: d40b0ffbe514429ed24eaa5d0c2ce2d52c80d37d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608959"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Nasıl yapılır: Uygulama için varsayılan saat temelli önbellek İlkesi ayarlama
Önbelleğe alınmış kaynak gönderilen üst bilgiler ve 13 ve RFC 2616, kullanılabilir 14 bölümlerde tanımlanan önbellek davranışı tarafından tanımlanan önbellek davranışı bir uygulamanın varsayılan saat temelli önbellek ilkesini sağlayan [Internet Engineering Task Force () IETF)](https://www.ietf.org/) Web sitesi. Bu, çoğu uygulama için uygun önbellek davranıştır.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Bir uygulama için varsayılan otomatik İlkesi ayarlama  
  
1.  Varsayılan zaman tabanlı ilke nesnesi oluşturun.  
  
2.  Uygulama etki alanı için varsayılan olarak ilkesi ayarlayın.  
  
## <a name="example"></a>Örnek  
 Bu bölümdeki iki örneği aynı ilkeler üretir.  
  
 Aşağıdaki örnek, zamana bağlı bir varsayılan ilke oluşturur ve uygulama etki alanı için varsayılan olarak ayarlar.  
  
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
  
 Varsayılan saat temelli önbellek İlkesi kullanarak da oluşturabilirsiniz <xref:System.Net.Cache.RequestCachePolicy> aşağıdaki örnekte gösterildiği gibi sınıf:  
  
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
- [Ağ Uygulamaları için Önbellek Yönetimi](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Önbellek İlkesi](../../../docs/framework/network-programming/cache-policy.md)
- [Konum Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Saat Temelli Önbellek İlkeleri](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching > öğesi (ağ ayarları)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
