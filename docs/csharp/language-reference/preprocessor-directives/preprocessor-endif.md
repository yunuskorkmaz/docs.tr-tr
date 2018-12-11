---
title: '#endif - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 13b43919b666dcc8c5adfc3490eaad73960547ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243913"
---
# <a name="endif-c-reference"></a><span data-ttu-id="e05e1-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e05e1-102">#endif (C# Reference)</span></span>
<span data-ttu-id="e05e1-103">`#endif` ile başlayan bir koşullu yönergesi sonuna belirten [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="e05e1-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="e05e1-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="e05e1-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="e05e1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e05e1-105">Remarks</span></span>  
 <span data-ttu-id="e05e1-106">İle başlayarak, koşullu bir yönerge bir `#if` yönergesi, açıkça tamamlanmalıdır ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="e05e1-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="e05e1-107">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#endif`.</span><span class="sxs-lookup"><span data-stu-id="e05e1-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05e1-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e05e1-108">See Also</span></span>

- [<span data-ttu-id="e05e1-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e05e1-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e05e1-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e05e1-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e05e1-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e05e1-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
