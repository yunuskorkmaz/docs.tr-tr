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
# <a name="security-and-serialization"></a><span data-ttu-id="aeaf6-102">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="aeaf6-102">Security and Serialization</span></span>
<span data-ttu-id="aeaf6-103">Serileştirme, başka bir kodun erişilemeyen nesne örneği verilerini görmesine veya değiştirmesine izin <xref:System.Security.Permissions.SecurityPermission> verebileceğinden, serileştirme gerçekleştiren kod için özel bir izin gereklidir: <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> belirtilen bayrakla.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="aeaf6-104">Varsayılan ilke kapsamında, bu izin Internet tarafından indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="aeaf6-105">Normalde, bir nesne örneğinin tüm alanları seri hale getirilmiştir, bu da verilerin örnek için serileştirilmiş verilerde temsil edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="aeaf6-106">Üyenin erişilebilirliğinden bağımsız olarak, veri değerlerinin ne olduğunu belirlemek için biçimi yorumlayabilen kod mümkündür.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="aeaf6-107">Benzer şekilde, deserialization serileştirilmiş gösterimverileri verileri ayıklar ve yine erişilebilirlik kurallarına bakılmaksızın nesne durumu doğrudan ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="aeaf6-108">Güvenliğe duyarlı veriler içerebilecek herhangi bir nesne, mümkünse seri olarak izlenebilir hale getirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="aeaf6-109">Serileştirilebilir olması gerekiyorsa, hassas verileri seri olarak tutamayan belirli alanları yapmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="aeaf6-110">Bu yapılamıyorsa, bu verilerin serileştirme izni olan herhangi bir koda maruz kalacağını unutmayın ve hiçbir kötü amaçlı kodun bu izni alamadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="aeaf6-111">Arabirim yalnızca <xref:System.Runtime.Serialization.ISerializable> serileştirme altyapısı tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="aeaf6-112">Ancak, korumasız sayılsa bile, hassas bilgileri serbest bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="aeaf6-113">**ISerializable**uygulayarak özel serileştirme sağlarsanız, aşağıdaki önlemleri aldığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="aeaf6-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="aeaf6-114">Yöntem, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> **Belirtilen SerializationFormatter** izni ile **SecurityPermission** talep ederek veya yöntem çıktısı ile hassas bilgi serbest bırakıldığından emin olmak tarafından açıkça güvence altına alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="aeaf6-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="aeaf6-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="aeaf6-116">Serileştirme için kullanılan özel oluşturucu da kapsamlı giriş doğrulama gerçekleştirmeli ve kötü amaçlı kod tarafından kötüye karşı korunmasına yardımcı olmak için korumalı veya özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="aeaf6-117">Bu tür bir sınıfın bir örneğini başka yollarla elde etmek için gereken aynı güvenlik denetimlerini ve izinlerini, örneğin sınıfı açıkça oluşturma veya dolaylı olarak bir tür fabrika aracılığıyla oluşturma gibi zorlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeaf6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeaf6-118">See also</span></span>

- [<span data-ttu-id="aeaf6-119">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aeaf6-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
