---
title: 'Özyinelemeli İşlevler: rec Anahtar Sözcüğü (F#)'
description: "'F # rec' anahtar sözcüğü bir özyinelemeli işlev tanımlamak için 'let' anahtar sözcüğü ile nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 5aab6ed8ab0fc3c0f0bcfc93c3ce6518ec53254f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562684"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="de63e-103">Özyinelemeli İşlevler: rec Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="de63e-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="de63e-104">`rec` Anahtar sözcüğü ile birlikte kullanılır `let` özyinelemeli işlev tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="de63e-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="de63e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de63e-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="de63e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de63e-106">Remarks</span></span>

<span data-ttu-id="de63e-107">Özyinelemeli İşlevler, kendileri çağıran İşlevler F # dilinde açıkça tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="de63e-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="de63e-108">Bu tanımlanıyorsa tanımlayıcısı işlev kapsamında kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="de63e-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="de63e-109">Aşağıdaki kod hesaplar bir özyinelemeli işlev göstermektedir *n*<sup>th</sup> Fibonacci sayı.</span><span class="sxs-lookup"><span data-stu-id="de63e-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="de63e-110">Yeniden hesaplama yapmayı daha önce hesaplanan değerler içerdiğinden, yukarıdaki kod bellek ve işlemci zamanı kısıp uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="de63e-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="de63e-111">Yöntem türü içinde dolaylı olarak özyinelemelidir; eklemenize gerek yoktur `rec` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="de63e-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="de63e-112">Sınıflardaki let bağlamaları örtülü olarak özyinelemeli değildir.</span><span class="sxs-lookup"><span data-stu-id="de63e-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="de63e-113">Karşılıklı özyinelemeli İşlevler</span><span class="sxs-lookup"><span data-stu-id="de63e-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="de63e-114">Bazen işlevlerdir *karşılıklı özyinelemeli*, çağrıları burada bir işlevi çağırır sırayla çağrıları herhangi bir sayıda ile ilk çağıran başka arasında bir daire, form anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="de63e-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="de63e-115">Bu tür işlevleri bir araya tanımlamalısınız `let` kullanarak binding `and` birbirine bağlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="de63e-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="de63e-116">Aşağıdaki örnek iki birbirini gösterir özyinelemeli işlevler.</span><span class="sxs-lookup"><span data-stu-id="de63e-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="de63e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de63e-117">See also</span></span>

- [<span data-ttu-id="de63e-118">İşlevler</span><span class="sxs-lookup"><span data-stu-id="de63e-118">Functions</span></span>](index.md)
