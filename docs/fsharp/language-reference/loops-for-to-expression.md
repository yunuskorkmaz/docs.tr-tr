---
title: 'Döngüler: for...to İfadesi (F#)'
description: 'Bkz. nasıl F # for... ifade için bir döngü değişken değerlerini aralığında bir döngüde yinelemek için kullanılır.'
ms.date: 05/16/2016
ms.openlocfilehash: 841c7d557abc11e0253cb87ab8081cc77671b44b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563408"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="f3bc7-103">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="f3bc7-103">Loops: for...to Expression</span></span>

<span data-ttu-id="f3bc7-104">`for...to` İfade Döngü değişkeninin değerini aralığında bir döngüde yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="f3bc7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3bc7-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="f3bc7-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3bc7-106">Remarks</span></span>
<span data-ttu-id="f3bc7-107">Tanımlayıcı türü türünden algılanır *Başlat* ve *son* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="f3bc7-108">Bu deyimler türlerinde 32 bit tamsayı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="f3bc7-109">Teknik olarak bir ifade rağmen `for...to` daha geleneksel deyimi kesinlik temelli bir programlama dili gibi.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="f3bc7-110">Dönüş türü için *gövde ifade* olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="f3bc7-111">Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="f3bc7-112">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="f3bc7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3bc7-113">See Also</span></span>
[<span data-ttu-id="f3bc7-114">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f3bc7-114">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f3bc7-115">Döngüler: `for...in` ifade</span><span class="sxs-lookup"><span data-stu-id="f3bc7-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="f3bc7-116">Döngüler: `while...do` ifade</span><span class="sxs-lookup"><span data-stu-id="f3bc7-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
