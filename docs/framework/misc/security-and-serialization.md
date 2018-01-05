---
title: "Güvenlik ve Serileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a870834b86f1ed99181614278a7381932a18ac8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-serialization"></a>Güvenlik ve Serileştirme
Seri hale getirme bakın veya aksi durumda erişilemez olacak nesne örnek verileri değiştirmek başka bir kod izin verebilir, özel bir izni serileştirme gerçekleştirme kodu gereklidir çünkü: <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> bayrağı belirtilmiş. Varsayılan ilkesi altında için Internet indirilen bu izni verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir.  
  
 Normalde, bir nesne örneğinin tüm alanlar veri örneği için seri duruma getirilmiş verilerde temsil edilen anlamı serileştirilir. Hangi veri değerleri, üye erişilebilirliğini bağımsız belirlemek için kullanılacak biçimi çevirebilir kodunu mümkündür. Benzer şekilde, seri durumdan çıkarma serileştirilmiş gösteriminden verileri ayıklar ve nesne durumu doğrudan yeniden erişilebilirlik kuralları bağımsız olarak ayarlar.  
  
 Güvenlik açısından duyarlı verileri içeren herhangi bir nesne nonserializable, mümkünse yapılmalıdır. Hassas verileri nonserializable tutun belirli alanları yapmak Serileştirilebilir olmalıdır, deneyin. Bu yapılamaz, seri hale getirmek ve kötü amaçlı kod bu izni alabilirsiniz emin olmak için izni olan herhangi bir kodu bu verilerin açığa çıkardığını unutmayın.  
  
 <xref:System.Runtime.Serialization.ISerializable> Arabirimi, yalnızca serileştirme altyapısı tarafından kullanılmak üzere tasarlanmıştır. Ancak, korumasız, olası hassas bilgileri serbest bırakabilirsiniz. Uygulayarak özel serileştirme sağlarsanız, **ISerializable**, aşağıdaki önlemleri almanız emin olun:  
  
-   <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Yöntemi açıkça güvenli yoğun ya da **SecurityPermission** ile **SerializationFormatter** göre yaparak emin, ya da belirtilen izni yok duyarlı bilgi yöntemi çıkışıyla yayımlanır. Örneğin:  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
-   Serileştirme için kullanılan özel Oluşturucu de kapsamlı giriş doğrulaması yapmalıdır ve korumalı veya kötü amaçlı kod tarafından kötüye karşı korunmasına yardımcı olmak için özel olması gerekir. Aynı güvenlik denetimleri ve başka bir yöntemle açıkça sınıfı oluşturma veya Fabrika çeşit üzerinden dolaylı olarak oluşturma gibi herhangi bir tür sınıfının bir örneği elde etmek için gereken izinler uygulamalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
