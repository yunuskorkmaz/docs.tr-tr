---
title: "Satır İçi İşlevler (F#)"
description: "Doğrudan çağırma koda tümleşik F # satır içi işlevler kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a><span data-ttu-id="f5976-104">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="f5976-104">Inline Functions</span></span>

<span data-ttu-id="f5976-105">*Satır içi işlevler* doğrudan çağıran koda tümleşik işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="f5976-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="f5976-106">Satır içi işlevler kullanma</span><span class="sxs-lookup"><span data-stu-id="f5976-106">Using Inline Functions</span></span>
<span data-ttu-id="f5976-107">Statik tür parametreleri kullandığınızda, türü parametrelere göre parametreli hiçbir işlev satır içi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5976-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="f5976-108">Bu, bu tür parametreleri derleyici çözebilirsiniz garanti eder.</span><span class="sxs-lookup"><span data-stu-id="f5976-108">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="f5976-109">Sıradan genel tür parametreleri kullandığınızda, bu tür bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="f5976-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="f5976-110">Üye kısıtlamaları kullanımını etkinleştirmenin dışında satır içi işlevler kodu en iyi duruma getirme yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5976-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="f5976-111">Ancak, satır içi işlevlerin aşırı kullanımı kodunuzu derleyici en iyi duruma getirme ve kitaplık işlevleri uyarlamasını değişiklikler daha az dayanıklı olması neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5976-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="f5976-112">Bu nedenle, diğer tüm iyileştirme tekniklerini denediyseniz sürece satır içi işlevler için en iyi duruma getirme yapmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f5976-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="f5976-113">Bir işlev veya yöntem satır içi yapma performansı artırır ancak, her zaman geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="f5976-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="f5976-114">Bu nedenle, tüm verilen işlev satır içi yapmadan aslında pozitif bir etkiye sahip olup olmadığını doğrulamak için performans ölçümleri kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f5976-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="f5976-115">`inline` Değiştiricisi işlevler en üst düzeyinde, modülü düzeyinde ya da bir sınıf yöntemi düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="f5976-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="f5976-116">Aşağıdaki kod örneği, en üst düzeyinde, satır içi örnek yöntemi ve satır içi statik yöntemi satır içi işlev gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5976-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="f5976-117">Satır içi işlevler ve tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="f5976-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="f5976-118">Varlığını `inline` etkiler çıkarım yazın.</span><span class="sxs-lookup"><span data-stu-id="f5976-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="f5976-119">Satır içi işlevler statik olarak çözümlenmiş tür parametreleri, çünkü olmayan satır içi işlevler edilemez ise.</span><span class="sxs-lookup"><span data-stu-id="f5976-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="f5976-120">Aşağıdaki kod örneğinde bir durumu gösterir nerede `inline` statik olarak çözümlenmiş tür parametresi olan bir işlev kullandığından yararlıdır `float` dönüşüm işleci.</span><span class="sxs-lookup"><span data-stu-id="f5976-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="f5976-121">Olmadan `inline` değiştiricisi, tür çıkarımı zorlar belirli bir türdeki bu durumda yapılacak işlevi `int`.</span><span class="sxs-lookup"><span data-stu-id="f5976-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="f5976-122">Ancak `inline` değiştiricisi, işlevi bir statik olarak çözümlenmiş tür parametreye sahip olayla de.</span><span class="sxs-lookup"><span data-stu-id="f5976-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="f5976-123">İle `inline` değiştiricisi, türü olayla aşağıdaki olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="f5976-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="f5976-124">Bu işlev bir dönüştürme destekleyen herhangi bir türü kabul eden anlamına gelir **float**.</span><span class="sxs-lookup"><span data-stu-id="f5976-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="f5976-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5976-125">See Also</span></span>
[<span data-ttu-id="f5976-126">İşlevler</span><span class="sxs-lookup"><span data-stu-id="f5976-126">Functions</span></span>](index.md)

[<span data-ttu-id="f5976-127">Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="f5976-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="f5976-128">Statik olarak çözümlenmiş tür parametreleri</span><span class="sxs-lookup"><span data-stu-id="f5976-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
