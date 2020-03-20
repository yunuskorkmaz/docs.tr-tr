---
title: Güvenlik ve Serileştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
ms.openlocfilehash: 634388e3920e0b9dbee85aa3ea555471cee604ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181110"
---
# <a name="security-and-serialization"></a>Güvenlik ve Serileştirme
Serileştirme, başka bir kodun erişilemeyen nesne örneği verilerini görmesine veya değiştirmesine izin <xref:System.Security.Permissions.SecurityPermission> verebileceğinden, serileştirme gerçekleştiren kod için özel bir izin gereklidir: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> belirtilen bayrakla. Varsayılan ilke kapsamında, bu izin Internet tarafından indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir.  
  
 Normalde, bir nesne örneğinin tüm alanları seri hale getirilmiştir, bu da verilerin örnek için serileştirilmiş verilerde temsil edildiği anlamına gelir. Üyenin erişilebilirliğinden bağımsız olarak, veri değerlerinin ne olduğunu belirlemek için biçimi yorumlayabilen kod mümkündür. Benzer şekilde, deserialization serileştirilmiş gösterimverileri verileri ayıklar ve yine erişilebilirlik kurallarına bakılmaksızın nesne durumu doğrudan ayarlar.  
  
 Güvenliğe duyarlı veriler içerebilecek herhangi bir nesne, mümkünse seri olarak izlenebilir hale getirilmelidir. Serileştirilebilir olması gerekiyorsa, hassas verileri seri olarak tutamayan belirli alanları yapmaya çalışın. Bu yapılamıyorsa, bu verilerin serileştirme izni olan herhangi bir koda maruz kalacağını unutmayın ve hiçbir kötü amaçlı kodun bu izni alamadığından emin olun.  
  
 Arabirim yalnızca <xref:System.Runtime.Serialization.ISerializable> serileştirme altyapısı tarafından kullanılmak üzere tasarlanmıştır. Ancak, korumasız sayılsa bile, hassas bilgileri serbest bırakabilir. **ISerializable**uygulayarak özel serileştirme sağlarsanız, aşağıdaki önlemleri aldığınızdan emin olun:  
  
- Yöntem, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> **Belirtilen SerializationFormatter** izni ile **SecurityPermission** talep ederek veya yöntem çıktısı ile hassas bilgi serbest bırakıldığından emin olmak tarafından açıkça güvence altına alınmalıdır. Örnek:  
  
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
  
- Serileştirme için kullanılan özel oluşturucu da kapsamlı giriş doğrulama gerçekleştirmeli ve kötü amaçlı kod tarafından kötüye karşı korunmasına yardımcı olmak için korumalı veya özel olmalıdır. Bu tür bir sınıfın bir örneğini başka yollarla elde etmek için gereken aynı güvenlik denetimlerini ve izinlerini, örneğin sınıfı açıkça oluşturma veya dolaylı olarak bir tür fabrika aracılığıyla oluşturma gibi zorlamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
