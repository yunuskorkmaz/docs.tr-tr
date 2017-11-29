---
title: "Döngüler: for...to İfadesi (F#)"
description: "Bkz. nasıl F # for... ifade için bir döngü değişken değerlerini aralığında bir döngüde yinelemek için kullanılır."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e14c38d9-b1ef-4b7f-be9a-fb6ef6708e02
ms.openlocfilehash: 1a1d71d30b5e87e4691a78acd5032de9419399db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forto-expression"></a><span data-ttu-id="55590-104">Döngüler: for...to İfadesi</span><span class="sxs-lookup"><span data-stu-id="55590-104">Loops: for...to Expression</span></span>

<span data-ttu-id="55590-105">`for...to` İfade Döngü değişkeninin değerini aralığında bir döngüde yinelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55590-105">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>


## <a name="syntax"></a><span data-ttu-id="55590-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55590-106">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="55590-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55590-107">Remarks</span></span>
<span data-ttu-id="55590-108">Tanımlayıcı türü türünden algılanır *Başlat* ve *son* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="55590-108">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="55590-109">Bu deyimler türlerinde 32 bit tamsayı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="55590-109">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="55590-110">Teknik olarak bir ifade rağmen `for...to` daha geleneksel deyimi kesinlik temelli bir programlama dili gibi.</span><span class="sxs-lookup"><span data-stu-id="55590-110">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="55590-111">Dönüş türü için *gövde ifade* olmalıdır `unit`.</span><span class="sxs-lookup"><span data-stu-id="55590-111">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="55590-112">Aşağıdaki örnekler çeşitli kullanımları `for...to` ifade.</span><span class="sxs-lookup"><span data-stu-id="55590-112">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="55590-113">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="55590-113">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="55590-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55590-114">See Also</span></span>
[<span data-ttu-id="55590-115">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="55590-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="55590-116">Döngüler: `for...in` ifade</span><span class="sxs-lookup"><span data-stu-id="55590-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="55590-117">Döngüler: `while...do` ifade</span><span class="sxs-lookup"><span data-stu-id="55590-117">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
