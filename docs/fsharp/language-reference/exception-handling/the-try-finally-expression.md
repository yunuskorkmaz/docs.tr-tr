---
title: 'Özel durumlar: try...finally İfadesi'
description: F# ' TRY... finally ' ifadesi bir kod bloğu özel durum oluşturursa bile Temizleme kodunu yürütmenize olanak sağlar.
ms.date: 05/16/2016
ms.openlocfilehash: 03fbda1ef5d55560232f0217f603fc04c0af0eb4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630281"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="2aa8f-103">Özel durumlar: try...finally İfadesi</span><span class="sxs-lookup"><span data-stu-id="2aa8f-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="2aa8f-104">İfade `try...finally` , bir kod bloğu özel durum oluşturursa bile temizleme kodu çalıştırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="2aa8f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2aa8f-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="2aa8f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2aa8f-106">Remarks</span></span>

<span data-ttu-id="2aa8f-107">İfadesi, *İfade1*öğesinin yürütülmesi sırasında bir özel durumun oluşturulup oluşturulmadığına bakılmaksızın, Önceki sözdiziminde İfade2 içindeki kodu yürütmek için kullanılabilir. `try...finally`</span><span class="sxs-lookup"><span data-stu-id="2aa8f-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="2aa8f-108">*Deyim2* türü tüm ifadenin değerine katkıda bulunmaz; bir özel durum gerçekleşmediğinde döndürülen tür *İfade1*' deki son değerdir.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="2aa8f-109">Bir özel durum oluştuğunda, hiçbir değer döndürülmez ve denetim akışı, çağrı yığınını yukarı eşleşen bir sonraki özel durum işleyicisine aktarır.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="2aa8f-110">Hiçbir özel durum işleyici bulunmazsa program sonlanır.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="2aa8f-111">Eşleşen bir işleyicisindeki kod yürütülmeden veya program sonlandırıldığında, `finally` daldaki kod yürütülür.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="2aa8f-112">Aşağıdaki kod, `try...finally` ifadesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="2aa8f-113">Konsola giden çıkış aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="2aa8f-114">Çıktıdan görebileceğiniz gibi, akış, dıştaki özel durum işlendikten önce kapatılmıştır ve dosya `test.txt` , aktarılan özel durum olsa bile, arabelleklerin temizlendiğini ve diske yazıldığını belirten metni `test1`içerir. dış özel durum işleyicisine denetim.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="2aa8f-115">Yapının yapıdan ayrı bir yapı `try...finally` olduğunu unutmayın. `try...with`</span><span class="sxs-lookup"><span data-stu-id="2aa8f-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="2aa8f-116">Bu nedenle, kodunuz hem `with` blok `finally` hem de blok gerektiriyorsa, aşağıdaki kod örneğinde olduğu gibi iki yapıları iç içe almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="2aa8f-117">Sıra ifadeleri ve zaman uyumsuz iş akışları dahil hesaplama ifadeleri bağlamında, **deneyin... finally** ifadeleri özel bir uygulamaya sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="2aa8f-118">Daha fazla bilgi için bkz. [Hesaplama ifadeleri](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="2aa8f-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2aa8f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2aa8f-119">See also</span></span>

- [<span data-ttu-id="2aa8f-120">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="2aa8f-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="2aa8f-121">Özel Durumlar: `try...with` İfade</span><span class="sxs-lookup"><span data-stu-id="2aa8f-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
