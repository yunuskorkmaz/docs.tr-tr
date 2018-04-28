---
title: 'Döngüler: while...do İfadesi (F#)'
description: 'Bkz: nasıl... sırada yapmak ifadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 847f99faab42c8805bd788e42e3f24ad6369ba52
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="35e18-103">Döngüler: while...do İfadesi</span><span class="sxs-lookup"><span data-stu-id="35e18-103">Loops: while...do Expression</span></span>

<span data-ttu-id="35e18-104">`while...do` İfadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35e18-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="35e18-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35e18-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="35e18-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35e18-106">Remarks</span></span>
<span data-ttu-id="35e18-107">*Test ifade* etkinleştirilmişse; değerlendirilir `true`, *gövde ifade* yürütülür ve test deyim yeniden değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="35e18-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="35e18-108">*Gövde ifade* türünde olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="35e18-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="35e18-109">Test ifade ise `false`, yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="35e18-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="35e18-110">Aşağıdaki örnek kullanımını göstermektedir `while...do` ifade.</span><span class="sxs-lookup"><span data-stu-id="35e18-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="35e18-111">Önceki kod çıkışı biri son 10'dur bir rastgele sayı 1 ve 20 arasında akışıdır.</span><span class="sxs-lookup"><span data-stu-id="35e18-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="35e18-112">Kullanabileceğiniz `while...do` sequence ifadeleri ve diğer hesaplama ifadeleri özelleştirilmiş bir sürümünü durumda içinde `while...do` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35e18-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="35e18-113">Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="35e18-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="35e18-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="35e18-114">See Also</span></span>
[<span data-ttu-id="35e18-115">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="35e18-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="35e18-116">Döngüler: `for...in` ifade</span><span class="sxs-lookup"><span data-stu-id="35e18-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="35e18-117">Döngüler: `for...to` ifade</span><span class="sxs-lookup"><span data-stu-id="35e18-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
