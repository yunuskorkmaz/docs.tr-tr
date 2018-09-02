---
title: '#endif (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: a652c1226f8f0c624ec8ebf0e665a4aa77ddf6f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420820"
---
# <a name="endif-c-reference"></a><span data-ttu-id="aee1a-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aee1a-102">#endif (C# Reference)</span></span>
<span data-ttu-id="aee1a-103">`#endif` ile başlayan bir koşullu yönergesi sonuna belirten [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="aee1a-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="aee1a-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="aee1a-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="aee1a-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aee1a-105">Remarks</span></span>  
 <span data-ttu-id="aee1a-106">İle başlayarak, koşullu bir yönerge bir `#if` yönergesi, açıkça tamamlanmalıdır ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="aee1a-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="aee1a-107">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#endif`.</span><span class="sxs-lookup"><span data-stu-id="aee1a-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee1a-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aee1a-108">See Also</span></span>

- [<span data-ttu-id="aee1a-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aee1a-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="aee1a-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aee1a-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aee1a-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aee1a-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
