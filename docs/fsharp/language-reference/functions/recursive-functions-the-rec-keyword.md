---
title: 'Yinelemeli İşlevler: rec Anahtar Sözcüğü'
description: "Bir özyinelemeli işlev tanımlamak için ' Let ' anahtar sözcüğüyle F # ' Rec ' anahtar sözcüğünün nasıl kullanıldığını öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: c2374f90b4585327c6f5208a3d6bca75a23d0cbb
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455663"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="797c3-103">Yinelemeli İşlevler: rec Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="797c3-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="797c3-104">`rec`Anahtar sözcüğü `let` özyinelemeli bir işlev tanımlamak için anahtar sözcüğüyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="797c3-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="797c3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="797c3-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="797c3-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="797c3-106">Remarks</span></span>

<span data-ttu-id="797c3-107">Özyinelemeli işlevler, kendilerini çağıran işlevler, F # dilinde açıkça tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="797c3-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="797c3-108">Bu, tanımlanmakta olan tanımlayıcıların işlevin kapsamında kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="797c3-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="797c3-109">Aşağıdaki kod, matematik tanımını kullanarak *n*<sup>.</sup> fibonaccı numarasını hesaplayan özyinelemeli bir işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="797c3-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="797c3-110">Uygulamada, önceki örneğe benzer bir kod, unecessarily daha önce hesaplanmış olan değerleri yeniden hesaplar olduğundan ideal değildir.</span><span class="sxs-lookup"><span data-stu-id="797c3-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="797c3-111">Bunun nedeni, bu makalede daha fazla açıklanacak tail özyinelemeli değildir.</span><span class="sxs-lookup"><span data-stu-id="797c3-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="797c3-112">Yöntemler tür içinde örtük olarak özyinelemeli; anahtar sözcüğü eklemeye gerek yoktur `rec` .</span><span class="sxs-lookup"><span data-stu-id="797c3-112">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="797c3-113">Sınıfların içindeki bağlamaların örtülü olarak özyinelemeli olmadığından izin verin.</span><span class="sxs-lookup"><span data-stu-id="797c3-113">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="797c3-114">Kuyruk özyineleme</span><span class="sxs-lookup"><span data-stu-id="797c3-114">Tail recursion</span></span>

<span data-ttu-id="797c3-115">Bazı Özyinelemeli işlevler için, daha "saf" tanımın [tail özyinelemeli](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)olan bir tanımına yeniden düzenlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="797c3-115">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="797c3-116">Bu, gereksiz yeniden hesaplamaları önler.</span><span class="sxs-lookup"><span data-stu-id="797c3-116">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="797c3-117">Örneğin, önceki fibonaccı sayı Oluşturucusu şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="797c3-117">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="797c3-118">Bu daha karmaşık bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="797c3-118">This is a more complicated implementation.</span></span> <span data-ttu-id="797c3-119">Fibonaccı numarası oluşturmak, matematiksel olarak saf, ancak verimsiz bir "Naïve" algoritmasına yönelik harika bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="797c3-119">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="797c3-120">Birkaç yönü, yine de özyinelemeli olarak tanımlanmış olan F # ' da verimli hale getirir:</span><span class="sxs-lookup"><span data-stu-id="797c3-120">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="797c3-121">Bir `loop` ı, F # deseninin adlı özyinelemeli bir iç işlev.</span><span class="sxs-lookup"><span data-stu-id="797c3-121">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="797c3-122">İki biriktiricidir parametresi, bu değerler, çoğaltılan çağrılara biriktir.</span><span class="sxs-lookup"><span data-stu-id="797c3-122">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="797c3-123">`n`Belirli bir birikme döndürmek için değerinin bir denetimi.</span><span class="sxs-lookup"><span data-stu-id="797c3-123">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="797c3-124">Bu örnek bir döngüyle yinelemeli olarak yazılmışsa, kod, belirli bir koşul karşılanana kadar iki farklı değer ile benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="797c3-124">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="797c3-125">Bunun tail-özyinelemeli olmasının nedeni, özyinelemeli çağrının çağrı yığınında değer kaydetmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="797c3-125">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="797c3-126">Hesaplanmakta olan tüm ara değerler, iç işleve girişler aracılığıyla toplanır.</span><span class="sxs-lookup"><span data-stu-id="797c3-126">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="797c3-127">Bu Ayrıca, F # derleyicisinin bir döngü gibi bir şey yazmışsınız gibi, kodu en yüksek hıza kadar hızlı bir şekilde iyileştirmelerine de olanak tanır `while` .</span><span class="sxs-lookup"><span data-stu-id="797c3-127">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="797c3-128">Önceki örnekte gösterildiği gibi, bir iç ve dış işlevle bir şeyi yinelemeli olarak işleyen F # kodu yazmak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="797c3-128">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="797c3-129">İç işlev, Kuyruk özyineleme kullanır, dış işlevin çağıranlar için daha iyi bir arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="797c3-129">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="797c3-130">Birbirini karşılıklı özyinelemeli Işlevler</span><span class="sxs-lookup"><span data-stu-id="797c3-130">Mutually Recursive Functions</span></span>

<span data-ttu-id="797c3-131">Bazen işlevler *birbirini yinelemelidir*, yani bir işlevin bir kez çağrı yaptığı, aralarında herhangi bir sayıda çağrıya sahip olan diğeri çağıran bir daire oluşturur.</span><span class="sxs-lookup"><span data-stu-id="797c3-131">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="797c3-132">Bu tür işlevleri bir bağlamada birlikte tanımlamanız gerekir `let` , `and` anahtar sözcüğünü kullanarak birbirine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="797c3-132">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="797c3-133">Aşağıdaki örnekte birbirini dışlayan iki özyinelemeli işlev gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="797c3-133">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="797c3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="797c3-134">See also</span></span>

- [<span data-ttu-id="797c3-135">İşlevler</span><span class="sxs-lookup"><span data-stu-id="797c3-135">Functions</span></span>](index.md)
