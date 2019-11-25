---
title: 'Döngüler: for...to İfadesi'
description: F# İçin bkz.... to ifadesi bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 882b6e48dd09efcb57f7ef2f419e68a6c43393a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283909"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="75071-103">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="75071-103">Loops: for...to Expression</span></span>

<span data-ttu-id="75071-104">`for...to` ifadesi bir döngü değişkeninin bir dizi değeri üzerinde bir döngüde yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75071-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="75071-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75071-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="75071-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75071-106">Remarks</span></span>

<span data-ttu-id="75071-107">Tanımlayıcının türü *Başlangıç* ve *bitiş* ifadelerinin türünden algılanır.</span><span class="sxs-lookup"><span data-stu-id="75071-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="75071-108">Bu ifadeler için türler 32 bitlik tamsayılar olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75071-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="75071-109">Teknik olarak bir ifade, `for...to`, bir zorunlu programlama dilinde geleneksel bir ifadeye benzer.</span><span class="sxs-lookup"><span data-stu-id="75071-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="75071-110">*Body ifadesi* için dönüş türü `unit`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75071-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="75071-111">Aşağıdaki örneklerde `for...to` ifadesinin çeşitli kullanımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75071-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="75071-112">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="75071-112">The output of the previous code is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="75071-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75071-113">See also</span></span>

- [<span data-ttu-id="75071-114">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="75071-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="75071-115">Döngüler: `for...in` Ifade</span><span class="sxs-lookup"><span data-stu-id="75071-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="75071-116">Döngüler: `while...do` Ifade</span><span class="sxs-lookup"><span data-stu-id="75071-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
