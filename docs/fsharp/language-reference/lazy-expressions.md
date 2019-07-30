---
title: Gecikmeli İfadeler
description: Yavaş ifadelerin F# uygulamalarınızın ve kitaplıklarınızın performansını nasıl geliştirebileceğinizi öğrenin.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630744"
---
# <a name="lazy-expressions"></a><span data-ttu-id="3e1ce-103">Gecikmeli İfadeler</span><span class="sxs-lookup"><span data-stu-id="3e1ce-103">Lazy Expressions</span></span>

<span data-ttu-id="3e1ce-104">*Lazy ifadeleri* hemen değerlendirilmeyecek ifadelerdir, ancak bunun yerine sonuç gerektiğinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-104">*Lazy expressions* are expressions that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="3e1ce-105">Bu, kodunuzun performansını artırmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e1ce-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e1ce-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="3e1ce-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e1ce-107">Remarks</span></span>

<span data-ttu-id="3e1ce-108">Önceki sözdiziminde *ifade* , yalnızca bir sonuç gerekli olduğunda değerlendirilen koddur ve *tanımlayıcı* sonucu depolayan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="3e1ce-109">Değer, için `'T` kullanılan gerçek [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)türün ifadenin sonucundan belirlendiği türdür.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="3e1ce-110">Yavaş ifadeler, bir ifadenin yürütülmesini yalnızca bir sonucun gerekli olduğu durumlara göre kısıtlayarak performansı iyileştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-110">Lazy expressions enable you to improve performance by restricting the execution of an expressions to only those situations in which a result is needed.</span></span>

<span data-ttu-id="3e1ce-111">İfadeleri gerçekleştirilecek şekilde zorlamak için yöntemini `Force`çağırın.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-111">To force the expressions to be performed, you call the method `Force`.</span></span> <span data-ttu-id="3e1ce-112">`Force`yürütmenin yalnızca bir kez gerçekleştirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="3e1ce-113">Sonraki çağrılar `Force` aynı sonucu döndürecek, ancak herhangi bir kod yürütmüyor.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="3e1ce-114">Aşağıdaki kod, geç ifadelerin kullanımını ve `Force`kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-114">The following code illustrates the use of lazy expressions and the use of `Force`.</span></span> <span data-ttu-id="3e1ce-115">`result` Bu kodda, türü `Lazy<int>`, `Force`veyöntemi döndürür. `int`</span><span class="sxs-lookup"><span data-stu-id="3e1ce-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="3e1ce-116">Yavaş değerlendirme, ancak `Lazy` tür değil, diziler için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="3e1ce-117">Daha fazla bilgi için bkz. [diziler](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="3e1ce-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3e1ce-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e1ce-118">See also</span></span>

- [<span data-ttu-id="3e1ce-119">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3e1ce-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3e1ce-120">LazyExtensions modülü</span><span class="sxs-lookup"><span data-stu-id="3e1ce-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
