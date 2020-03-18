---
title: '#elif - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712578"
---
# <a name="elif-c-reference"></a><span data-ttu-id="c9575-102">#elif (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c9575-102">#elif (C# Reference)</span></span>
<span data-ttu-id="c9575-103">`#elif`bileşik koşullu yönerge oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9575-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="c9575-104">İfade, `#elif` ne önceki [#if](./preprocessor-if.md) ne de önceki, isteğe `#elif` bağlı, yönerge `true`ifadeleri değerlendirilmezse değerlendirilecektir.</span><span class="sxs-lookup"><span data-stu-id="c9575-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="c9575-105">Bir `#elif` ifade , `true`derleyici ve sonraki koşullu yönerge arasındaki `#elif` tüm kodu değerlendirirse.</span><span class="sxs-lookup"><span data-stu-id="c9575-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="c9575-106">Örnek:</span><span class="sxs-lookup"><span data-stu-id="c9575-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="c9575-107">Birden çok sembolü `==` değerlendirmek için `!=` işleçleri `&&` (eşitlik), `||` (eşitsizlik), (ve) ve (veya) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9575-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="c9575-108">Sembolleri ve işleçleri parantez içinde de gruplayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9575-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9575-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9575-109">Remarks</span></span>  
 <span data-ttu-id="c9575-110">`#elif`kullanmaya eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="c9575-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="c9575-111">Her `#elif` `#if` biri bir [#endif](./preprocessor-endif.md)gerektirdiğinden, `#elif` bir eşleneme `#endif`olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9575-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="c9575-112">Nasıl [#if](./preprocessor-if.md) kullanılacağına bir örnek `#elif`için #if bakın.</span><span class="sxs-lookup"><span data-stu-id="c9575-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9575-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9575-113">See also</span></span>

- [<span data-ttu-id="c9575-114">C# Referans</span><span class="sxs-lookup"><span data-stu-id="c9575-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c9575-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c9575-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c9575-116">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="c9575-116">C# Preprocessor Directives</span></span>](./index.md)
