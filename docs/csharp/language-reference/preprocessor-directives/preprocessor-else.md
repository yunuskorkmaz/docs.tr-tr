---
title: "#else (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3468d35a6e45c06f46fe8671708ce01a3cc7b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="else-c-reference"></a><span data-ttu-id="aa5e4-102">#else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aa5e4-102">#else (C# Reference)</span></span>
<span data-ttu-id="aa5e4-103">`#else`Bileşik koşullu yönergesi oluşturmanıza olanak tanır şekilde, önceki içinde ifadeleri hiçbiri [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya (isteğe bağlı) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) yönergeleri `true`, derleyici tüm kod değerlendirir arasında `#else` ve sonraki `#endif`.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa5e4-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa5e4-104">Remarks</span></span>  
 <span data-ttu-id="aa5e4-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) sonra sonraki önişlemci yönergesi olmalıdır `#else`.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="aa5e4-106">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#else`.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5e4-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa5e4-107">See Also</span></span>  
 [<span data-ttu-id="aa5e4-108">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa5e4-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aa5e4-109">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa5e4-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aa5e4-110">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="aa5e4-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
