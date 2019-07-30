---
title: 'Döngüler: for...to İfadesi'
description: F# İçin bkz.... to ifadesi bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 910c04aa4ea6b2c637dcad147347c1c317b5e0c0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626620"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="22a8b-103">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="22a8b-103">Loops: for...to Expression</span></span>

<span data-ttu-id="22a8b-104">İfade `for...to` , bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22a8b-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="22a8b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22a8b-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="22a8b-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22a8b-106">Remarks</span></span>

<span data-ttu-id="22a8b-107">Tanımlayıcının türü *Başlangıç* ve *bitiş* ifadelerinin türünden algılanır.</span><span class="sxs-lookup"><span data-stu-id="22a8b-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="22a8b-108">Bu ifadeler için türler 32 bitlik tamsayılar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22a8b-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="22a8b-109">Teknik olarak bir ifade, `for...to` bir zorunlu programlama dilinde geleneksel bir ifadeye benzer.</span><span class="sxs-lookup"><span data-stu-id="22a8b-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="22a8b-110">*Body ifadesi* `unit`için dönüş türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22a8b-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="22a8b-111">Aşağıdaki örneklerde, `for...to` ifadesinin çeşitli kullanımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="22a8b-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="22a8b-112">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="22a8b-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="22a8b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22a8b-113">See also</span></span>

- [<span data-ttu-id="22a8b-114">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="22a8b-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="22a8b-115">Lerin `for...in`İfadesini</span><span class="sxs-lookup"><span data-stu-id="22a8b-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="22a8b-116">Lerin `while...do`İfadesini</span><span class="sxs-lookup"><span data-stu-id="22a8b-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
