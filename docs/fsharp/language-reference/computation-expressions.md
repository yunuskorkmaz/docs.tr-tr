---
title: Hesaplama İfadeleri (F#)
description: 'Hesaplamaları sıralı ve denetim akışı yapılarını ve bağlamalar kullanılarak birleştirilen içinde F # yazmak için kullanışlı bir söz dizimi oluşturmayı öğrenin.'
ms.date: 07/27/2018
ms.openlocfilehash: 4995efc757d99a575ee9fad3abf0465a32398c44
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "36207439"
---
# <a name="computation-expressions"></a><span data-ttu-id="21aad-103">Hesaplama İfadeleri</span><span class="sxs-lookup"><span data-stu-id="21aad-103">Computation Expressions</span></span>

<span data-ttu-id="21aad-104">F # hesaplama ifadeleri, sıralı ve denetim akışı yapılarını ve bağlamalar kullanılarak birleştirilen hesaplamalar yazmak için kullanışlı bir söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="21aad-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="21aad-105">Hesaplama ifadesi türüne bağlı olarak bunlar, monadları, monoids monad dönüştürücüler ve applicative işlev nesneleri ifade etmenin bir yolu olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="21aad-106">Ancak, diğer diller aksine (gibi *gösterimi* Haskell içinde), tek bir soyutlama bağlı değil ve makroları veya diğer tür güvenmeyin azaltılarak kullanışlı ve bağlama duyarlı bir söz dizimi gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="21aad-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="21aad-107">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="21aad-107">Overview</span></span>

<span data-ttu-id="21aad-108">Hesaplamaları birçok biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-108">Computations can take many forms.</span></span> <span data-ttu-id="21aad-109">En yaygın hesaplamanın anlamak ve değiştirilmesi kolay olan tek iş parçacıklı yürütme biçimidir.</span><span class="sxs-lookup"><span data-stu-id="21aad-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="21aad-110">Ancak, tüm biçimlerinin hesaplama tek iş parçacıklı yürütme basit değildir.</span><span class="sxs-lookup"><span data-stu-id="21aad-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="21aad-111">Bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="21aad-111">Some examples include:</span></span>

* <span data-ttu-id="21aad-112">Belirleyici olmayan hesaplamaları</span><span class="sxs-lookup"><span data-stu-id="21aad-112">Non-deterministic computations</span></span>
* <span data-ttu-id="21aad-113">Zaman uyumsuz hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="21aad-113">Asynchronous computations</span></span>
* <span data-ttu-id="21aad-114">Effectful hesaplamaları</span><span class="sxs-lookup"><span data-stu-id="21aad-114">Effectful computations</span></span>
* <span data-ttu-id="21aad-115">Games'in hesaplamaları</span><span class="sxs-lookup"><span data-stu-id="21aad-115">Generative computations</span></span>

<span data-ttu-id="21aad-116">Daha genel vardır *bağlama duyarlı* hesaplamalar bir uygulamanın bazı bölümlerini gerçekleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="21aad-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="21aad-117">Belirli bir bağlam olmadan bunu yapmasını önlemek için soyutlama dışında "sızıntısı" hesaplamalar kolay olduğundan bağlama duyarlı kod yazma, zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="21aad-118">Bu soyutlama genellikle kendi kendinize, F # yorumun yapmak için genelleştirilmiş bir yolu yoktur neden olan yazmak zor **hesaplama ifadeleri**.</span><span class="sxs-lookup"><span data-stu-id="21aad-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="21aad-119">Hesaplama ifadeleri, bağlama duyarlı hesaplamalar kodlaması için Tekdüzen bir söz dizimi ve Özet modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="21aad-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="21aad-120">Her hesaplama ifadesi tarafından yedeklenen bir *Oluşturucu* türü.</span><span class="sxs-lookup"><span data-stu-id="21aad-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="21aad-121">Oluşturucu türü hesaplama ifadesi için kullanılabilen işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21aad-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="21aad-122">Bkz: [yeni bir tür, hesaplama ifadesi oluşturma](computation-expressions.md#creating-a-new-type-of-computation-expression), özel hesaplama ifadesi oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21aad-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="21aad-123">Söz dizimi genel bakış</span><span class="sxs-lookup"><span data-stu-id="21aad-123">Syntax overview</span></span>

<span data-ttu-id="21aad-124">Tüm hesaplama ifadeleri, aşağıdaki biçime sahiptir:</span><span class="sxs-lookup"><span data-stu-id="21aad-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="21aad-125">Burada `builder-expr` hesaplama ifadesi tanımlayan bir oluşturucu türüne adıdır ve `cexper` hesaplama ifadesi ifade gövdesi.</span><span class="sxs-lookup"><span data-stu-id="21aad-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="21aad-126">Örneğin, `async` hesaplama ifadesi kod şuna benzeyebilir:</span><span class="sxs-lookup"><span data-stu-id="21aad-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="21aad-127">Özel, ek bir söz dizimi bir hesaplama ifadesi içinde mevcut değildir önceki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="21aad-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="21aad-128">Hesaplama ifadeleri ile aşağıdaki ifade biçimleri desteklenir:</span><span class="sxs-lookup"><span data-stu-id="21aad-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="21aad-129">Her biri bu anahtar sözcükler ve diğer standart F # anahtar sözcükleri olup yalnızca bir hesaplama ifadesinde kullanılabilir yedekleme Oluşturucu türü tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="21aad-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="21aad-130">Bunun tek özel durum `match!`, kendisi kullanımına yönelik söz dizimi sugar `let!` sonucuna bir desen eşleşmesi tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="21aad-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="21aad-131">Oluşturucu türü hesaplama ifadesi parçalarını birleştirilir biçimini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir deyişle, hesaplama ifadesi nasıl davranacağını metotlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="21aad-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="21aad-132">Bir oluşturucu sınıf tanımlamak için başka bir, döngüler ve bağlamalar gibi birçok F # yapılarını, işlemi özelleştirmenizi sağlar söylemek yoludur.</span><span class="sxs-lookup"><span data-stu-id="21aad-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="21aad-133">`let!` Anahtar sözcüğü bir ad ile başka bir hesaplama ifadesi için bir çağrı sonucunu bağlar:</span><span class="sxs-lookup"><span data-stu-id="21aad-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="21aad-134">Bir hesaplama ifadesi ile çağrı bağlama `let`, hesaplama ifadesi sonucu almazsınız.</span><span class="sxs-lookup"><span data-stu-id="21aad-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="21aad-135">Bunun yerine, değeri bağlı *gerçekleşmemiş* çağırmak için hesaplama ifadesi.</span><span class="sxs-lookup"><span data-stu-id="21aad-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="21aad-136">Kullanım `let!` sonucu bağlamak için.</span><span class="sxs-lookup"><span data-stu-id="21aad-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="21aad-137">`let!` tarafından tanımlanan `Bind(x, f)` üyesi Oluşturucu türü.</span><span class="sxs-lookup"><span data-stu-id="21aad-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="21aad-138">`do!` Anahtar sözcüğü, bir hesaplama ifadesi çağıran döndürür bir `unit`-ister türü (tarafından tanımlanan `Zero` üyesi oluşturucu üzerinde):</span><span class="sxs-lookup"><span data-stu-id="21aad-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! sumbitData data url
        ...
    }
```

<span data-ttu-id="21aad-139">İçin [zaman uyumsuz iş akışı](asynchronous-workflows.md), bu tür `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="21aad-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="21aad-140">Türü diğer hesaplama ifadeleri için büyük olasılıkla `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="21aad-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="21aad-141">`do!` tarafından tanımlanan `Bind(x, f)` Oluşturucu türü üyesinde burada `f` üreten bir `unit`.</span><span class="sxs-lookup"><span data-stu-id="21aad-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="21aad-142">`yield` Anahtar sözcüğü, böylece olarak kullanılabilecek bir değer hesaplama ifadesinden döndürmek için bir <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="21aad-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="21aad-143">Olduğu gibi [C# anahtar sözcüğü yield](../../csharp/language-reference/keywords/yield.md), hesaplama ifadesi içindeki her öğeyi geri yinelendiğinde olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="21aad-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="21aad-144">`yield` tarafından tanımlanan `Yield(x)` Oluşturucu türü üyesinde burada `x` geri yield öğedir.</span><span class="sxs-lookup"><span data-stu-id="21aad-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="21aad-145">`yield!` Anahtar sözcüğü, bir hesaplama ifadesi değerleri koleksiyonunu düzleştirme için:</span><span class="sxs-lookup"><span data-stu-id="21aad-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="21aad-146">Hesaplama ifadesi değerlendirildiğinde, çağıran `yield!` öğelerinden geri bir sonuç düzleştirme tek, veriyor olması.</span><span class="sxs-lookup"><span data-stu-id="21aad-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="21aad-147">`yield!` tarafından tanımlanan `YieldFrom(x)` Oluşturucu türü üyesinde burada `x` değerleri oluşan bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="21aad-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="21aad-148">`return` Anahtar sözcüğü hesaplama ifadesi için karşılık gelen türünde bir değeri sarar.</span><span class="sxs-lookup"><span data-stu-id="21aad-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="21aad-149">Hesaplama ifadeleri kullanarak yanı sıra `yield`, "bir hesaplama ifadesi tamamlamak için" kullanılır:</span><span class="sxs-lookup"><span data-stu-id="21aad-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="21aad-150">`return` tarafından tanımlanan `Return(x)` Oluşturucu türü üyesinde burada `x` sarmalamak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="21aad-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="21aad-151">`return!` Anahtar sözcüğü bir hesaplama ifadesi değerini fark etti ve hesaplama ifadesi için karşılık gelen türü sonucu sarmalar:</span><span class="sxs-lookup"><span data-stu-id="21aad-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="21aad-152">`return!` tarafından tanımlanan `ReturnFrom(x)` Oluşturucu türü üyesinde burada `x` başka bir hesaplama ifadesi.</span><span class="sxs-lookup"><span data-stu-id="21aad-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="21aad-153">F # 4.5 ile başlayarak `match!` anahtar sözcüğü verir satır içi bir çağrı sonucunu üzerinde başka bir hesaplama ifadesi ve desen eşleştirme için:</span><span class="sxs-lookup"><span data-stu-id="21aad-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="21aad-154">Bir hesaplama ifadesi ile çağrılırken `match!`, gibi çağrısının sonucuna fark edeceksiniz `let!`.</span><span class="sxs-lookup"><span data-stu-id="21aad-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="21aad-155">Bu genellikle bir hesaplama ifadesi sonucu olduğu çağrıldığında kullanılır bir [isteğe bağlı](options.md).</span><span class="sxs-lookup"><span data-stu-id="21aad-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="21aad-156">Yerleşik hesaplama ifadeleri</span><span class="sxs-lookup"><span data-stu-id="21aad-156">Built-in computation expressions</span></span>

<span data-ttu-id="21aad-157">F # çekirdek kitaplığının üç yerleşik hesaplama ifadeleri tanımlar: [Sequence ifadeleri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [sorgu ifadeleri](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="21aad-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="21aad-158">Yeni bir hesaplama ifadesi türü oluşturma</span><span class="sxs-lookup"><span data-stu-id="21aad-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="21aad-159">Builder sınıfı oluşturarak ve sınıf üzerinde belirli özel yöntemler tanımlayarak kendi hesaplama ifadeleri özelliklerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21aad-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="21aad-160">Builder sınıfı, isteğe bağlı olarak aşağıdaki tabloda listelendiği gibi yöntemleri tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21aad-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="21aad-161">Aşağıdaki tablo, bir iş akışı Oluşturucu sınıfta kullanılabilir yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="21aad-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="21aad-162">**Yöntemi**</span><span class="sxs-lookup"><span data-stu-id="21aad-162">**Method**</span></span>|<span data-ttu-id="21aad-163">**Tipik bir imza**</span><span class="sxs-lookup"><span data-stu-id="21aad-163">**Typical signature(s)**</span></span>|<span data-ttu-id="21aad-164">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="21aad-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="21aad-165">İçin adlı `let!` ve `do!` hesaplama ifadeleri de.</span><span class="sxs-lookup"><span data-stu-id="21aad-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="21aad-166">Bir hesaplama ifadesi bir işlev olarak sarmalar.</span><span class="sxs-lookup"><span data-stu-id="21aad-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="21aad-167">İçin adlı `return` hesaplama ifadeleri de.</span><span class="sxs-lookup"><span data-stu-id="21aad-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="21aad-168">İçin adlı `return!` hesaplama ifadeleri de.</span><span class="sxs-lookup"><span data-stu-id="21aad-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="21aad-169">`M<'T> -> M<'T>` veya</span><span class="sxs-lookup"><span data-stu-id="21aad-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="21aad-170">Hesaplama ifadesi yürütür.</span><span class="sxs-lookup"><span data-stu-id="21aad-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="21aad-171">`M<'T> * M<'T> -> M<'T>` veya</span><span class="sxs-lookup"><span data-stu-id="21aad-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="21aad-172">Hesaplama ifadeleri sıralama için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="21aad-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="21aad-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` veya</span><span class="sxs-lookup"><span data-stu-id="21aad-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="21aad-174">İçin adlı `for...do` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="21aad-175">İçin adlı `try...finally` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="21aad-176">İçin adlı `try...with` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="21aad-177">İçin adlı `use` hesaplama ifadeleri bağlarında.</span><span class="sxs-lookup"><span data-stu-id="21aad-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="21aad-178">İçin adlı `while...do` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="21aad-179">İçin adlı `yield` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="21aad-180">İçin adlı `yield!` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="21aad-181">İçin boş olarak adlandırılan `else` , dallar `if...then` hesaplama ifadeleri ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|

<span data-ttu-id="21aad-182">Bir oluşturucu sınıftaki yöntemlerin birçoğu kullanın ve dönüş bir `M<'T>` genellikle örneğin birleştirilmeye, hesaplamalar türünü belirtir ayrı olarak tanımlanan bir tür olan yapı `Async<'T>` zaman uyumsuz iş akışları için ve `Seq<'T>` Sıralı iş akışları.</span><span class="sxs-lookup"><span data-stu-id="21aad-182">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="21aad-183">Bu yöntem imzalarını birleştirilir ve birbirleri ile iç içe geçmiş kendisine etkinleştirin; böylelikle bir yapı döndürülen iş akışı nesnesinin sonraki geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-183">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="21aad-184">Derleyici, bir hesaplama ifade ayrıştırırken, yukarıdaki tabloda yöntemleri ve hesaplama ifadesi kodu kullanarak, iç içe geçmiş işlev çağrıları bir dizi ifade dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="21aad-184">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="21aad-185">İç içe geçmiş ifade aşağıdaki şekildedir:</span><span class="sxs-lookup"><span data-stu-id="21aad-185">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="21aad-186">Yukarıdaki kodda, çağrıları `Run` ve `Delay` hesaplama ifadesi Oluşturucu sınıfta tanımlı değil göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-186">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="21aad-187">Olarak burada belirtilen hesaplama ifadesi gövdesinin `{| cexpr |}`, aşağıdaki tabloda açıklanan çevirileri tarafından Oluşturucu sınıfının yöntemlerini içeren çağırıyor çevrilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-187">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="21aad-188">Hesaplama ifadesi `{| cexpr |}` tanımlı yinelemeli olarak bu çevirileri göre olduğundan burada `expr` bir F # ifadesi ve `cexpr` hesaplama ifadesi.</span><span class="sxs-lookup"><span data-stu-id="21aad-188">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>



|<span data-ttu-id="21aad-189">İfade</span><span class="sxs-lookup"><span data-stu-id="21aad-189">Expression</span></span>|<span data-ttu-id="21aad-190">Çeviri</span><span class="sxs-lookup"><span data-stu-id="21aad-190">Translation</span></span>|
|----------|-----------|
|<code>{&#124; let binding in cexpr &#124;}</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{&#124; let! pattern = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; do! expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; yield expr &#124;}</code>|`builder.Yield(expr)`|
|<code>{&#124; yield! expr &#124;}</code>|`builder.YieldFrom(expr)`|
|<code>{&#124; return expr &#124;}</code>|`builder.Return(expr)`|
|<code>{&#124; return! expr &#124;}</code>|`builder.ReturnFrom(expr)`|
|<code>{&#124; use pattern = expr in cexpr &#124;}</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; use! value = expr in cexpr &#124;}</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> {&#124; cexpr &#124;}))))</code>|
|<code>{&#124; if expr then cexpr0 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else binder.Zero()</code>|
|<code>{&#124; if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then {&#124; cexpr0 &#124;} else {&#124; cexpr1 &#124;}</code>|
|<code>{&#124; match expr with &#124; pattern_i -> cexpr_i &#124;}</code>|<code>match expr with &#124; pattern_i -> {&#124; cexpr_i &#124;}</code>|
|<code>{&#124; for pattern in expr do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; for identifier = expr1 to expr2 do cexpr &#124;}</code>|<code>builder.For(enumeration, (fun identifier -> {&#124; cexpr &#124;}))</code>|
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
<span data-ttu-id="21aad-191">Önceki tabloda `other-expr` tabloda listelenmeyen bir ifade açıklar.</span><span class="sxs-lookup"><span data-stu-id="21aad-191">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="21aad-192">Bir oluşturucu sınıf tüm yöntemleri uygulayın ve tüm önceki tabloda listelenen çevirileri destek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="21aad-192">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="21aad-193">Uygulanmaz bu yapıları hesaplama türü ifadelerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21aad-193">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="21aad-194">Örneğin desteklemek istemiyorsanız, `use` anahtar sözcüğü, hesaplama ifadeleri de tanımını çıkarabilirsiniz `Use` Oluşturucu sınıfınızdaki.</span><span class="sxs-lookup"><span data-stu-id="21aad-194">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="21aad-195">Aşağıdaki kod örneği, bir hesaplama olabilecek bir dizi aynı anda tek bir adımda değerlendirilen olarak kapsülleyen bir hesaplama ifadesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="21aad-195">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="21aad-196">Bir ayırt edici birleşim türü `OkOrException`, ifade hata durumunu şimdiye değerlendirilen olarak kodlar.</span><span class="sxs-lookup"><span data-stu-id="21aad-196">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="21aad-197">Bu kod Oluşturucu yöntemleri bazı ortak uygulamalar gibi hesaplama ifadeleri kullanabileceğiniz birkaç tipik desenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="21aad-197">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> NotYetDone (fun () -> func value)
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res -> 
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally 
            (whileLoop 
                (fun () -> ie.MoveNext()) 
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this 
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "NotYetDone <closure>"
comp |> step |> step |> step |> step |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step |> step |> step |> step |> step
```

<span data-ttu-id="21aad-198">Hesaplama ifadesi ifade döndürür bir temel türü vardır.</span><span class="sxs-lookup"><span data-stu-id="21aad-198">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="21aad-199">Temel alınan türü, hesaplanan bir sonuç ya da gerçekleştirilebilir Gecikmeli bir hesaplama gösterebilir veya bazı koleksiyon türü yineleme yapmak için bir yol sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-199">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="21aad-200">Önceki örnekte, temel türde **sonunda**.</span><span class="sxs-lookup"><span data-stu-id="21aad-200">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="21aad-201">Bir sıralama ifadesi için temel türdür <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21aad-201">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21aad-202">Bir sorgu ifadesi için temel türdür <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="21aad-202">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21aad-203">Zaman uyumsuz bir iş akışı için temel türdür [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="21aad-203">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="21aad-204">`Async` Nesne sonucu hesaplamak için gerçekleştirilecek işin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21aad-204">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="21aad-205">Örneğin, çağrı [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) hesaplama çalıştırmak ve sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="21aad-205">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="21aad-206">Özel işlemler</span><span class="sxs-lookup"><span data-stu-id="21aad-206">Custom Operations</span></span>
<span data-ttu-id="21aad-207">Hesaplama ifadesi üzerinde özel bir işlemi tanımlar ve bir işleç bir hesaplama ifadesi olarak özel bir işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="21aad-207">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="21aad-208">Örneğin, bir sorgu ifadesinde bir sorgu işleci içerebilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-208">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="21aad-209">Özel bir işlemi tanımlarken Yield tanımlamanız gerekir ve hesaplama ifadesi yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="21aad-209">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="21aad-210">Özel bir işlemi tanımlamak için hesaplama ifadesi için bir oluşturucu sınıf koyun ve ardından uygulama [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="21aad-210">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="21aad-211">Bu öznitelik, bir özel işleminde kullanılacak adı olan bir bağımsız değişkeni olarak bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="21aad-211">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="21aad-212">Bu ad, açılış kaşlı ayracından hesaplama deyimine başlangıcında kapsama gelir.</span><span class="sxs-lookup"><span data-stu-id="21aad-212">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="21aad-213">Bu nedenle, bu bloğunda bir özel işlem olarak aynı ada sahip tanımlayıcılar kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="21aad-213">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="21aad-214">Örneğin, tanımlayıcıların gibi kullanmaktan kaçının `all` veya `last` sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="21aad-214">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="21aad-215">Mevcut oluşturucular yeni özel işlemleri ile genişletme</span><span class="sxs-lookup"><span data-stu-id="21aad-215">Extending existing Builders with new Custom Operations</span></span>
<span data-ttu-id="21aad-216">Bir oluşturucu sınıf zaten varsa, kendi özel işlemler öğesinden Bu oluşturucu sınıf dışında genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="21aad-216">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="21aad-217">Uzantılar, modüller bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="21aad-217">Extensions must be declared in modules.</span></span> <span data-ttu-id="21aad-218">Ad alanları, aynı dosya ve tür tanımlandığı ad alanı bildirimi grubu dışında uzantı üyeleri içeremez.</span><span class="sxs-lookup"><span data-stu-id="21aad-218">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="21aad-219">Aşağıdaki örnek, varolan uzantısı gösterir `Microsoft.FSharp.Linq.QueryBuilder` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="21aad-219">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="21aad-220">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21aad-220">See Also</span></span>
[<span data-ttu-id="21aad-221">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="21aad-221">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="21aad-222">Zaman Uyumsuz İş Akışları</span><span class="sxs-lookup"><span data-stu-id="21aad-222">Asynchronous Workflows</span></span>](asynchronous-workflows.md)

[<span data-ttu-id="21aad-223">Diziler</span><span class="sxs-lookup"><span data-stu-id="21aad-223">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[<span data-ttu-id="21aad-224">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="21aad-224">Query Expressions</span></span>](query-expressions.md)
