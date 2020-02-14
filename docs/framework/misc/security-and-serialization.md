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
ms.openlocfilehash: cb0ba120eeb57788c0525d45b714ad8edd2c39ed
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216970"
---
# <a name="security-and-serialization"></a><span data-ttu-id="54be0-102">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="54be0-102">Security and Serialization</span></span>
<span data-ttu-id="54be0-103">Serileştirme diğer kodun başka bir şekilde erişilemeyen nesne örneği verilerini görmesine veya değiştirmesine izin abileceğinden, kod serileştirme: <xref:System.Security.Permissions.SecurityPermission> belirtilen <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> bayrağıyla özel bir izin gerekir.</span><span class="sxs-lookup"><span data-stu-id="54be0-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="54be0-104">Varsayılan ilke altında, bu izin Internet 'Ten indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="54be0-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="54be0-105">Normalde, bir nesne örneğinin tüm alanları serileştirilir ve bu, verilerin örnek için seri hale getirilmiş verilerde temsil edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="54be0-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="54be0-106">Veri değerlerinin ne olduğunu, üyenin erişilebilirliğiyle bağımsız olarak belirlemek için biçimi yorumlayabilen kod mümkündür.</span><span class="sxs-lookup"><span data-stu-id="54be0-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="54be0-107">Benzer şekilde, seri durumdan çıkarma, verileri serileştirilmiş gösterimden ayıklar ve doğrudan, nesne durumunu erişilebilirlik kurallarından bağımsız olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="54be0-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="54be0-108">Güvenlik duyarlı veriler içerebilen herhangi bir nesne, mümkünse seri hale getirilebilir olmayan bir şekilde yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54be0-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="54be0-109">Seri hale getirilebilir olması gerekiyorsa, gizli verileri tutan, seri hale getirilebilen belirli alanları yapmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="54be0-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="54be0-110">Bu işlem yapılabiliyorsa, bu verilerin serileştirme izni olan herhangi bir koda sunulamadığını ve kötü amaçlı bir kodun bu izni alamazsanız emin olun.</span><span class="sxs-lookup"><span data-stu-id="54be0-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="54be0-111"><xref:System.Runtime.Serialization.ISerializable> arabirimi yalnızca serileştirme altyapısı tarafından kullanılmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="54be0-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="54be0-112">Ancak korumasız ise, hassas bilgileri serbest bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="54be0-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="54be0-113">**ISerializable**uygulayarak özel serileştirme sağlarsanız, aşağıdaki önlemleri aldığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="54be0-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="54be0-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> yöntemi, **SerializationFormatter** Iznine sahip **SecurityPermission** 'ı belirtilen veya yöntem çıkışıyla hiçbir hassas bilgi yayınlanmadan emin olarak açıkça güvenli hale getirmelidir.</span><span class="sxs-lookup"><span data-stu-id="54be0-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="54be0-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="54be0-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="54be0-116">Serileştirme için kullanılan özel Oluşturucu ayrıca tam giriş doğrulaması gerçekleştirmeyi ve kötü amaçlı kodun kötüye kullanılmasına karşı korumaya yardımcı olmak için korumalı veya özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="54be0-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="54be0-117">Bu, sınıfın açıkça oluşturulması veya bir tür fabrika aracılığıyla dolaylı olarak oluşturulması gibi bazı yollarla bu tür bir sınıfın bir örneğini almak için gereken güvenlik denetimlerini ve izinlerini zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="54be0-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54be0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54be0-118">See also</span></span>

- [<span data-ttu-id="54be0-119">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="54be0-119">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
