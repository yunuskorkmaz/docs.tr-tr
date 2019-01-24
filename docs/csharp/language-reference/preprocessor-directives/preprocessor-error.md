---
title: '#hata - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559350"
---
# <a name="error-c-reference"></a><span data-ttu-id="7a1c2-102">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7a1c2-102">#error (C# Reference)</span></span>
<span data-ttu-id="7a1c2-103">`#error` oluşturmanıza olanak sağlar. bir [CS1029](../compiler-messages/cs1029.md) kodunuzda belirli bir konumdan kullanıcı tanımlı hata.</span><span class="sxs-lookup"><span data-stu-id="7a1c2-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="7a1c2-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7a1c2-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="7a1c2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a1c2-105">Remarks</span></span>  
 <span data-ttu-id="7a1c2-106">Yaygın `#error` bir koşullu yönergesiyse.</span><span class="sxs-lookup"><span data-stu-id="7a1c2-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="7a1c2-107">Kullanıcı tanımlı bir uyarı ile oluşturmak mümkündür [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="7a1c2-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a1c2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7a1c2-108">Example</span></span>  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a1c2-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a1c2-109">See also</span></span>

- [<span data-ttu-id="7a1c2-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7a1c2-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7a1c2-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7a1c2-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7a1c2-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7a1c2-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
