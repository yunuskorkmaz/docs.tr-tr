---
title: "Özel Durumlar: try...finally İfadesi (F#)"
description: "Bilgi nasıl F # ' try... finally' ifadesi, bir kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak tanır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="2a76c-104">Özel Durumlar: try...finally İfadesi</span><span class="sxs-lookup"><span data-stu-id="2a76c-104">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="2a76c-105">`try...finally` İfade kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a76c-105">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="2a76c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a76c-106">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="2a76c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a76c-107">Remarks</span></span>
<span data-ttu-id="2a76c-108">`try...finally` İfade kod yürütmek için kullanılabilir *İfade2* olup bir özel durum yürütülmesi sırasında oluşturulan bağımsız olarak önceki sözdiziminde *İfade1*.</span><span class="sxs-lookup"><span data-stu-id="2a76c-108">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="2a76c-109">Türü *İfade2* tüm ifadenin değerine katılmadığı bir özel durum meydana gelmez, döndürülen türü son değeri *İfade1*.</span><span class="sxs-lookup"><span data-stu-id="2a76c-109">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="2a76c-110">Bir özel durum oluştuğunda, bu değer döndürülür ve sonraki eşleşen özel durum işleyici çağrı yığını kurmak için denetim akışı aktarır.</span><span class="sxs-lookup"><span data-stu-id="2a76c-110">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="2a76c-111">Hiçbir özel durum işleyicisi bulunursa, program sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="2a76c-111">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="2a76c-112">Eşleşen bir işleyici kodu yürütülen veya program sonlandırır, kodda önce `finally` şube gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2a76c-112">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="2a76c-113">Aşağıdaki kod kullanımını gösteren `try...finally` ifade.</span><span class="sxs-lookup"><span data-stu-id="2a76c-113">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="2a76c-114">Konsola çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="2a76c-114">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="2a76c-115">Çıktısını görebileceğiniz gibi dış özel durumun işlendiğini önce akış kapatıldı ve dosya `test.txt` metni içeren `test1`, arabellek atılmış ve özel durum transfer olsa bile diske yazılan gösterir Dış özel durum işleyici denetler.</span><span class="sxs-lookup"><span data-stu-id="2a76c-115">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="2a76c-116">Unutmayın `try...with` yapıdır gelen ayrı bir yapı `try...finally` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2a76c-116">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="2a76c-117">Bu nedenle, kodunuzun her ikisi de gerektiriyorsa bir `with` bloğu ve `finally` bloğu, aşağıdaki kod örneğinde olduğu gibi iki yapıları iç içe gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a76c-117">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="2a76c-118">Hesaplama ifadeleri bağlamında sequence ifadeleri ve zaman uyumsuz iş akışları dahil olmak üzere **try... finally** ifadeleri, özel bir uygulama olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a76c-118">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="2a76c-119">Daha fazla bilgi için bkz: [hesaplama ifadeleri](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2a76c-119">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="2a76c-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a76c-120">See Also</span></span>
[<span data-ttu-id="2a76c-121">Özel durum işleme</span><span class="sxs-lookup"><span data-stu-id="2a76c-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="2a76c-122">Özel durumlar: `try...with` ifade</span><span class="sxs-lookup"><span data-stu-id="2a76c-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
