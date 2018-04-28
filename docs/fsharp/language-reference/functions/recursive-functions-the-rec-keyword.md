---
title: 'Özyinelemeli İşlevler: rec Anahtar Sözcüğü (F#)'
description: "F # 'rec' anahtar sözcüğü özyinelemeli bir işlev tanımlamak için 'let' anahtar sözcüğü ile nasıl kullanıldığı hakkında bilgi edinin."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1f5302c125605d2186deab0bbeaf2e84cc51edc3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="b5ca3-103">Özyinelemeli İşlevler: rec Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b5ca3-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="b5ca3-104">`rec` Anahtar sözcüğü ile birlikte kullanıldığında `let` özyinelemeli bir işlev tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="b5ca3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5ca3-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b5ca3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5ca3-106">Remarks</span></span>
<span data-ttu-id="b5ca3-107">Özyinelemeli İşlevler, kendileri arama işlevleri açıkça F # dilinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="b5ca3-108">Bu tanımlanıyorsa tanımlayıcı işlevi kapsamında kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="b5ca3-109">Aşağıdaki kod hesaplar bir özyinelemeli işlev gösterir *n*th Fibonacci numarası.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-109">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="b5ca3-110">Önceden hesaplanan değerler recomputation içerdiğinden, gibi Yukarıdaki kod bellek ve işlemci süresini kayıp uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="b5ca3-111">Örtük olarak özyinelemeli türü içinde yöntemleridir; eklemeye gerek yoktur `rec` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="b5ca3-112">Sınıflardaki let bağlamaları örtülü olarak özyinelemeli değildir.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-112">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="b5ca3-113">Karşılıklı özyinelemeli İşlevler</span><span class="sxs-lookup"><span data-stu-id="b5ca3-113">Mutually Recursive Functions</span></span>
<span data-ttu-id="b5ca3-114">Bazen işlevlerdir *karşılıklı özyinelemeli*, çağrıları burada bir işlevi çağırır sırayla çağrıları herhangi bir sayı ile ilk çağıran başka arasında bir daire form anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="b5ca3-115">Bu tür işlevler bir araya tanımlamalısınız `let` kullanarak binding `and` birbirine bağlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="b5ca3-116">Aşağıdaki örnekte iki birbirini gösterir özyinelemeli işlevler.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="b5ca3-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5ca3-117">See Also</span></span>
[<span data-ttu-id="b5ca3-118">İşlevler</span><span class="sxs-lookup"><span data-stu-id="b5ca3-118">Functions</span></span>](index.md)
