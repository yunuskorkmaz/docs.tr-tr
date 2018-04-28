---
title: Geç Hesaplamalar (F#)
description: 'F # geç hesaplamalar uygulamalarınızı ve kitaplıkları performansını geliştirebilirsiniz nasıl öğrenin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 72dc5a14a845b52ae2512314d730516ca0cf4b9d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="lazy-computations"></a><span data-ttu-id="cf629-103">Geç Hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="cf629-103">Lazy Computations</span></span>

<span data-ttu-id="cf629-104">*Geç hesaplamalar* hemen değerlendirilmez, ancak sonuç gerektiğinde yerine değerlendirilir hesaplamalar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="cf629-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="cf629-105">Bu, kodunuzu performansının artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf629-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf629-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf629-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="cf629-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf629-107">Remarks</span></span>

<span data-ttu-id="cf629-108">Önceki sözdiziminde *ifade* yalnızca bir sonuç gerekli olduğunda değerlendirilen kodu ve *tanımlayıcısı* sonucu depolayan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="cf629-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="cf629-109">Değer [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), burada gerçek türü için kullanılan `'T` ifade sonucundan belirlenir.</span><span class="sxs-lookup"><span data-stu-id="cf629-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="cf629-110">Geç hesaplamalar hesaplamanın sonucu gerekli durumlar için yürütmesi kısıtlayarak performansını artırmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="cf629-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="cf629-111">Gerçekleştirilecek hesaplama zorlamak için yöntemi çağırın `Force`.</span><span class="sxs-lookup"><span data-stu-id="cf629-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="cf629-112">`Force` yalnızca bir kez gerçekleştirilmesi yürütme neden olur.</span><span class="sxs-lookup"><span data-stu-id="cf629-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="cf629-113">Sonraki çağrılar `Force` aynı sonucu, ancak herhangi bir kod yürütülmez döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf629-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="cf629-114">Aşağıdaki kod yavaş hesaplama kullanımını ve kullanımını gösterir `Force`.</span><span class="sxs-lookup"><span data-stu-id="cf629-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="cf629-115">Bu kod türünü `result` olan `Lazy<int>`ve `Force` yöntemi döndürür bir `int`.</span><span class="sxs-lookup"><span data-stu-id="cf629-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="cf629-116">Geç değerlendirme, ama `Lazy` yazın, sıraları için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf629-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="cf629-117">Daha fazla bilgi için bkz: [sıraları](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="cf629-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf629-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf629-118">See Also</span></span>

[<span data-ttu-id="cf629-119">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cf629-119">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cf629-120">LazyExtensions Modülü</span><span class="sxs-lookup"><span data-stu-id="cf629-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
