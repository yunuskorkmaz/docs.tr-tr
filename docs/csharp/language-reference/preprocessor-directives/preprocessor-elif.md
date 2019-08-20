---
title: '#elif- C# başvuru'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608590"
---
# <a name="elif-c-reference"></a><span data-ttu-id="26aec-102">#elif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="26aec-102">#elif (C# Reference)</span></span>
<span data-ttu-id="26aec-103">`#elif`bileşik bir koşullu yönerge oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="26aec-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="26aec-104">Yukarıdaki #if ne de `#elif` önceki, isteğe bağlı bir [](./preprocessor-if.md) yönerge ifadesi olarak `true`değerlendiriliyorsa ifadedeğerlendirilir.`#elif`</span><span class="sxs-lookup"><span data-stu-id="26aec-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="26aec-105">Bir `#elif` ifade olarak `true`değerlendirilirse, derleyici `#elif` ve sonraki koşullu yönerge arasındaki tüm kodu değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="26aec-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="26aec-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="26aec-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="26aec-107">Birden çok sembolü değerlendirmek için `==` işleçleri (eşitlik) `!=` , (eşitsizlik `&&` ), (ve) ve `||` (veya) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26aec-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="26aec-108">Simgeleri ve işleçleri parantez ile de gruplandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26aec-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26aec-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26aec-109">Remarks</span></span>  
 <span data-ttu-id="26aec-110">`#elif`, ile eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="26aec-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="26aec-111">Kullanılması `#elif` daha basittir çünkü her biri `#if` bir [#endif](./preprocessor-endif.md)gerektirir, ancak bir `#elif` eşleştirme `#endif`olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26aec-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="26aec-112">Öğesinin [](./preprocessor-if.md) nasıl kullanılacağına `#elif`ilişkin bir örnek için bkz. #if.</span><span class="sxs-lookup"><span data-stu-id="26aec-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26aec-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26aec-113">See also</span></span>

- [<span data-ttu-id="26aec-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="26aec-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="26aec-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="26aec-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="26aec-116">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="26aec-116">C# Preprocessor Directives</span></span>](./index.md)
