---
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 95a67a552efacf9e77dc3ebc3e0187817a6d82e2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698577"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="2bd57-102">'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir</span><span class="sxs-lookup"><span data-stu-id="2bd57-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="2bd57-103">Visual Basic bir veri türünü genişletmenin tek yolu standart bir modül içinde bir genişletme yöntemi tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2bd57-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="2bd57-104">Genişletme yöntemi bir `Sub` yordamı veya `Function` yordamı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2bd57-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="2bd57-105">Tüm genişletme yöntemlerinin, <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanından `<Extension()>` uzantı özniteliğiyle işaretlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2bd57-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="2bd57-106">İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="2bd57-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="2bd57-107">Uzantı özniteliğinin başka bir kullanımı geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2bd57-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="2bd57-108">**Hata kimliği:** BC36550</span><span class="sxs-lookup"><span data-stu-id="2bd57-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2bd57-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2bd57-109">To correct this error</span></span>  
  
- <span data-ttu-id="2bd57-110">Uzantı özniteliğini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="2bd57-110">Remove the extension attribute.</span></span>  
  
- <span data-ttu-id="2bd57-111">Uzantınızı bir kapsayıcı modülünde tanımlanan bir yöntem olarak yeniden tasarlama.</span><span class="sxs-lookup"><span data-stu-id="2bd57-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd57-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2bd57-112">Example</span></span>  
 <span data-ttu-id="2bd57-113">Aşağıdaki örnek, `String` veri türü için `Print` yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2bd57-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
```vb  
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
  
## <a name="see-also"></a><span data-ttu-id="2bd57-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bd57-114">See also</span></span>

- [<span data-ttu-id="2bd57-115">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="2bd57-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="2bd57-116">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="2bd57-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="2bd57-117">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="2bd57-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
