---
title: 'Döngüler: while...do İfadesi'
description: 'Bkz: nasıl sırada... yapmak ifadesi belirtilen test koşulu true olduğu sürece, yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: d2a77e0bfefe3b6b026012e6b2938ba670326bcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904026"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="32e36-103">Döngüler: while...do İfadesi</span><span class="sxs-lookup"><span data-stu-id="32e36-103">Loops: while...do Expression</span></span>

<span data-ttu-id="32e36-104">`while...do` İfadesi belirtilen test koşulu true olduğu sürece, yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32e36-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>

## <a name="syntax"></a><span data-ttu-id="32e36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32e36-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="32e36-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32e36-106">Remarks</span></span>

<span data-ttu-id="32e36-107">*Test ifade* ise; değerlendirilir `true`, *gövde ifadesi* yürütülür ve test ifade tekrar değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="32e36-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="32e36-108">*Gövde ifadesi* türüne sahip olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="32e36-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="32e36-109">Test ifade ise `false`, yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="32e36-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="32e36-110">Aşağıdaki örnek, kullanımını gösterir `while...do` ifade.</span><span class="sxs-lookup"><span data-stu-id="32e36-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="32e36-111">Önceki kodun çıktısı biri son 10'dur bir rastgele sayı 1 ile 20 arasında akışıdır.</span><span class="sxs-lookup"><span data-stu-id="32e36-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

> [!NOTE]
> <span data-ttu-id="32e36-112">Kullanabileceğiniz `while...do` sequence ifadeleri ve diğer hesaplama ifadeleri, özelleştirilmiş bir sürümünü durumda `while...do` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32e36-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="32e36-113">Daha fazla bilgi için [dizileri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="32e36-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32e36-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32e36-114">See also</span></span>

- [<span data-ttu-id="32e36-115">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="32e36-115">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="32e36-116">Döngüler: `for...in` İfade</span><span class="sxs-lookup"><span data-stu-id="32e36-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="32e36-117">Döngüler: `for...to` İfade</span><span class="sxs-lookup"><span data-stu-id="32e36-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)