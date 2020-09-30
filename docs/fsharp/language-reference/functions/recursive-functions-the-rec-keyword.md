---
title: 'Yinelemeli İşlevler: rec Anahtar Sözcüğü'
description: "Bir özyinelemeli işlev tanımlamak için ' Let ' anahtar sözcüğüyle F # ' Rec ' anahtar sözcüğünün nasıl kullanıldığını öğrenin."
ms.date: 08/12/2020
ms.openlocfilehash: 1ab00ff9400129e531fd7320861b3d9625cad08c
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438073"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="b0ce2-103">Yinelemeli İşlevler: rec Anahtar Sözcüğü</span><span class="sxs-lookup"><span data-stu-id="b0ce2-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="b0ce2-104">`rec`Anahtar sözcüğü `let` özyinelemeli bir işlev tanımlamak için anahtar sözcüğüyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0ce2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0ce2-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b0ce2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0ce2-106">Remarks</span></span>

<span data-ttu-id="b0ce2-107">Özyinelemeli işlevler-kendilerini çağıran işlevler-anahtar sözcüğüyle F # dilinde açıkça tanımlanır `rec` .</span><span class="sxs-lookup"><span data-stu-id="b0ce2-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="b0ce2-108">`rec`Anahtar sözcüğü, `let` bağlamanın adını gövdesinde kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="b0ce2-109">Aşağıdaki örnek, matematik tanımını kullanarak *n*<sup>.</sup> fibonaccı numarasını hesaplayan özyinelemeli bir işlevi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let rec fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="b0ce2-110">Uygulamada, önceki örneğe benzer bir kod, unecessarily daha önce hesaplanmış olan değerleri yeniden hesaplar olduğundan ideal değildir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="b0ce2-111">Bunun nedeni, bu makalede daha fazla açıklanacak tail özyinelemeli değildir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="b0ce2-112">Yöntemler içinde tanımlandıkları tür içinde örtülü olarak özyinelemeli olur, yani anahtar sözcüğü eklemeye gerek yoktur `rec` .</span><span class="sxs-lookup"><span data-stu-id="b0ce2-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="b0ce2-113">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b0ce2-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="b0ce2-114">Sınıfların içindeki bağlamaların örtülü olarak özyinelemeli olmamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="b0ce2-115">Tüm `let` bağlantılı işlevler `rec` anahtar sözcüğünü gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="b0ce2-116">Kuyruk özyineleme</span><span class="sxs-lookup"><span data-stu-id="b0ce2-116">Tail recursion</span></span>

<span data-ttu-id="b0ce2-117">Bazı Özyinelemeli işlevler için, daha "saf" tanımın [tail özyinelemeli](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion)olan bir tanımına yeniden düzenlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="b0ce2-118">Bu, gereksiz yeniden hesaplamaları önler.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="b0ce2-119">Örneğin, önceki fibonaccı sayı Oluşturucusu şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="b0ce2-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

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

<span data-ttu-id="b0ce2-120">Bu daha karmaşık bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-120">This is a more complicated implementation.</span></span> <span data-ttu-id="b0ce2-121">Fibonaccı numarası oluşturmak, matematiksel olarak saf, ancak verimsiz bir "Naïve" algoritmasına yönelik harika bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="b0ce2-122">Birkaç yönü, yine de özyinelemeli olarak tanımlanmış olan F # ' da verimli hale getirir:</span><span class="sxs-lookup"><span data-stu-id="b0ce2-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="b0ce2-123">Bir `loop` ı, F # deseninin adlı özyinelemeli bir iç işlev.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="b0ce2-124">İki biriktiricidir parametresi, bu değerler, çoğaltılan çağrılara biriktir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="b0ce2-125">`n`Belirli bir birikme döndürmek için değerinin bir denetimi.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="b0ce2-126">Bu örnek bir döngüyle yinelemeli olarak yazılmışsa, kod, belirli bir koşul karşılanana kadar iki farklı değer ile benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="b0ce2-127">Bunun tail-özyinelemeli olmasının nedeni, özyinelemeli çağrının çağrı yığınında değer kaydetmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="b0ce2-128">Hesaplanmakta olan tüm ara değerler, iç işleve girişler aracılığıyla toplanır.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="b0ce2-129">Bu Ayrıca, F # derleyicisinin bir döngü gibi bir şey yazmışsınız gibi, kodu en yüksek hıza kadar hızlı bir şekilde iyileştirmelerine de olanak tanır `while` .</span><span class="sxs-lookup"><span data-stu-id="b0ce2-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="b0ce2-130">Önceki örnekte gösterildiği gibi, bir iç ve dış işlevle bir şeyi yinelemeli olarak işleyen F # kodu yazmak yaygındır.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="b0ce2-131">İç işlev, Kuyruk özyineleme kullanır, dış işlevin çağıranlar için daha iyi bir arabirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="b0ce2-132">Birbirini karşılıklı özyinelemeli Işlevler</span><span class="sxs-lookup"><span data-stu-id="b0ce2-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="b0ce2-133">Bazen işlevler *birbirini yinelemelidir*, yani bir işlevin bir kez çağrı yaptığı, aralarında herhangi bir sayıda çağrıya sahip olan diğeri çağıran bir daire oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="b0ce2-134">Bu tür işlevleri bir bağlamada birlikte tanımlamanız gerekir `let` , `and` anahtar sözcüğünü kullanarak birbirine bağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="b0ce2-135">Aşağıdaki örnekte birbirini dışlayan iki özyinelemeli işlev gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="b0ce2-136">Özyinelemeli değerler</span><span class="sxs-lookup"><span data-stu-id="b0ce2-136">Recursive values</span></span>

<span data-ttu-id="b0ce2-137">`let`Özyinelemeli olacak şekilde, bir-bağlantılı değer de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="b0ce2-138">Bu işlem bazen günlüğe kaydetme için yapılır.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-138">This is sometimes done for logging.</span></span> <span data-ttu-id="b0ce2-139">F # 5 ve işlevi ile `nameof` bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b0ce2-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="b0ce2-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0ce2-140">See also</span></span>

- [<span data-ttu-id="b0ce2-141">İşlevler</span><span class="sxs-lookup"><span data-stu-id="b0ce2-141">Functions</span></span>](index.md)
