---
title: "&#39; Uzantı &#39; öznitelik yalnızca uygulanabilir &#39; Modül &#39; &#39; Alt &#39; veya &#39; İşlev &#39; bildirimleri"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords: BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="74063-102">&#39; Uzantı &#39; öznitelik yalnızca uygulanabilir &#39; Modül &#39; &#39; Alt &#39; veya &#39; İşlev &#39; bildirimleri</span><span class="sxs-lookup"><span data-stu-id="74063-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="74063-103">Visual Basic'te bir veri türü genişletmek için tek bir standart modül içinde bir genişletme yöntemi tanımlamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="74063-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="74063-104">Genişletme yöntemi olabilir bir `Sub` yordamı veya `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="74063-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="74063-105">Tüm uzantı yöntemleri uzantısı özniteliği ile işaretlenmiş olmalıdır `<Extension()>`, gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="74063-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="74063-106">İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="74063-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="74063-107">Herhangi bir uzantı özniteliğinin kullanımını geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="74063-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="74063-108">**Hata Kimliği:** BC36550</span><span class="sxs-lookup"><span data-stu-id="74063-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74063-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="74063-109">To correct this error</span></span>  
  
-   <span data-ttu-id="74063-110">Uzantı özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="74063-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="74063-111">Uzantınızı yeniden tasarlamanız kapsayan bir modülde tanımlanmış bir yöntem olarak.</span><span class="sxs-lookup"><span data-stu-id="74063-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74063-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="74063-112">Example</span></span>  
 <span data-ttu-id="74063-113">Aşağıdaki örnek tanımlayan bir `Print` yöntemi `String` veri türü.</span><span class="sxs-lookup"><span data-stu-id="74063-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="74063-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74063-114">See Also</span></span>  
 [<span data-ttu-id="74063-115">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="74063-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="74063-116">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="74063-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="74063-117">Module deyimi</span><span class="sxs-lookup"><span data-stu-id="74063-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
