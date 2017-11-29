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
ms.openlocfilehash: 9897bbfff542bf708f8fbbc1ac29f7688a1590ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-serialization"></a><span data-ttu-id="464d8-102">Güvenlik ve Serileştirme</span><span class="sxs-lookup"><span data-stu-id="464d8-102">Security and Serialization</span></span>
<span data-ttu-id="464d8-103">Seri hale getirme bakın veya aksi durumda erişilemez olacak nesne örnek verileri değiştirmek başka bir kod izin verebilir, özel bir izni serileştirme gerçekleştirme kodu gereklidir çünkü: <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> bayrağı belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="464d8-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="464d8-104">Varsayılan ilkesi altında için Internet indirilen bu izni verilmez veya intranet kodu; yalnızca yerel bilgisayarda kod bu izin verilir.</span><span class="sxs-lookup"><span data-stu-id="464d8-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="464d8-105">Normalde, bir nesne örneğinin tüm alanlar veri örneği için seri duruma getirilmiş verilerde temsil edilen anlamı serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="464d8-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="464d8-106">Hangi veri değerleri, üye erişilebilirliğini bağımsız belirlemek için kullanılacak biçimi çevirebilir kodunu mümkündür.</span><span class="sxs-lookup"><span data-stu-id="464d8-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="464d8-107">Benzer şekilde, seri durumdan çıkarma serileştirilmiş gösteriminden verileri ayıklar ve nesne durumu doğrudan yeniden erişilebilirlik kuralları bağımsız olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="464d8-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="464d8-108">Güvenlik açısından duyarlı verileri içeren herhangi bir nesne nonserializable, mümkünse yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="464d8-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="464d8-109">Hassas verileri nonserializable tutun belirli alanları yapmak Serileştirilebilir olmalıdır, deneyin.</span><span class="sxs-lookup"><span data-stu-id="464d8-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="464d8-110">Bu yapılamaz, seri hale getirmek ve kötü amaçlı kod bu izni alabilirsiniz emin olmak için izni olan herhangi bir kodu bu verilerin açığa çıkardığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="464d8-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="464d8-111"><xref:System.Runtime.Serialization.ISerializable> Arabirimi, yalnızca serileştirme altyapısı tarafından kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="464d8-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="464d8-112">Ancak, korumasız, olası hassas bilgileri serbest bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="464d8-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="464d8-113">Uygulayarak özel serileştirme sağlarsanız, **ISerializable**, aşağıdaki önlemleri almanız emin olun:</span><span class="sxs-lookup"><span data-stu-id="464d8-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
-   <span data-ttu-id="464d8-114"><xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Yöntemi açıkça güvenli yoğun ya da **SecurityPermission** ile **SerializationFormatter** göre yaparak emin, ya da belirtilen izni yok duyarlı bilgi yöntemi çıkışıyla yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="464d8-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="464d8-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="464d8-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="464d8-116">Serileştirme için kullanılan özel Oluşturucu de kapsamlı giriş doğrulaması yapmalıdır ve korumalı veya kötü amaçlı kod tarafından kötüye karşı korunmasına yardımcı olmak için özel olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="464d8-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="464d8-117">Aynı güvenlik denetimleri ve başka bir yöntemle açıkça sınıfı oluşturma veya Fabrika çeşit üzerinden dolaylı olarak oluşturma gibi herhangi bir tür sınıfının bir örneği elde etmek için gereken izinler uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="464d8-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464d8-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="464d8-118">See Also</span></span>  
 [<span data-ttu-id="464d8-119">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="464d8-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
