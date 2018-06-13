---
title: 'Özel Durumlar: try...finally İfadesi (F#)'
description: "Bilgi nasıl F # ' try... finally' ifadesi, bir kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak tanır."
ms.date: 05/16/2016
ms.openlocfilehash: a5fdec7b3986fc9a85c34b08d20dc31947c92b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563499"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="8f679-103">Özel Durumlar: try...finally İfadesi</span><span class="sxs-lookup"><span data-stu-id="8f679-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="8f679-104">`try...finally` İfade kod bloğu bir özel durum oluşturursa bile temizleme kodu yürütme olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f679-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="8f679-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f679-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="8f679-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f679-106">Remarks</span></span>
<span data-ttu-id="8f679-107">`try...finally` İfade kod yürütmek için kullanılabilir *İfade2* olup bir özel durum yürütülmesi sırasında oluşturulan bağımsız olarak önceki sözdiziminde *İfade1*.</span><span class="sxs-lookup"><span data-stu-id="8f679-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="8f679-108">Türü *İfade2* tüm ifadenin değerine katılmadığı bir özel durum meydana gelmez, döndürülen türü son değeri *İfade1*.</span><span class="sxs-lookup"><span data-stu-id="8f679-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="8f679-109">Bir özel durum oluştuğunda, bu değer döndürülür ve sonraki eşleşen özel durum işleyici çağrı yığını kurmak için denetim akışı aktarır.</span><span class="sxs-lookup"><span data-stu-id="8f679-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="8f679-110">Hiçbir özel durum işleyicisi bulunursa, program sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="8f679-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="8f679-111">Eşleşen bir işleyici kodu yürütülen veya program sonlandırır, kodda önce `finally` şube gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8f679-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="8f679-112">Aşağıdaki kod kullanımını gösteren `try...finally` ifade.</span><span class="sxs-lookup"><span data-stu-id="8f679-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="8f679-113">Konsola çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="8f679-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="8f679-114">Çıktısını görebileceğiniz gibi dış özel durumun işlendiğini önce akış kapatıldı ve dosya `test.txt` metni içeren `test1`, arabellek atılmış ve özel durum transfer olsa bile diske yazılan gösterir Dış özel durum işleyici denetler.</span><span class="sxs-lookup"><span data-stu-id="8f679-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="8f679-115">Unutmayın `try...with` yapıdır gelen ayrı bir yapı `try...finally` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f679-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="8f679-116">Bu nedenle, kodunuzun her ikisi de gerektiriyorsa bir `with` bloğu ve `finally` bloğu, aşağıdaki kod örneğinde olduğu gibi iki yapıları iç içe gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f679-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="8f679-117">Hesaplama ifadeleri bağlamında sequence ifadeleri ve zaman uyumsuz iş akışları dahil olmak üzere **try... finally** ifadeleri, özel bir uygulama olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f679-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="8f679-118">Daha fazla bilgi için bkz: [hesaplama ifadeleri](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8f679-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="8f679-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f679-119">See Also</span></span>
[<span data-ttu-id="8f679-120">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="8f679-120">Exception Handling</span></span>](index.md)

[<span data-ttu-id="8f679-121">Özel durumlar: `try...with` ifade</span><span class="sxs-lookup"><span data-stu-id="8f679-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
