---
title: '#endif - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 58e29363ca1298966ecf88e6b456f33f43a176b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573052"
---
# <a name="endif-c-reference"></a><span data-ttu-id="56f41-102">#endif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="56f41-102">#endif (C# Reference)</span></span>
<span data-ttu-id="56f41-103">`#endif` ile başlayan bir koşullu yönergesi sonuna belirten [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="56f41-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="56f41-104">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="56f41-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="56f41-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56f41-105">Remarks</span></span>  
 <span data-ttu-id="56f41-106">İle başlayarak, koşullu bir yönerge bir `#if` yönergesi, açıkça tamamlanmalıdır ile bir `#endif` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="56f41-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="56f41-107">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#endif`.</span><span class="sxs-lookup"><span data-stu-id="56f41-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f41-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56f41-108">See also</span></span>

- [<span data-ttu-id="56f41-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="56f41-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="56f41-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="56f41-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="56f41-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="56f41-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
