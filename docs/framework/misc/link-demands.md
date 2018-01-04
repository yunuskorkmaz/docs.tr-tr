---
title: "Bağlantı Talepleri"
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
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e59ae7b0c26106f19f5b14290047deb9b5f30c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="link-demands"></a><span data-ttu-id="be90e-102">Bağlantı Talepleri</span><span class="sxs-lookup"><span data-stu-id="be90e-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="be90e-103">Bir bağlantı isteği güvenlik denetimi tam zamanında derleme sırasında neden olur ve yalnızca hemen çağrıyı yapan derlemeyi kodunuzu denetler.</span><span class="sxs-lookup"><span data-stu-id="be90e-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="be90e-104">Kodunuzu işlev işaretçisi başvuruları ve yöntem çağrıları dahil olmak üzere bir tür referansı bağlandığında bağlama oluşur.</span><span class="sxs-lookup"><span data-stu-id="be90e-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="be90e-105">Çağrıyı yapan derlemeyi kodunuzu bağlamak için yeterli izni yok, bağlantıyı verilmez ve kodu yüklenen ve Çalıştır çalışma zamanı özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="be90e-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="be90e-106">Bağlantı talepleri kodunuzdan devralınan sınıflar geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="be90e-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="be90e-107">Tam yığın ilerlemesi isteğe bağlı bu tür yapılmaz ve kodunuzu saldırıları luring için hala açık olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="be90e-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="be90e-108">Derlemesi yönteminde bir bağlantı isteği tarafından korunuyorsa, örneğin, doğrudan çağıran B derlemesindeki derleme B'deki izinlerine göre değerlendirilir  Bu yöntem kullanılarak derleme B. derleme dolaylı olarak yöntemi çağırırsa ancak, bağlantı isteği C derlemesindeki yöntemi işlemeyecek Bağlantı isteği hemen çağrıyı yapan derlemeyi arayanlar kodunuzu bağlamak zorunda gerekir yalnızca izinleri doğrudan belirtir.</span><span class="sxs-lookup"><span data-stu-id="be90e-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="be90e-109">Tüm arayanlar kodunuzu çalıştırmak için gereken izinleri belirtmiyor.</span><span class="sxs-lookup"><span data-stu-id="be90e-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="be90e-110"><xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, Ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> yığın ilerlemesi değiştiricileri bağlantı talepleri değerlendirmesi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="be90e-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="be90e-111">Bağlantı talepleri yığın ilerlemesi gerçekleştirmediği için yığın ilerlemesi değiştiricileri bağlantı talepleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="be90e-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="be90e-112">Bir bağlantı isteği tarafından korunan bir yöntem aracılığıyla erişilen varsa [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md), sonra da Yansıtma üzerinden erişilen kodunun ilk çağıran bir bağlantı isteği denetler.</span><span class="sxs-lookup"><span data-stu-id="be90e-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="be90e-113">Bu, yöntem bulma ve yansıma kullanarak gerçekleştirilen yöntem çağırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="be90e-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="be90e-114">Örneğin, kod döndürülecek yansıma kullandığını varsayın bir <xref:System.Reflection.MethodInfo> nesne bir yöntemi temsil eden bir bağlantı isteği tarafından korunan ve sonra geçen **MethodInfo** nesnenin özgün yöntemini çağırmak için kullandığı bazı bir kod nesnesine.</span><span class="sxs-lookup"><span data-stu-id="be90e-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="be90e-115">Bu durumda bağlantı isteğe bağlı onay iki kez oluşur: döndürür kodu için bir kez **MethodInfo** nesne ve onu çağıran kodu için bir kez.</span><span class="sxs-lookup"><span data-stu-id="be90e-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be90e-116">Statik oluşturucular uygulamanın kodu yürütme yolu dışında sistem tarafından denir çünkü bir statik sınıf oluşturucu üzerinde gerçekleştirilen bir bağlantı isteği Oluşturucusu korumaz.</span><span class="sxs-lookup"><span data-stu-id="be90e-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="be90e-117">Bir bağlantı isteği tüm bir sınıfa uygulandığında, sınıfı kalan korunmasına rağmen sonuç olarak, bu erişim statik oluşturucuya koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="be90e-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="be90e-118">Aşağıdaki kod parçası, bildirimli olarak herhangi bir kod bağlantılandırma belirtir `ReadData` yöntemi olmalıdır `CustomPermission` izni.</span><span class="sxs-lookup"><span data-stu-id="be90e-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="be90e-119">Bu izni kuramsal özel izinleri ve .NET Framework mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="be90e-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="be90e-120">İsteğe bağlı geçirerek yapılan bir **SecurityAction.LinkDemand** bayrağını `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="be90e-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="be90e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be90e-121">See Also</span></span>  
 [<span data-ttu-id="be90e-122">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be90e-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="be90e-123">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="be90e-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
