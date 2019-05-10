---
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 88212fb2c04eab61b719a161ae01ccdda9a6110d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640720"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="32459-102">'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir</span><span class="sxs-lookup"><span data-stu-id="32459-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="32459-103">Visual Basic'te bir veri türü genişletmek için tek bir standart modül içinde bir genişletme yöntemi tanımlamak için yoludur.</span><span class="sxs-lookup"><span data-stu-id="32459-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="32459-104">Genişletme yöntemi olabilir bir `Sub` yordamı veya `Function` yordamı.</span><span class="sxs-lookup"><span data-stu-id="32459-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="32459-105">Tüm uzantı yöntemleri uzantı özniteliğiyle işaretlenmelidir `<Extension()>`, gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="32459-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="32459-106">İsteğe bağlı olarak, bir uzantı yöntemini içeren modül aynı şekilde işaretlenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="32459-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="32459-107">Herhangi bir kullanıma uzantısı özniteliği geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="32459-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="32459-108">**Hata Kimliği:** BC36550</span><span class="sxs-lookup"><span data-stu-id="32459-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32459-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="32459-109">To correct this error</span></span>  
  
- <span data-ttu-id="32459-110">Uzantı özniteliğine kaldırın.</span><span class="sxs-lookup"><span data-stu-id="32459-110">Remove the extension attribute.</span></span>  
  
- <span data-ttu-id="32459-111">Uzantınızı kapsayan bir modülde tanımlanmış bir yöntem olarak yeniden tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="32459-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32459-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="32459-112">Example</span></span>  
 <span data-ttu-id="32459-113">Aşağıdaki örnekte tanımlayan bir `Print` yöntemi `String` veri türü.</span><span class="sxs-lookup"><span data-stu-id="32459-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32459-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32459-114">See also</span></span>

- [<span data-ttu-id="32459-115">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="32459-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="32459-116">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="32459-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="32459-117">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="32459-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
