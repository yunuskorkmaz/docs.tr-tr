---
title: 'Döngüler: while...do İfadesi (F#)'
description: 'Bkz: nasıl... sırada yapmak ifadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: e3198246e44bbb11b226f04da6795f3da22626e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562238"
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="4bb4d-103">Döngüler: while...do İfadesi</span><span class="sxs-lookup"><span data-stu-id="4bb4d-103">Loops: while...do Expression</span></span>

<span data-ttu-id="4bb4d-104">`while...do` İfadesi, belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="4bb4d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bb4d-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="4bb4d-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bb4d-106">Remarks</span></span>
<span data-ttu-id="4bb4d-107">*Test ifade* etkinleştirilmişse; değerlendirilir `true`, *gövde ifade* yürütülür ve test deyim yeniden değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="4bb4d-108">*Gövde ifade* türünde olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="4bb4d-109">Test ifade ise `false`, yineleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="4bb4d-110">Aşağıdaki örnek kullanımını göstermektedir `while...do` ifade.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="4bb4d-111">Önceki kod çıkışı biri son 10'dur bir rastgele sayı 1 ve 20 arasında akışıdır.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="4bb4d-112">Kullanabileceğiniz `while...do` sequence ifadeleri ve diğer hesaplama ifadeleri özelleştirilmiş bir sürümünü durumda içinde `while...do` ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="4bb4d-113">Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [hesaplama ifadeleri](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4bb4d-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="4bb4d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4bb4d-114">See Also</span></span>
[<span data-ttu-id="4bb4d-115">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4bb4d-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4bb4d-116">Döngüler: `for...in` ifade</span><span class="sxs-lookup"><span data-stu-id="4bb4d-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="4bb4d-117">Döngüler: `for...to` ifade</span><span class="sxs-lookup"><span data-stu-id="4bb4d-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
