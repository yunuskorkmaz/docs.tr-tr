---
title: "Döngüler: while...do İfadesi (F#)"
description: "Bkz. nasıl while... yapmak ifadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 6a186d75dcda383764949c2cd3b09bc9e3d1080a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="fdc45-104">Döngüler: while...do İfadesi</span><span class="sxs-lookup"><span data-stu-id="fdc45-104">Loops: while...do Expression</span></span>

<span data-ttu-id="fdc45-105">`while...do` İfadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdc45-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="fdc45-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdc45-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="fdc45-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdc45-107">Remarks</span></span>
<span data-ttu-id="fdc45-108">*Test ifade* etkinleştirilmişse; değerlendirilir `true`, *gövde ifade* yürütülür ve test deyim yeniden değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fdc45-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="fdc45-109">*Gövde ifade* türünde olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="fdc45-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="fdc45-110">Test ifade ise `false`, yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="fdc45-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="fdc45-111">Aşağıdaki örnek kullanımını göstermektedir `while...do` ifade.</span><span class="sxs-lookup"><span data-stu-id="fdc45-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="fdc45-112">Önceki kod çıkışı biri son 10'dur bir rastgele sayı 1 ve 20 arasında akışıdır.</span><span class="sxs-lookup"><span data-stu-id="fdc45-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="fdc45-113">Kullanabileceğiniz `while...do` sequence ifadeleri ve diğer hesaplama ifadeleri özelleştirilmiş bir sürümünü durumda içinde `while...do` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdc45-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="fdc45-114">Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="fdc45-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="fdc45-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdc45-115">See Also</span></span>
[<span data-ttu-id="fdc45-116">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdc45-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="fdc45-117">Döngüler: `for...in` ifade</span><span class="sxs-lookup"><span data-stu-id="fdc45-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="fdc45-118">Döngüler: `for...to` ifade</span><span class="sxs-lookup"><span data-stu-id="fdc45-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
