---
title: Satır İçi İşlevler
description: Doğrudan çağıran kodun içinde F# tümleşik olan satır içi işlevleri nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 2830d1ada5b3005c3fcae975a44e85a7c84554f7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630685"
---
# <a name="inline-functions"></a><span data-ttu-id="36142-103">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="36142-103">Inline Functions</span></span>

<span data-ttu-id="36142-104">*Satır içi işlevler* doğrudan çağıran koda tümleştirilen işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="36142-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>

## <a name="using-inline-functions"></a><span data-ttu-id="36142-105">Satır Içi Işlevleri kullanma</span><span class="sxs-lookup"><span data-stu-id="36142-105">Using Inline Functions</span></span>

<span data-ttu-id="36142-106">Statik tür parametreleri kullandığınızda, tür parametrelerine göre parametreli olan tüm işlevler satır içi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36142-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="36142-107">Bu, derleyicinin bu tür parametrelerini çözümleyebilecek olmasını güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="36142-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="36142-108">Sıradan genel tür parametreleri kullandığınızda böyle bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="36142-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="36142-109">Üye kısıtlamaları kullanımını etkinleştirmenin dışında, satır içi işlevler kodu iyileştirmek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="36142-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="36142-110">Ancak, satır içi işlevlerin aşırı kullanımı, kodunuzun, derleyici iyileştirmeleri ve kitaplık işlevlerinin uygulanması için değişikliklere daha az dayanıklı olmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="36142-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="36142-111">Bu nedenle, diğer en iyi duruma getirme tekniklerini denemediğiniz takdirde en iyi duruma getirme için satır içi işlevleri kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="36142-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="36142-112">İşlevin veya yöntemin satır içi yapılması bazen performansı iyileştirebilir, ancak bu her zaman durum değildir.</span><span class="sxs-lookup"><span data-stu-id="36142-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="36142-113">Bu nedenle, belirli bir işlevi satır içi olarak yapmanın aslında pozitif bir etkiye sahip olduğunu doğrulamak için performans ölçümlerini da kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="36142-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="36142-114">`inline` Değiştirici, en üst düzeydeki işlevlere, modül düzeyinde veya bir sınıftaki yöntem düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="36142-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="36142-115">Aşağıdaki kod örneği, en üst düzeydeki bir satır içi işlev, bir satır içi örnek yöntemi ve bir satır içi statik yöntem gösterir.</span><span class="sxs-lookup"><span data-stu-id="36142-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="36142-116">Satır içi Işlevler ve tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="36142-116">Inline Functions and Type Inference</span></span>

<span data-ttu-id="36142-117">' Nin `inline` varlığı tür çıkarımı etkiler.</span><span class="sxs-lookup"><span data-stu-id="36142-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="36142-118">Bunun nedeni, satır içi işlevlerin statik olarak çözümlenen tür parametrelerine sahip olmasından kaynaklanır, ancak satır içi olmayan işlevler olamaz.</span><span class="sxs-lookup"><span data-stu-id="36142-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="36142-119">Aşağıdaki kod örneğinde, statik olarak çözümlenen bir `inline` tür parametresine sahip bir işlev kullandığınız için `float` , dönüştürme işleci olan bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="36142-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="36142-120">Değiştirici olmadan, tür çıkarımı işlevi belirli bir tür almaya zorlar, bu durumda `int`. `inline`</span><span class="sxs-lookup"><span data-stu-id="36142-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="36142-121">Ancak `inline` değiştiriciyle işlev statik olarak çözümlenen bir tür parametresine sahip olacak şekilde de algılanır.</span><span class="sxs-lookup"><span data-stu-id="36142-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="36142-122">`inline` Değiştiriciyle, tür şu şekilde algılanır:</span><span class="sxs-lookup"><span data-stu-id="36142-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="36142-123">Bu, işlevin **float**öğesine dönüştürmeyi destekleyen herhangi bir türü kabul ettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="36142-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>

## <a name="see-also"></a><span data-ttu-id="36142-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36142-124">See also</span></span>

- [<span data-ttu-id="36142-125">İşlevler</span><span class="sxs-lookup"><span data-stu-id="36142-125">Functions</span></span>](index.md)
- [<span data-ttu-id="36142-126">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="36142-126">Constraints</span></span>](../generics/constraints.md)
- [<span data-ttu-id="36142-127">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="36142-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
