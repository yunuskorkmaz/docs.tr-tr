---
title: Güvenlik ve Serileştirme
description: Güvenlik ve serileştirme hakkında bilgi edinin. Nesne örneği verilerini görmek veya değiştirmek için belirtilen SerializationFormatter bayrağıyla SecurityPermission kullanın.
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
ms.openlocfilehash: 393e334e8165f55812681848070929bdfb03a2a5
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855692"
---
# <a name="security-and-serialization"></a><span data-ttu-id="78c23-104">Güvenlik ve serileştirme</span><span class="sxs-lookup"><span data-stu-id="78c23-104">Security and serialization</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="78c23-105">Serileştirme diğer kodun başka bir şekilde erişilemeyen nesne örneği verilerini görmesine veya değiştirmesine izin abileceğinden, kod serileştirme: belirtilen bayrağıyla özel bir izin gerekir <xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> .</span><span class="sxs-lookup"><span data-stu-id="78c23-105">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="78c23-106">Varsayılan ilke altında, bu izin Internet 'Ten indirilen veya intranet koduna verilmez; yalnızca yerel bilgisayardaki koda bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="78c23-106">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="78c23-107">Normalde, bir nesne örneğinin tüm alanları serileştirilir ve bu, verilerin örnek için seri hale getirilmiş verilerde temsil edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="78c23-107">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="78c23-108">Veri değerlerinin ne olduğunu, üyenin erişilebilirliğiyle bağımsız olarak belirlemek için biçimi yorumlayabilen kod mümkündür.</span><span class="sxs-lookup"><span data-stu-id="78c23-108">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="78c23-109">Benzer şekilde, seri durumdan çıkarma, verileri serileştirilmiş gösterimden ayıklar ve doğrudan, nesne durumunu erişilebilirlik kurallarından bağımsız olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="78c23-109">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="78c23-110">Güvenlik duyarlı veriler içerebilen herhangi bir nesne, mümkünse seri hale getirilebilir olmayan bir şekilde yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78c23-110">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="78c23-111">Seri hale getirilebilir olması gerekiyorsa, gizli verileri tutan, seri hale getirilebilen belirli alanları yapmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="78c23-111">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="78c23-112">Bu alanlar seri hale getirilebilir değilse, hassas veriler serileştirme iznine sahip herhangi bir koda sunulur.</span><span class="sxs-lookup"><span data-stu-id="78c23-112">If those fields cannot be made nonserializable, the sensitive data will be exposed to any code that has permission to serialize.</span></span> <span data-ttu-id="78c23-113">Kötü amaçlı bir kodun bu izni alamıyor olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="78c23-113">Make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="78c23-114"><xref:System.Runtime.Serialization.ISerializable>Arabirim yalnızca serileştirme altyapısı tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="78c23-114">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="78c23-115">Ancak korumasız ise, hassas bilgileri serbest bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="78c23-115">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="78c23-116">**ISerializable**uygulayarak özel serileştirme sağlarsanız, aşağıdaki önlemleri aldığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="78c23-116">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="78c23-117"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>Yöntemi, **SerializationFormatter** Iznine sahip **SecurityPermission** 'ı belirtilen veya yöntem çıkışıyla hiçbir hassas bilgi yayınlanmadan emin olarak açıkça güvenli hale getirmelidir.</span><span class="sxs-lookup"><span data-stu-id="78c23-117">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="78c23-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="78c23-118">For example:</span></span>  
  
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
  
- <span data-ttu-id="78c23-119">Serileştirme için kullanılan özel Oluşturucu ayrıca tam giriş doğrulaması gerçekleştirmeyi ve kötü amaçlı kodun kötüye kullanılmasına karşı korumaya yardımcı olmak için korumalı veya özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78c23-119">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="78c23-120">Bu, sınıfın açıkça oluşturulması veya bir tür fabrika aracılığıyla dolaylı olarak oluşturulması gibi bazı yollarla bu tür bir sınıfın bir örneğini almak için gereken güvenlik denetimlerini ve izinlerini zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="78c23-120">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c23-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c23-121">See also</span></span>

- [<span data-ttu-id="78c23-122">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="78c23-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
