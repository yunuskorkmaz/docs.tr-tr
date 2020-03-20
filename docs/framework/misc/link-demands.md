---
title: Bağlantı Talepleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181169"
---
# <a name="link-demands"></a><span data-ttu-id="c2261-102">Bağlantı Talepleri</span><span class="sxs-lookup"><span data-stu-id="c2261-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="c2261-103">Bağlantı talebi, tam zamanında derleme sırasında bir güvenlik denetimine neden olur ve yalnızca kodunuzun hemen çağrı montajını denetler.</span><span class="sxs-lookup"><span data-stu-id="c2261-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="c2261-104">Bağlama, kodunuz işlev işaretçisi başvuruları ve yöntem çağrıları da dahil olmak üzere bir tür başvurusuna bağlandığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="c2261-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="c2261-105">Arama derlemesi kodunuza bağlanmak için yeterli izine sahip değilse, bağlantıya izin verilmez ve kod yüklenip çalıştırıldığında çalışma zamanı özel durumu atılır.</span><span class="sxs-lookup"><span data-stu-id="c2261-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="c2261-106">Bağlantı talepleri, kodunuzdan devralınan sınıflarda geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="c2261-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="c2261-107">Tam yığın yürüyüşü bu tür bir taleple gerçekleştirilmediğini ve kodunuzu hala çekme saldırılarına karşı duyarlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c2261-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="c2261-108">Örneğin, A derlemesindeki bir yöntem bağlantı talebi yle korunuyorsa, B derlemesinde doğrudan arayan, B Derlemesi izinlerine göre değerlendirilir.  Ancak, bağlantı talebi, B derlemesindeki yöntemi kullanarak A derlemesindeki yöntemi dolaylı olarak çağırırsa, C derlemesindeki bir yöntemi değerlendirmez. Bağlantı talebi, yalnızca hemen arama derlemesindeki doğrudan arayanların kodunuza bağlanması gereken izinleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2261-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="c2261-109">Tüm arayanların kodunuzu çalıştırmak için çalışması gereken izinleri belirtmez.</span><span class="sxs-lookup"><span data-stu-id="c2261-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="c2261-110">, <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A>ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> yığın yürüyüş değiştiriciler bağlantı taleplerinin değerlendirilmesi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c2261-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="c2261-111">Bağlantı talepleri yığın yürüyüşü yapmadığından, yığın yürüyüş değiştiriciler bağlantı talepleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c2261-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="c2261-112">Bağlantı talebi tarafından korunan bir [yönteme Yansıma](../reflection-and-codedom/reflection.md)aracılığıyla erişilirse, bağlantı talebi yansıma aracılığıyla erişilen kodun hemen arayanını denetler.</span><span class="sxs-lookup"><span data-stu-id="c2261-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="c2261-113">Bu, hem yöntem bulma hem de yansıma kullanılarak gerçekleştirilen yöntem çağırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2261-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="c2261-114">Örneğin, kodun bir bağlantı <xref:System.Reflection.MethodInfo> talebi tarafından korunan bir yöntemi temsil eden bir nesneyi döndürmek için yansıma kullandığını ve sonra bu **MethodInfo** nesnesini özgün yöntemi çağırmak için nesneyi kullanan başka bir koda aktardığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c2261-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="c2261-115">Bu durumda bağlantı talebi denetimi iki kez oluşur: Bir kez **MethodInfo** nesnesini döndüren kod için ve bir kez de onu çağıran kod için.</span><span class="sxs-lookup"><span data-stu-id="c2261-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2261-116">Statik yapı oluşturucuüzerinde gerçekleştirilen bir bağlantı talebi, uygulamanın kod yürütme yolu dışında, sistem tarafından çağrıldığı için yapıcıyı korumaz.</span><span class="sxs-lookup"><span data-stu-id="c2261-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="c2261-117">Sonuç olarak, bir bağlantı talebi tüm sınıfa uygulandığında, sınıfın geri kalanını korusa da statik bir oluşturucuya erişimi koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="c2261-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="c2261-118">Aşağıdaki kod parçası bildirimsel olarak `ReadData` yönteme bağlantı veren herhangi `CustomPermission` bir kodun izin alması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2261-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="c2261-119">Bu izin varsayımsal bir özel izindir ve .NET Framework'de bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="c2261-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="c2261-120">Talep bir **SecurityAction.LinkDemand** bayrağı geçerek `CustomPermissionAttribute`yapılır.</span><span class="sxs-lookup"><span data-stu-id="c2261-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2261-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2261-121">See also</span></span>

- [<span data-ttu-id="c2261-122">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c2261-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="c2261-123">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c2261-123">Code Access Security</span></span>](code-access-security.md)
