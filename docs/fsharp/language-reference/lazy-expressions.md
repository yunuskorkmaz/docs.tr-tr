---
title: Gecikmeli İfadeler
description: 'F # yavaş ifadelerinin uygulamalarınızın ve kitaplıklarınızın performansını nasıl geliştirebileceğinizi öğrenin.'
ms.date: 08/15/2020
ms.openlocfilehash: 0b8496467295ce6793f80c341af88bb1819f4a47
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425509"
---
# <a name="lazy-expressions"></a><span data-ttu-id="13bb0-103">Gecikmeli İfadeler</span><span class="sxs-lookup"><span data-stu-id="13bb0-103">Lazy Expressions</span></span>

<span data-ttu-id="13bb0-104">*Lazy ifadeleri* hemen değerlendirilmeyecek ifadelerdir, ancak bunun yerine sonuç gerektiğinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="13bb0-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="13bb0-105">Bu, kodunuzun performansını artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="13bb0-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="13bb0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="13bb0-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="13bb0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13bb0-107">Remarks</span></span>

<span data-ttu-id="13bb0-108">Önceki sözdiziminde *ifade* , yalnızca bir sonuç gerekli olduğunda değerlendirilen koddur ve *tanımlayıcı* sonucu depolayan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="13bb0-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="13bb0-109">Değer `Lazy<'T>` , için kullanılan gerçek türün `'T` ifadenin sonucundan belirlendiği türdür.</span><span class="sxs-lookup"><span data-stu-id="13bb0-109">The value is of type `Lazy<'T>`, where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="13bb0-110">Yavaş ifadeler, bir ifadenin yürütülmesini yalnızca bir sonucun gerekli olduğu durumlara göre kısıtlayarak performansı iyileştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="13bb0-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="13bb0-111">İfadeleri gerçekleştirilecek şekilde zorlamak için yöntemini çağırın `Force` .</span><span class="sxs-lookup"><span data-stu-id="13bb0-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="13bb0-112">`Force` yürütmenin yalnızca bir kez gerçekleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="13bb0-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="13bb0-113">Sonraki çağrılar `Force` aynı sonucu döndürecek, ancak herhangi bir kod yürütmüyor.</span><span class="sxs-lookup"><span data-stu-id="13bb0-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="13bb0-114">Aşağıdaki kod, geç ifadelerin kullanımını ve kullanımını gösterir `Force` .</span><span class="sxs-lookup"><span data-stu-id="13bb0-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="13bb0-115">Bu kodda, türü, `result` `Lazy<int>` ve `Force` yöntemi döndürür `int` .</span><span class="sxs-lookup"><span data-stu-id="13bb0-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="13bb0-116">Yavaş değerlendirme, ancak tür değil, `Lazy` diziler için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13bb0-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="13bb0-117">Daha fazla bilgi için bkz. [diziler](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="13bb0-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13bb0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13bb0-118">See also</span></span>

- [<span data-ttu-id="13bb0-119">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="13bb0-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="13bb0-120">LazyExtensions modülü</span><span class="sxs-lookup"><span data-stu-id="13bb0-120">LazyExtensions module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-lazyextensions.html)
