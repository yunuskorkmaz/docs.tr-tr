---
title: 'Döngüler: while...do İfadesi'
description: Bkz. while... do ifadesi, belirtilen test koşulu true olduğunda yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: f05bdd9f8f4b9446d59f68e1231fb75e18e9b526
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630759"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="57e7b-103">Döngüler: while...do İfadesi</span><span class="sxs-lookup"><span data-stu-id="57e7b-103">Loops: while...do Expression</span></span>

<span data-ttu-id="57e7b-104">`while...do` İfade, belirtilen bir test koşulu doğru olduğunda yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57e7b-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="57e7b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57e7b-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="57e7b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57e7b-106">Remarks</span></span>

<span data-ttu-id="57e7b-107">*Test ifadesi* değerlendirilir; Eğer ise `true`, *gövde ifadesi* yürütülür ve test ifadesi yeniden değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="57e7b-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="57e7b-108">*Body ifadesinin* türü `unit`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57e7b-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="57e7b-109">Test ifadesi ise `false`, yineleme sonlanır.</span><span class="sxs-lookup"><span data-stu-id="57e7b-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="57e7b-110">Aşağıdaki örnek, `while...do` ifadesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="57e7b-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="57e7b-111">Önceki kodun çıktısı, en fazla 10 olan 1 ile 20 arasında rastgele sayıların bir akışıdır.</span><span class="sxs-lookup"><span data-stu-id="57e7b-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="57e7b-112">Dizi ifadelerinde ve `while...do` diğer hesaplama ifadelerinde kullanabilirsiniz, bu durumda `while...do` ifadenin özelleştirilmiş bir sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57e7b-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="57e7b-113">Daha fazla bilgi için bkz. [diziler](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [Hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="57e7b-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57e7b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57e7b-114">See also</span></span>

- [<span data-ttu-id="57e7b-115">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="57e7b-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="57e7b-116">Lerin `for...in`İfadesini</span><span class="sxs-lookup"><span data-stu-id="57e7b-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="57e7b-117">Lerin `for...to`İfadesini</span><span class="sxs-lookup"><span data-stu-id="57e7b-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
