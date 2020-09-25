---
description: '#Elif-C# başvurusu'
title: '#Elif-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 383c143792a39bb3abcd255804360ad5e2f8ef74
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168705"
---
# <a name="elif-c-reference"></a><span data-ttu-id="b211e-103">#elif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b211e-103">#elif (C# Reference)</span></span>

<span data-ttu-id="b211e-104">`#elif` bileşik bir koşullu yönerge oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b211e-104">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="b211e-105">`#elif`Yukarıdaki [#if](./preprocessor-if.md) ne de önceki, isteğe bağlı bir yönerge ifadesi olarak değerlendiriliyorsa ifade değerlendirilir `#elif` `true` .</span><span class="sxs-lookup"><span data-stu-id="b211e-105">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="b211e-106">Bir `#elif` ifade olarak değerlendirilirse `true` , derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b211e-106">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="b211e-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b211e-107">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="b211e-108">`==`Birden çok sembolü değerlendirmek için İşleçleri (eşitlik), (eşitsizlik), ( `!=` `&&` ve) ve `||` (veya) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b211e-108">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="b211e-109">Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b211e-109">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b211e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b211e-110">Remarks</span></span>  

 <span data-ttu-id="b211e-111">`#elif` , ile eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="b211e-111">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="b211e-112">Kullanılması `#elif` daha basittir çünkü her biri `#if` bir [#endif](./preprocessor-endif.md)gerektirir, ancak bir `#elif` eşleştirme olmadan kullanılabilir `#endif` .</span><span class="sxs-lookup"><span data-stu-id="b211e-112">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="b211e-113">Öğesinin nasıl kullanılacağına ilişkin bir örnek için bkz. [#if](./preprocessor-if.md) `#elif` .</span><span class="sxs-lookup"><span data-stu-id="b211e-113">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b211e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b211e-114">See also</span></span>

- [<span data-ttu-id="b211e-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b211e-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b211e-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b211e-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b211e-117">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b211e-117">C# Preprocessor Directives</span></span>](./index.md)
