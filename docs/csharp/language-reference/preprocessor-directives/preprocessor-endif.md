---
title: "#endif (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7e68dd20d914052c3fe5cabcb83abdae100465c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="endif-c-reference"></a><span data-ttu-id="886bb-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="886bb-102">#endif (C# Reference)</span></span>
<span data-ttu-id="886bb-103">`#endif`ile başlayan bir koşullu yönergesi sonunu belirtir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="886bb-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="886bb-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="886bb-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="886bb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="886bb-105">Remarks</span></span>  
 <span data-ttu-id="886bb-106">İle başlayarak, koşullu bir yönerge bir `#if` yönergesi, açıkça bitirilmelidir ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="886bb-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="886bb-107">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#endif`.</span><span class="sxs-lookup"><span data-stu-id="886bb-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886bb-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="886bb-108">See Also</span></span>  
 [<span data-ttu-id="886bb-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="886bb-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="886bb-110">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="886bb-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="886bb-111">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="886bb-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
