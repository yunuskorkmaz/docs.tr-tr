---
title: '#elif - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 00a9298be6ecd6f5e775d930190ddb6e227e4711
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587235"
---
# <a name="elif-c-reference"></a><span data-ttu-id="52978-102">#elif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="52978-102">#elif (C# Reference)</span></span>
<span data-ttu-id="52978-103">`#elif` bir bileşik koşullu yönergesi oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="52978-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="52978-104">`#elif` Kullanılmazsa, ifade değerlendirilir önceki [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) veya hiçbir, isteğe bağlı, önceki `#elif` yönerge nevyhodnocovat için `true`.</span><span class="sxs-lookup"><span data-stu-id="52978-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="52978-105">Varsa bir `#elif` ifadeyi hesaplar için `true`, derleyicinin kod arasında değerlendirir `#elif` ve sonraki koşullu yönergesi.</span><span class="sxs-lookup"><span data-stu-id="52978-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="52978-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="52978-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="52978-107">İşleçleri `==` (eşitlik) `!=` (eşitsizlik) `&&` (ve) ve `||` (veya) birden çok sembolleri değerlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="52978-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="52978-108">Ayrıca, simgeler ve işleçler parantezli gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52978-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52978-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52978-109">Remarks</span></span>  
 <span data-ttu-id="52978-110">`#elif` kullanmakla eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="52978-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="52978-111">Kullanarak `#elif` basittir çünkü her `#if` gerektiren bir [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)bilgileriyse bir `#elif` eşleşmeyen kullanılabilir `#endif`.</span><span class="sxs-lookup"><span data-stu-id="52978-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="52978-112">Bkz: [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nasıl kullanılacağına ilişkin bir örnek `#elif`.</span><span class="sxs-lookup"><span data-stu-id="52978-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52978-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52978-113">See also</span></span>

- [<span data-ttu-id="52978-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="52978-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="52978-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="52978-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="52978-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="52978-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
