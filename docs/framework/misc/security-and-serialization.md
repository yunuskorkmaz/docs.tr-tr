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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4deadc175bd4cc3635a6c8d8d8b80100b5a9938
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151794"
---
# <a name="security-and-serialization"></a><span data-ttu-id="aed3e-102">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="aed3e-102">Security and Serialization</span></span>
<span data-ttu-id="aed3e-103">Serileştirme bakın veya erişilemez Aksi durumda olacak nesne örneği verileri değiştirmek başka bir kod izin vermek için özel bir izin serileştirme gerçekleştiren kod gereklidir: <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> bayrağı belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="aed3e-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="aed3e-104">Varsayılan ilkesi altında çok Internet karşıdan bu izin verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="aed3e-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="aed3e-105">Normalde, bir nesne örneğinin tüm alanlar veri örneği için seri duruma getirilmiş verilerde temsil edilen anlamı serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="aed3e-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="aed3e-106">Veri değerleri, üyenin erişilebilirliğini bağımsız nelerdir belirlemek için biçim yorumlayabilir kodunu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="aed3e-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="aed3e-107">Benzer şekilde, seri durumundan çıkarma serileştirilmiş temsilinden verileri ayıklayan ve nesne durumu doğrudan yeniden erişilebilirlik kuralları bağımsız olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aed3e-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="aed3e-108">Güvenlik açısından duyarlı verileri içerebilen herhangi bir nesne nonserializable, mümkünse yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aed3e-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="aed3e-109">Hassas verileri nonserializable tutun belirli alanlar seri hale getirilebilir olması gerekir, deneyin.</span><span class="sxs-lookup"><span data-stu-id="aed3e-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="aed3e-110">Bu yapılamaz, bu verileri seri hale getirmek ve kötü amaçlı bir kodun bu izin alabilirsiniz emin olmak için izni olan herhangi bir kod sunulan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="aed3e-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="aed3e-111"><xref:System.Runtime.Serialization.ISerializable> Arabirimi, yalnızca seri hale getirme altyapısı tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aed3e-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="aed3e-112">Ancak, korumasız, potansiyel olarak hassas bilgileri serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aed3e-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="aed3e-113">Özel serileştirme uygulayarak sağlarsanız **ISerializable**, aşağıdaki önlemleri dikkate aldığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="aed3e-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
-   <span data-ttu-id="aed3e-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Yöntemi açıkça güvenli yoğun ya da **SecurityPermission** ile **SerializationFormatter** göre yaparak emin olan ya da belirtilen izni yok duyarlı bilgi yöntemi çıkış ile serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="aed3e-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="aed3e-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="aed3e-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="aed3e-116">Serileştirme için kullanılan özel bir oluşturucu ayrıca kapsamlı giriş doğrulaması gerçekleştirmeniz ve kötü amaçlı kod tarafından kötüye karşı korumaya yardımcı olmak için özel veya korumalı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aed3e-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="aed3e-117">Aynı güvenlik denetimleri ve açıkça sınıfı oluşturma veya Fabrika tür üzerinden dolaylı olarak oluşturma gibi diğer araçları, böyle bir sınıfın bir örneği elde etmek için gerekli izinler uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aed3e-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed3e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aed3e-118">See also</span></span>

- [<span data-ttu-id="aed3e-119">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aed3e-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
