---
title: 'Özyinelemeli İşlevler: Rec anahtar sözcüğü (F#)'
description: Bilgi nasıl F# 'rec' anahtar sözcüğü, bir özyinelemeli işlev tanımlamak için 'let' anahtar sözcüğü ile kullanılır.
ms.date: 05/16/2016
ms.openlocfilehash: 0db3ed7f85a1380654f2827b4773985b661589c7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127738"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="ca89f-103">Özyinelemeli İşlevler: Rec anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="ca89f-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="ca89f-104">`rec` Anahtar sözcüğü ile birlikte kullanılır `let` özyinelemeli işlev tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ca89f-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca89f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca89f-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="ca89f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca89f-106">Remarks</span></span>

<span data-ttu-id="ca89f-107">Özyinelemeli İşlevler, kendileri çağıran işlevler açıkça tanımlanır F# dili.</span><span class="sxs-lookup"><span data-stu-id="ca89f-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="ca89f-108">Bu tanımlanıyorsa tanımlayıcısı işlev kapsamında kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ca89f-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="ca89f-109">Aşağıdaki kod hesaplar bir özyinelemeli işlev göstermektedir *n*<sup>th</sup> Fibonacci sayı.</span><span class="sxs-lookup"><span data-stu-id="ca89f-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="ca89f-110">Yeniden hesaplama yapmayı daha önce hesaplanan değerler içerdiğinden, yukarıdaki kod bellek ve işlemci zamanı kısıp uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ca89f-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="ca89f-111">Yöntem türü içinde dolaylı olarak özyinelemelidir; eklemenize gerek yoktur `rec` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ca89f-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="ca89f-112">Sınıflardaki let bağlamaları örtülü olarak özyinelemeli değildir.</span><span class="sxs-lookup"><span data-stu-id="ca89f-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="ca89f-113">Karşılıklı özyinelemeli İşlevler</span><span class="sxs-lookup"><span data-stu-id="ca89f-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="ca89f-114">Bazen işlevlerdir *karşılıklı özyinelemeli*, çağrıları burada bir işlevi çağırır sırayla çağrıları herhangi bir sayıda ile ilk çağıran başka arasında bir daire, form anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ca89f-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="ca89f-115">Bu tür işlevleri bir araya tanımlamalısınız `let` kullanarak binding `and` birbirine bağlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ca89f-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="ca89f-116">Aşağıdaki örnek iki birbirini gösterir özyinelemeli işlevler.</span><span class="sxs-lookup"><span data-stu-id="ca89f-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="ca89f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca89f-117">See also</span></span>

- [<span data-ttu-id="ca89f-118">İşlevler</span><span class="sxs-lookup"><span data-stu-id="ca89f-118">Functions</span></span>](index.md)
