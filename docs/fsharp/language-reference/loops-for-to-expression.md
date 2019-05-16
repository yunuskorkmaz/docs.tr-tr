---
title: 'Döngüler: for...to İfadesi'
description: Bkz. nasıl F# for... ifade bir döngüde bir dizi bir döngü değişkeninin değerleri üzerinden yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 5b7bb9bac659ddf1d457be1ce17e90a2593666de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645243"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="8bed9-103">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="8bed9-103">Loops: for...to Expression</span></span>

<span data-ttu-id="8bed9-104">`for...to` İfadesi, bir dizi bir döngü değişkeninin değerleri üzerinden bir döngü içinde yineleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8bed9-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="8bed9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bed9-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="8bed9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bed9-106">Remarks</span></span>

<span data-ttu-id="8bed9-107">Tanımlayıcı türü türünden çıkarılan *Başlat* ve *son* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="8bed9-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="8bed9-108">Bu ifadeler için türler, 32 bit tamsayılar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bed9-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="8bed9-109">Teknik olarak bir ifade rağmen `for...to` daha geleneksel bir kesinlik temelli bir programlama dili deyiminde gibi.</span><span class="sxs-lookup"><span data-stu-id="8bed9-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="8bed9-110">İçin dönüş türü *gövde ifadesi* olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="8bed9-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="8bed9-111">Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.</span><span class="sxs-lookup"><span data-stu-id="8bed9-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="8bed9-112">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="8bed9-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="8bed9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bed9-113">See also</span></span>

- [<span data-ttu-id="8bed9-114">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8bed9-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8bed9-115">Döngüler: `for...in` İfade</span><span class="sxs-lookup"><span data-stu-id="8bed9-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="8bed9-116">Döngüler: `while...do` İfade</span><span class="sxs-lookup"><span data-stu-id="8bed9-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
