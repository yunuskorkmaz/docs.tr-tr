---
title: "Geç Hesaplamalar (F#)"
description: "F # geç hesaplamalar uygulamalarınızı ve kitaplıkları performansını geliştirebilirsiniz nasıl öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3499293e-1d53-4b02-b764-f687fbdaa7fe
ms.openlocfilehash: 984c96ab68a8919e2382eefe8260b07f191027dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lazy-computations"></a><span data-ttu-id="38c37-104">Geç Hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="38c37-104">Lazy Computations</span></span>

<span data-ttu-id="38c37-105">*Geç hesaplamalar* hemen değerlendirilmez, ancak sonuç gerektiğinde yerine değerlendirilir hesaplamalar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="38c37-105">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="38c37-106">Bu, kodunuzu performansının artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="38c37-106">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="38c37-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38c37-107">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="38c37-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38c37-108">Remarks</span></span>

<span data-ttu-id="38c37-109">Önceki sözdiziminde *ifade* yalnızca bir sonuç gerekli olduğunda değerlendirilen kodu ve *tanımlayıcısı* sonucu depolayan bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="38c37-109">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="38c37-110">Değer [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), burada gerçek türü için kullanılan `'T` ifade sonucundan belirlenir.</span><span class="sxs-lookup"><span data-stu-id="38c37-110">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="38c37-111">Geç hesaplamalar hesaplamanın sonucu gerekli durumlar için yürütmesi kısıtlayarak performansını artırmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="38c37-111">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="38c37-112">Gerçekleştirilecek hesaplama zorlamak için yöntemi çağırın `Force`.</span><span class="sxs-lookup"><span data-stu-id="38c37-112">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="38c37-113">`Force`yalnızca bir kez gerçekleştirilmesi yürütme neden olur.</span><span class="sxs-lookup"><span data-stu-id="38c37-113">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="38c37-114">Sonraki çağrılar `Force` aynı sonucu, ancak herhangi bir kod yürütülmez döndürür.</span><span class="sxs-lookup"><span data-stu-id="38c37-114">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="38c37-115">Aşağıdaki kod yavaş hesaplama kullanımını ve kullanımını gösterir `Force`.</span><span class="sxs-lookup"><span data-stu-id="38c37-115">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="38c37-116">Bu kod türünü `result` olan `Lazy<int>`ve `Force` yöntemi döndürür bir `int`.</span><span class="sxs-lookup"><span data-stu-id="38c37-116">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="38c37-117">Geç değerlendirme, ama `Lazy` yazın, sıraları için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38c37-117">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="38c37-118">Daha fazla bilgi için bkz: [sıraları](sequences.md).</span><span class="sxs-lookup"><span data-stu-id="38c37-118">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38c37-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38c37-119">See Also</span></span>

[<span data-ttu-id="38c37-120">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="38c37-120">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="38c37-121">LazyExtensions Modülü</span><span class="sxs-lookup"><span data-stu-id="38c37-121">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
