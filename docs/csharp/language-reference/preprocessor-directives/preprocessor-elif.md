---
title: '#elif (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a><span data-ttu-id="671b0-102">#elif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="671b0-102">#elif (C# Reference)</span></span>
<span data-ttu-id="671b0-103">`#elif`Bileşik koşullu yönergesi oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="671b0-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="671b0-104">`#elif` Ne ifade'nin değerlendirilmesi önceki [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ya da herhangi bir önceki, isteğe bağlı, `#elif` yönerge ifadeleri değerlendirmek için `true`.</span><span class="sxs-lookup"><span data-stu-id="671b0-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="671b0-105">Varsa bir `#elif` ifadeyi hesaplar için `true`, tüm kod arasında derleyici değerlendirir `#elif` ve sonraki koşullu yönergesi.</span><span class="sxs-lookup"><span data-stu-id="671b0-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="671b0-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="671b0-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="671b0-107">İşleçleri kullanabilirsiniz `==` (eşitlik) `!=` (eşitsizlik) `&&` (ve) ve `||` (veya) çoklu sembolleri değerlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="671b0-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="671b0-108">Ayrıca, simgeler ve parantez işleçlerle de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="671b0-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="671b0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="671b0-109">Remarks</span></span>  
 <span data-ttu-id="671b0-110">`#elif`kullanmakla eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="671b0-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="671b0-111">Kullanarak `#elif` basittir, çünkü her `#if` gerektiren bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), ancak bir `#elif` eşleşen olmadan kullanılabilir `#endif`.</span><span class="sxs-lookup"><span data-stu-id="671b0-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="671b0-112">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#elif`.</span><span class="sxs-lookup"><span data-stu-id="671b0-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="671b0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="671b0-113">See Also</span></span>  
 [<span data-ttu-id="671b0-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="671b0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="671b0-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="671b0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="671b0-116">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="671b0-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
