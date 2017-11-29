---
title: "Özyinelemeli İşlevler: rec Anahtar Sözcüğü (F#)"
description: "F # 'rec' anahtar sözcüğü özyinelemeli bir işlev tanımlamak için 'let' anahtar sözcüğü ile nasıl kullanıldığı hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1a95639f-9bfe-4f1d-a5e2-246d1d37776e
ms.openlocfilehash: b837d2c0f8e2b1d28980620103097ccc8345c098
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="46081-104">Özyinelemeli İşlevler: rec Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="46081-104">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="46081-105">`rec` Anahtar sözcüğü ile birlikte kullanıldığında `let` özyinelemeli bir işlev tanımlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="46081-105">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="46081-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46081-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="46081-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46081-107">Remarks</span></span>
<span data-ttu-id="46081-108">Özyinelemeli İşlevler, kendileri arama işlevleri açıkça F # dilinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="46081-108">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="46081-109">Bu tanımlanıyorsa tanımlayıcı işlevi kapsamında kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="46081-109">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="46081-110">Aşağıdaki kod hesaplar bir özyinelemeli işlev gösterir  *n* th Fibonacci numarası.</span><span class="sxs-lookup"><span data-stu-id="46081-110">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="46081-111">Önceden hesaplanan değerler recomputation içerdiğinden, gibi Yukarıdaki kod bellek ve işlemci süresini kayıp uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="46081-111">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="46081-112">Örtük olarak özyinelemeli türü içinde yöntemleridir; eklemeye gerek yoktur `rec` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="46081-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="46081-113">Sınıflardaki let bağlamaları örtülü olarak özyinelemeli değildir.</span><span class="sxs-lookup"><span data-stu-id="46081-113">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="46081-114">Karşılıklı özyinelemeli İşlevler</span><span class="sxs-lookup"><span data-stu-id="46081-114">Mutually Recursive Functions</span></span>
<span data-ttu-id="46081-115">Bazen işlevlerdir *karşılıklı özyinelemeli*, çağrıları burada bir işlevi çağırır sırayla çağrıları herhangi bir sayı ile ilk çağıran başka arasında bir daire form anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46081-115">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="46081-116">Bu tür işlevler bir araya tanımlamalısınız `let` kullanarak binding `and` birbirine bağlamak için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="46081-116">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="46081-117">Aşağıdaki örnekte iki birbirini gösterir özyinelemeli işlevler.</span><span class="sxs-lookup"><span data-stu-id="46081-117">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="46081-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46081-118">See Also</span></span>
[<span data-ttu-id="46081-119">İşlevler</span><span class="sxs-lookup"><span data-stu-id="46081-119">Functions</span></span>](index.md)
