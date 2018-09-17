---
title: Geç Hesaplamalar (F#)
description: 'F # geç hesaplamalar uygulamalar ve kitaplıklar performansını nasıl artırabileceğinizi öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698216"
---
# <a name="lazy-computations"></a><span data-ttu-id="5f0e3-103">Geç Hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="5f0e3-103">Lazy Computations</span></span>

<span data-ttu-id="5f0e3-104">*Geç hesaplamalar* hemen değerlendirilmeyen, ancak bunun yerine sonucu gerektiğinde değerlendirilir hesaplamalar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="5f0e3-105">Bu, kodunuzun performansını artırmak için yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f0e3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f0e3-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="5f0e3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f0e3-107">Remarks</span></span>

<span data-ttu-id="5f0e3-108">Önceki sözdiziminde, *ifade* kod, yalnızca bir sonuç gerekli olduğunda değerlendirilir ve *tanımlayıcı* sonucu depolayan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="5f0e3-109">Değer türünde [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), burada gerçek türü için kullanılan `'T` ifadenin sonuç belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="5f0e3-110">Geç hesaplamalar performansını hesaplamanın içinde bir sonuç gereken durumlar için yürütme kısıtlayarak olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="5f0e3-111">Hesaplama gerçekleştirilmesini zorlamak için yöntemi çağırın. `Force`.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="5f0e3-112">`Force` yalnızca bir kez gerçekleştirilmek üzere yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="5f0e3-113">Yapılan sonraki çağrılar `Force` aynı sonucu, ancak herhangi bir kod Yürütülmeyen döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="5f0e3-114">Aşağıdaki kod, yavaş bir hesaplama kullanımını ve kullanımını göstermektedir `Force`.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="5f0e3-115">Bu kodda, türü `result` olduğu `Lazy<int>`ve `Force` yöntemi döndürür bir `int`.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="5f0e3-116">Geç değerlendirme, ama `Lazy` yazın, sıraları için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="5f0e3-117">Daha fazla bilgi için [dizileri](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="5f0e3-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f0e3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f0e3-118">See also</span></span>

- [<span data-ttu-id="5f0e3-119">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5f0e3-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5f0e3-120">LazyExtensions Modülü</span><span class="sxs-lookup"><span data-stu-id="5f0e3-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
