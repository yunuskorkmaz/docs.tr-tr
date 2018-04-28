---
title: Satır İçi İşlevler (F#)
description: 'Doğrudan çağırma koda tümleşik F # satır içi işlevler kullanmayı öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: cb0addd1456af1ab97e249b9c5ece4d9f0818fa3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="inline-functions"></a><span data-ttu-id="dd365-103">Satır İçi İşlevler</span><span class="sxs-lookup"><span data-stu-id="dd365-103">Inline Functions</span></span>

<span data-ttu-id="dd365-104">*Satır içi işlevler* doğrudan çağıran koda tümleşik işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="dd365-104">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="dd365-105">Satır içi işlevler kullanma</span><span class="sxs-lookup"><span data-stu-id="dd365-105">Using Inline Functions</span></span>
<span data-ttu-id="dd365-106">Statik tür parametreleri kullandığınızda, türü parametrelere göre parametreli hiçbir işlev satır içi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd365-106">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="dd365-107">Bu, bu tür parametreleri derleyici çözebilirsiniz garanti eder.</span><span class="sxs-lookup"><span data-stu-id="dd365-107">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="dd365-108">Sıradan genel tür parametreleri kullandığınızda, bu tür bir kısıtlama yoktur.</span><span class="sxs-lookup"><span data-stu-id="dd365-108">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="dd365-109">Üye kısıtlamaları kullanımını etkinleştirmenin dışında satır içi işlevler kodu en iyi duruma getirme yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd365-109">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="dd365-110">Ancak, satır içi işlevlerin aşırı kullanımı kodunuzu derleyici en iyi duruma getirme ve kitaplık işlevleri uyarlamasını değişiklikler daha az dayanıklı olması neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd365-110">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="dd365-111">Bu nedenle, diğer tüm iyileştirme tekniklerini denediyseniz sürece satır içi işlevler için en iyi duruma getirme yapmaktan kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="dd365-111">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="dd365-112">Bir işlev veya yöntem satır içi yapma performansı artırır ancak, her zaman geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="dd365-112">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="dd365-113">Bu nedenle, tüm verilen işlev satır içi yapmadan aslında pozitif bir etkiye sahip olup olmadığını doğrulamak için performans ölçümleri kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="dd365-113">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="dd365-114">`inline` Değiştiricisi işlevler en üst düzeyinde, modülü düzeyinde ya da bir sınıf yöntemi düzeyinde uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="dd365-114">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="dd365-115">Aşağıdaki kod örneği, en üst düzeyinde, satır içi örnek yöntemi ve satır içi statik yöntemi satır içi işlev gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd365-115">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="dd365-116">Satır içi işlevler ve tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="dd365-116">Inline Functions and Type Inference</span></span>
<span data-ttu-id="dd365-117">Varlığını `inline` etkiler çıkarım yazın.</span><span class="sxs-lookup"><span data-stu-id="dd365-117">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="dd365-118">Satır içi işlevler statik olarak çözümlenmiş tür parametreleri, çünkü olmayan satır içi işlevler edilemez ise.</span><span class="sxs-lookup"><span data-stu-id="dd365-118">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="dd365-119">Aşağıdaki kod örneğinde bir durumu gösterir nerede `inline` statik olarak çözümlenmiş tür parametresi olan bir işlev kullandığından yararlıdır `float` dönüşüm işleci.</span><span class="sxs-lookup"><span data-stu-id="dd365-119">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="dd365-120">Olmadan `inline` değiştiricisi, tür çıkarımı zorlar belirli bir türdeki bu durumda yapılacak işlevi `int`.</span><span class="sxs-lookup"><span data-stu-id="dd365-120">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="dd365-121">Ancak `inline` değiştiricisi, işlevi bir statik olarak çözümlenmiş tür parametreye sahip olayla de.</span><span class="sxs-lookup"><span data-stu-id="dd365-121">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="dd365-122">İle `inline` değiştiricisi, türü olayla aşağıdaki olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="dd365-122">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="dd365-123">Bu işlev bir dönüştürme destekleyen herhangi bir türü kabul eden anlamına gelir **float**.</span><span class="sxs-lookup"><span data-stu-id="dd365-123">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="dd365-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd365-124">See Also</span></span>
[<span data-ttu-id="dd365-125">İşlevler</span><span class="sxs-lookup"><span data-stu-id="dd365-125">Functions</span></span>](index.md)

[<span data-ttu-id="dd365-126">Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="dd365-126">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="dd365-127">Statik Olarak Çözümlenmiş Tür Parametreleri</span><span class="sxs-lookup"><span data-stu-id="dd365-127">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
