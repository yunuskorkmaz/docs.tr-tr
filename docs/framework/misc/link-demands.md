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
ms.openlocfilehash: e3bde5b18437cc9890f660f018e81582a4d708d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910914"
---
# <a name="link-demands"></a><span data-ttu-id="2f173-102">Bağlantı Talepleri</span><span class="sxs-lookup"><span data-stu-id="2f173-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="2f173-103">Bir bağlantı isteği, tam zamanında derleme sırasında bir güvenlik denetimine neden olur ve yalnızca kodunuzun hemen çağıran derlemesini denetler.</span><span class="sxs-lookup"><span data-stu-id="2f173-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="2f173-104">Bağlama, kodunuz işlev işaretçisi başvuruları ve Yöntem çağrıları dahil olmak üzere bir tür başvurusuna bağlandığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="2f173-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="2f173-105">Çağıran derlemenin kodunuza bağlamak için yeterli izni yoksa, bağlantıya izin verilmez ve kod yüklenip çalıştırıldığında bir çalışma zamanı özel durumu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2f173-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="2f173-106">Bağlantı talepleri, kodunuzun devraldığı sınıflarda geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="2f173-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="2f173-107">Tam bir yığın ilerinin bu talep türü ile gerçekleştirilmediğini ve kodunuzun yine de en fazla saldırı saldırılarına maruz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2f173-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="2f173-108">Örneğin, derleme A içindeki bir yöntem bir bağlantı talebi tarafından korunuyorsa, B derlemesinde doğrudan çağıran derleme B 'nin izinlerine göre değerlendirilir.  Ancak, bağlantı isteği, derleme B içindeki yöntemi kullanarak dolaylı olarak bir derlemeyi çağıran derleme C 'deki bir yöntemi değerlendirmeyecektir. Bağlantı talebi yalnızca hemen çağıran derlemede bulunan izin doğrudan çağıranlarının kodunuza bağlanması için sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f173-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="2f173-109">Tüm çağıranların kodunuzu çalıştırmak için sahip olması gereken izinleri belirtmez.</span><span class="sxs-lookup"><span data-stu-id="2f173-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="2f173-110"><xref:System.Security.CodeAccessPermission.Assert%2A>, Veyığın<xref:System.Security.CodeAccessPermission.PermitOnly%2A> ilerleme değiştiricileri bağlantı taleplerinin değerlendirilmesini etkilemez. <xref:System.Security.CodeAccessPermission.Deny%2A></span><span class="sxs-lookup"><span data-stu-id="2f173-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="2f173-111">Bağlantı talepleri bir yığın ilerleme işlemi gerçekleştirmediğinden, yığın ilerleme değiştiricilerin bağlantı taleplerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="2f173-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="2f173-112">Bir bağlantı talebi tarafından korunan bir yönteme [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)aracılığıyla erişiliyorsa, bağlantı talebi, yansıma aracılığıyla erişilen kodun hemen çağırışını denetler.</span><span class="sxs-lookup"><span data-stu-id="2f173-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="2f173-113">Bu, hem yöntem bulma hem de yansıma kullanılarak gerçekleştirilen yöntem çağırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2f173-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="2f173-114">Örneğin, kodun bir bağlantı talebi tarafından korunan bir yöntemi <xref:System.Reflection.MethodInfo> temsil eden bir nesneyi döndürmek için yansıma kullandığını varsayın ve sonra bu **MethodInfo** nesnesini, özgün yöntemi çağırmak için nesnesini kullanan başka bir koda geçirir.</span><span class="sxs-lookup"><span data-stu-id="2f173-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="2f173-115">Bu durumda, bağlantı isteği denetimi iki kez gerçekleşir: **MethodInfo** nesnesini döndüren kod için bir kez ve onu çağıran kod için bir kez.</span><span class="sxs-lookup"><span data-stu-id="2f173-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f173-116">Statik oluşturucular, uygulamanın kod yürütme yolu dışında, sistem tarafından çağrılamadığından, statik sınıf oluşturucusunda gerçekleştirilen bir bağlantı isteği oluşturucuyu korumaz.</span><span class="sxs-lookup"><span data-stu-id="2f173-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="2f173-117">Sonuç olarak, bir bağlantı isteği tüm sınıfa uygulandığında, sınıfın geri kalanını korusa da statik bir oluşturucuya erişimi koruyamaz.</span><span class="sxs-lookup"><span data-stu-id="2f173-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="2f173-118">Aşağıdaki kod parçası bildirimli olarak, `ReadData` yönteme bağlanan herhangi bir kodun `CustomPermission` izne sahip olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2f173-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="2f173-119">Bu izin kuramsal bir özel izindir ve .NET Framework yok.</span><span class="sxs-lookup"><span data-stu-id="2f173-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="2f173-120">Talep, öğesine `CustomPermissionAttribute`bir **SecurityAction. LinkDemand** bayrağı geçirilerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="2f173-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f173-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f173-121">See also</span></span>

- [<span data-ttu-id="2f173-122">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2f173-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="2f173-123">Kod erişim güvenliği</span><span class="sxs-lookup"><span data-stu-id="2f173-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
