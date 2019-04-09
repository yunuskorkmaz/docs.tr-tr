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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba3172b1a82c0a9f624a49eb63a193dd29faac1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166997"
---
# <a name="link-demands"></a><span data-ttu-id="ae2e8-102">Bağlantı Talepleri</span><span class="sxs-lookup"><span data-stu-id="ae2e8-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="ae2e8-103">Bağlantı talebi, tam zamanında derleme sırasında güvenlik denetimi neden olur ve kodunuzun yalnızca anında çağıran derlemeye denetler.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="ae2e8-104">Kodunuzu işlev işaretçi başvuruları ve yöntem çağrıları dahil olmak üzere, bir tür başvurusu ile ilişkili bağlama gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="ae2e8-105">Çağrıyı yapan derlemeyi, koda bağlamak için yeterli izne sahip değilse bağlantıya izin verilmiyor ve bir çalışma zamanı özel durum kodu yüklendi ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="ae2e8-106">Bağlantı talepleri kodunuzdan devralınan sınıflardaki geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="ae2e8-107">Bu talep türü ile tam bir yığın ilerlemesi yapılmaz ve kodunuzu saldırıları luring için saldırılara açıktır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="ae2e8-108">Derlemesi içindeki bir yöntemi bağlantı talebi tarafından korunuyorsa, örneğin, derleme B içinde doğrudan çağıran derleme B'nin izinlere göre değerlendirilir  Yöntemini kullanarak b derlemede derlemesindeki dolaylı olarak yöntemini çağırır, ancak bağlantı talebi C derlemesindeki bir yöntemi işlemeyecek Bağlantı talebi, koda bağlamak çağıranlar, hemen çağıran derlemeye olmalıdır yalnızca izinleri doğrudan belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="ae2e8-109">Tüm çağıranların kodunuzu çalıştırmak için sahip olmanız gereken izinleri belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="ae2e8-110"><xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, Ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> yığın ilerlemesi değiştiriciler bağlantı talepleri değerlendirmesi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="ae2e8-111">Bağlantı talepleri yığın ilerlemesi gerçekleştirmediği için yığın ilerlemesi değiştiriciler bağlantı talepleri üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="ae2e8-112">Bağlantı talebi tarafından korunan bir yöntem aracılığıyla erişilen, [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md), sonra da bağlantı talebi yansıma yoluyla erişilen kod şu anki çağırıcı denetler.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="ae2e8-113">Bu, hem yöntemi bulma ve yansıma kullanılarak gerçekleştirilen yöntem çağırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="ae2e8-114">Örneğin, kod döndürmek için yansıtma kullanır varsayalım. bir <xref:System.Reflection.MethodInfo> bağlantı talebi tarafından korunan ve ardından geçiren bir yöntemi temsil eden nesne **MethodInfo** nesnenin orijinal yöntemini çağırmak için kullandığı bazı bir kod için nesne.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="ae2e8-115">Bu durumda bağlantı talebi onay iki kez oluşuyor: döndüren kod için bir kez **MethodInfo** nesne ve onu çağıran kod için bir kez.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae2e8-116">Statik oluşturucular dışında uygulamanın kod yürütme yolu sistem tarafından çağrıldığı bir statik sınıf oluşturucu üzerinde gerçekleştirilen bağlantı talebi Oluşturucu korumaz.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="ae2e8-117">Bağlantı talebi tamamını bir sınıfa uygulandığında, sınıfın rest korumak ancak sonuç olarak, bu erişim için bir statik Oluşturucu koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="ae2e8-118">Aşağıdaki kod parçası, bildirimli herhangi kod bağlama belirtir `ReadData` yöntemi olmalıdır `CustomPermission` izni.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="ae2e8-119">Bu izin, kuramsal bir özel izni ve .NET Framework'teki yok.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="ae2e8-120">İsteğe bağlı geçirerek yapılan bir **SecurityAction.LinkDemand** bayrak `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ae2e8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae2e8-121">See also</span></span>

- [<span data-ttu-id="ae2e8-122">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae2e8-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="ae2e8-123">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ae2e8-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
