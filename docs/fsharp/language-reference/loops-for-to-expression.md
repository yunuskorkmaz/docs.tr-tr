---
title: 'Döngüler: for...to İfadesi (F#)'
description: 'Bkz. nasıl F # for... ifade için bir döngü değişken değerlerini aralığında bir döngüde yinelemek için kullanılır.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 95a8960d71c82c01118d2e71479fc0ec5298a02b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forto-expression"></a><span data-ttu-id="781ab-103">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="781ab-103">Loops: for...to Expression</span></span>

<span data-ttu-id="781ab-104">`for...to` İfade Döngü değişkeninin değerini aralığında bir döngüde yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="781ab-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="781ab-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="781ab-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="781ab-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="781ab-106">Remarks</span></span>
<span data-ttu-id="781ab-107">Tanımlayıcı türü türünden algılanır *Başlat* ve *son* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="781ab-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="781ab-108">Bu deyimler türlerinde 32 bit tamsayı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="781ab-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="781ab-109">Teknik olarak bir ifade rağmen `for...to` daha geleneksel deyimi kesinlik temelli bir programlama dili gibi.</span><span class="sxs-lookup"><span data-stu-id="781ab-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="781ab-110">Dönüş türü için *gövde ifade* olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="781ab-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="781ab-111">Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.</span><span class="sxs-lookup"><span data-stu-id="781ab-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="781ab-112">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="781ab-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="781ab-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="781ab-113">See Also</span></span>
[<span data-ttu-id="781ab-114">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="781ab-114">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="781ab-115">Döngüler: `for...in` ifade</span><span class="sxs-lookup"><span data-stu-id="781ab-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="781ab-116">Döngüler: `while...do` ifade</span><span class="sxs-lookup"><span data-stu-id="781ab-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
