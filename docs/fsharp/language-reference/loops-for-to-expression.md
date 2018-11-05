---
title: 'Döngüler: for...to İfadesi (F#)'
description: Bkz. nasıl F# for... ifade bir döngüde bir dizi bir döngü değişkeninin değerleri üzerinden yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 8160fd30c4f3afe8bb6b58f468802ef1c0ef32ee
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43800475"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="0ec44-103">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="0ec44-103">Loops: for...to Expression</span></span>

<span data-ttu-id="0ec44-104">`for...to` İfadesi, bir dizi bir döngü değişkeninin değerleri üzerinden bir döngü içinde yineleme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ec44-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ec44-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ec44-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="0ec44-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ec44-106">Remarks</span></span>

<span data-ttu-id="0ec44-107">Tanımlayıcı türü türünden çıkarılan *Başlat* ve *son* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="0ec44-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="0ec44-108">Bu ifadeler için türler, 32 bit tamsayılar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ec44-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="0ec44-109">Teknik olarak bir ifade rağmen `for...to` daha geleneksel bir kesinlik temelli bir programlama dili deyiminde gibi.</span><span class="sxs-lookup"><span data-stu-id="0ec44-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="0ec44-110">İçin dönüş türü *gövde ifadesi* olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="0ec44-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="0ec44-111">Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.</span><span class="sxs-lookup"><span data-stu-id="0ec44-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="0ec44-112">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="0ec44-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="0ec44-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ec44-113">See also</span></span>

- [<span data-ttu-id="0ec44-114">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0ec44-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0ec44-115">Döngüler: `for...in` ifadesi</span><span class="sxs-lookup"><span data-stu-id="0ec44-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="0ec44-116">Döngüler: `while...do` ifadesi</span><span class="sxs-lookup"><span data-stu-id="0ec44-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
