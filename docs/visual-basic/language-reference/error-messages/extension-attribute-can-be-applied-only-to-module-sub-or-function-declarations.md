---
title: '&#39;Uzantı&#39; özniteliği yalnızca uygulanabilir &#39;Modülü&#39;, &#39;alt&#39;, veya &#39;işlevi&#39; bildirimleri'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718240"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="6079b-102">&#39;Uzantı&#39; özniteliği yalnızca uygulanabilir &#39;Modülü&#39;, &#39;alt&#39;, veya &#39;işlevi&#39; bildirimleri</span><span class="sxs-lookup"><span data-stu-id="6079b-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="6079b-103">Visual Basic'te bir veri türü genişletmek için tek bir standart modül içinde bir genişletme yöntemi tanımlamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="6079b-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="6079b-104">Genişletme yöntemi olabilir bir `Sub` yordamı veya `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="6079b-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="6079b-105">Tüm uzantı yöntemleri uzantı özniteliğiyle işaretlenmelidir `<Extension()>`, gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6079b-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6079b-106">İsteğe bağlı olarak, bir uzantı yöntemini içeren modül aynı şekilde işaretlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="6079b-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="6079b-107">Herhangi bir kullanıma uzantısı özniteliği geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="6079b-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="6079b-108">**Hata Kimliği:** BC36550</span><span class="sxs-lookup"><span data-stu-id="6079b-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6079b-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6079b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="6079b-110">Uzantı özniteliğine kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6079b-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="6079b-111">Uzantınızı kapsayan bir modülde tanımlanmış bir yöntem olarak yeniden tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="6079b-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6079b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6079b-112">Example</span></span>  
 <span data-ttu-id="6079b-113">Aşağıdaki örnekte tanımlayan bir `Print` yöntemi `String` veri türü.</span><span class="sxs-lookup"><span data-stu-id="6079b-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6079b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6079b-114">See also</span></span>
- [<span data-ttu-id="6079b-115">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="6079b-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="6079b-116">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6079b-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="6079b-117">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="6079b-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
