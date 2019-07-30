---
title: 'Özyinelemeli Işlevler: REC anahtar sözcüğü'
description: "' Rec ' F# anahtar sözcüğünün özyinelemeli bir işlev tanımlamak için ' Let ' anahtar sözcüğüyle nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630655"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="802d9-103">Özyinelemeli Işlevler: REC anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="802d9-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="802d9-104">Anahtar sözcüğü özyinelemeli bir işlev tanımlamak için `let` anahtar sözcüğüyle birlikte kullanılır. `rec`</span><span class="sxs-lookup"><span data-stu-id="802d9-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="802d9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="802d9-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="802d9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="802d9-106">Remarks</span></span>

<span data-ttu-id="802d9-107">Kendini çağıran işlevler, açıkça F# dilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="802d9-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="802d9-108">Bu, tanımlanmakta olan tanımlayıcıların işlevin kapsamında kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="802d9-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="802d9-109">Aşağıdaki kod, *n*<sup>.</sup> fibonaccı numarasını hesaplayan özyinelemeli bir işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="802d9-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="802d9-110">Uygulamada, yukarıda yer alan kod, daha önce hesaplanmış değerlerin yeniden hesaplanmasını içerdiğinden, bellek ve işlemci süresinin boşa harcanmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="802d9-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="802d9-111">Yöntemler tür içinde örtük olarak özyinelemeli; `rec` anahtar sözcüğü eklemeye gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="802d9-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="802d9-112">Sınıfların içindeki bağlamaların örtülü olarak özyinelemeli olmadığından izin verin.</span><span class="sxs-lookup"><span data-stu-id="802d9-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="802d9-113">Birbirini karşılıklı özyinelemeli Işlevler</span><span class="sxs-lookup"><span data-stu-id="802d9-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="802d9-114">Bazen işlevler *birbirini yinelemelidir*, yani bir işlevin bir kez çağrı yaptığı, aralarında herhangi bir sayıda çağrıya sahip olan diğeri çağıran bir daire oluşturur.</span><span class="sxs-lookup"><span data-stu-id="802d9-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="802d9-115">Bu tür işlevleri bir `let` bağlamada birlikte tanımlamanız gerekir, `and` anahtar sözcüğünü kullanarak birbirine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="802d9-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="802d9-116">Aşağıdaki örnekte birbirini dışlayan iki özyinelemeli işlev gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="802d9-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="802d9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="802d9-117">See also</span></span>

- [<span data-ttu-id="802d9-118">İşlevler</span><span class="sxs-lookup"><span data-stu-id="802d9-118">Functions</span></span>](index.md)
