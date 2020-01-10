---
title: '#elif- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712578"
---
# <a name="elif-c-reference"></a><span data-ttu-id="7eff9-102">#elif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7eff9-102">#elif (C# Reference)</span></span>
<span data-ttu-id="7eff9-103">`#elif`, bileşik bir koşullu yönerge oluşturmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="7eff9-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="7eff9-104">`#elif` ifadesi, önceki [#if](./preprocessor-if.md) ne de önceki, isteğe bağlı `#elif` yönerge ifadelerinin `true`olarak değerlendirilmediği takdirde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="7eff9-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="7eff9-105">`#elif` bir ifade `true`değerlendirilirse, derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="7eff9-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="7eff9-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7eff9-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="7eff9-107">Birden çok simgeyi değerlendirmek için `==` (eşitlik), `!=` (eşitsizlik), `&&` (ve) ve `||` (ya da) işleçlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eff9-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="7eff9-108">Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7eff9-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eff9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7eff9-109">Remarks</span></span>  
 <span data-ttu-id="7eff9-110">`#elif` ile eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="7eff9-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="7eff9-111">Her `#if` [#endif](./preprocessor-endif.md)gerektirdiğinden `#elif` kullanımı basittir, ancak bir `#elif` eşleşen bir `#endif`olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7eff9-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="7eff9-112">`#elif`nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="7eff9-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eff9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7eff9-113">See also</span></span>

- [<span data-ttu-id="7eff9-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="7eff9-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7eff9-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7eff9-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7eff9-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7eff9-116">C# Preprocessor Directives</span></span>](./index.md)
