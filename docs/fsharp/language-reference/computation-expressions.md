---
title: Hesaplama İfadeleri
description: Kontrol akışı yapıları ve bağlamaları kullanılarak sıralanabilen ve birleştirilebilen F# hesaplamaları yazmak için nasıl kullanışlı sözdizimi oluşturabileceğinizi öğrenin.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400234"
---
# <a name="computation-expressions"></a><span data-ttu-id="21e25-103">Hesaplama İfadeleri</span><span class="sxs-lookup"><span data-stu-id="21e25-103">Computation Expressions</span></span>

<span data-ttu-id="21e25-104">F#'daki hesaplama ifadeleri, denetim akışı yapıları ve bağlamaları kullanılarak sıralanabilen ve birleştirilebilen hesaplamalar yazmak için kullanışlı bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="21e25-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="21e25-105">Hesaplama ifade türüne bağlı olarak, onlar monads, monoids, monad transformatörler ve aplikatif functors ifade etmek için bir yol olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="21e25-106">Ancak, diğer dillerin (Haskell'daki *do-notation* gibi) aksine, tek bir soyutlamayla bağlı değildirler ve uygun ve içeriğe duyarlı bir sözdizimini gerçekleştirmek için makrolara veya diğer meta programlama biçimlerine güvenmezler.</span><span class="sxs-lookup"><span data-stu-id="21e25-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="21e25-107">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="21e25-107">Overview</span></span>

<span data-ttu-id="21e25-108">Hesaplamalar çeşitli şekillerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-108">Computations can take many forms.</span></span> <span data-ttu-id="21e25-109">En yaygın hesaplama biçimi, anlaşılması ve değiştirilmesi kolay tek iş parçacığı yürütmedir.</span><span class="sxs-lookup"><span data-stu-id="21e25-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="21e25-110">Ancak, tüm hesaplama biçimleri tek iş parçacığı yürütme kadar basit değildir.</span><span class="sxs-lookup"><span data-stu-id="21e25-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="21e25-111">Bazı örnekler:</span><span class="sxs-lookup"><span data-stu-id="21e25-111">Some examples include:</span></span>

- <span data-ttu-id="21e25-112">Deterministik olmayan hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="21e25-112">Non-deterministic computations</span></span>
- <span data-ttu-id="21e25-113">Asynchronous hesaplamaları</span><span class="sxs-lookup"><span data-stu-id="21e25-113">Asynchronous computations</span></span>
- <span data-ttu-id="21e25-114">Etkili hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="21e25-114">Effectful computations</span></span>
- <span data-ttu-id="21e25-115">Üretici hesaplamaları</span><span class="sxs-lookup"><span data-stu-id="21e25-115">Generative computations</span></span>

<span data-ttu-id="21e25-116">Daha genel olarak, bir uygulamanın belirli bölümlerinde gerçekleştirmeniz gereken *içeriğe duyarlı* hesaplamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="21e25-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="21e25-117">İçeriğe duyarlı kod yazmak zor olabilir, çünkü bunu yapmanızı engellemek için soyutlamalar olmadan belirli bir bağlamın dışında hesaplamaları "sızdırmak" kolaydır.</span><span class="sxs-lookup"><span data-stu-id="21e25-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="21e25-118">Bu soyutlamalar genellikle kendiniz yazmak zor, bu yüzden F # sözde **hesaplama ifadeleri**yapmak için genelleştirilmiş bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="21e25-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="21e25-119">Hesaplama ifadeleri, içeriğe duyarlı hesaplamaları kodlamak için tek biçimli bir sözdizimi ve soyutlama modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="21e25-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="21e25-120">Her hesaplama ifadesi bir *oluşturucu* türü tarafından desteklenen.</span><span class="sxs-lookup"><span data-stu-id="21e25-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="21e25-121">Oluşturucu türü, hesaplama ifadesi için kullanılabilen işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="21e25-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="21e25-122">Bkz. Özel bir hesaplama ifadesinin nasıl oluşturulup oluşturulturunu gösteren [Yeni Bir Hesaplama İfadesi Türü Oluşturma.](computation-expressions.md#creating-a-new-type-of-computation-expression)</span><span class="sxs-lookup"><span data-stu-id="21e25-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="21e25-123">Sözdizimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="21e25-123">Syntax overview</span></span>

<span data-ttu-id="21e25-124">Tüm hesaplama ifadeleri aşağıdaki formu vardır:</span><span class="sxs-lookup"><span data-stu-id="21e25-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="21e25-125">nerede `builder-expr` hesaplama ifadesini tanımlayan bir oluşturucu türünün adıdır `cexper` ve hesaplama ifadesinin ifade gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="21e25-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="21e25-126">Örneğin, `async` hesaplama ifade kodu şu şekilde görünebilir:</span><span class="sxs-lookup"><span data-stu-id="21e25-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="21e25-127">Önceki örnekte gösterildiği gibi, bir hesaplama ifadesi içinde özel, ek sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="21e25-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="21e25-128">Aşağıdaki ifade formları hesaplama ifadeleri ile mümkündür:</span><span class="sxs-lookup"><span data-stu-id="21e25-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="21e25-129">Bu anahtar kelimelerin her biri ve diğer standart F# anahtar kelimeleri yalnızca destek oluşturucu türünde tanımlanmışsa, bir hesaplama ifadesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="21e25-130">Bunun tek `match!`istisnası, kendisi sonucu bir desen maç `let!` takip kullanımı için sözdizimli şeker olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="21e25-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="21e25-131">Oluşturucu türü, hesaplama ifadesinin parçalarının birleştirilmesi yöntemini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir de, yöntemleri hesaplama ifadesinin nasıl olacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="21e25-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="21e25-132">Oluşturucu sınıfını tanımlamanın başka bir yolu da, döngüler ve bağlamalar gibi birçok F# yapısının çalışmasını özelleştirmenize olanak sağladığını söylemektir.</span><span class="sxs-lookup"><span data-stu-id="21e25-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="21e25-133">Anahtar `let!` kelime, bir ada yapılan bir çağrının sonucunu başka bir hesaplama ifadesine bağlar:</span><span class="sxs-lookup"><span data-stu-id="21e25-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="21e25-134">Aramayı bir hesaplama ifadesine `let`bağlarsanız, hesaplama ifadesinin sonucunu alamazsınız.</span><span class="sxs-lookup"><span data-stu-id="21e25-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="21e25-135">Bunun yerine, *gerçekleşmemiş* çağrının değerini bu hesaplama ifadesine bağlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="21e25-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="21e25-136">Sonuca `let!` bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="21e25-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="21e25-137">`let!`oluşturucu türünde `Bind(x, f)` üye tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21e25-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="21e25-138">Anahtar `do!` kelime, (oluşturucudaki `Zero` üye tarafından `unit`tanımlanan) benzer bir türü döndüren bir hesaplama ifadesini çağırmak içindir:</span><span class="sxs-lookup"><span data-stu-id="21e25-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="21e25-139">[Async iş akışı](asynchronous-workflows.md)için, `Async<unit>`bu tür .</span><span class="sxs-lookup"><span data-stu-id="21e25-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="21e25-140">Diğer hesaplama ifadeleri için, tür `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="21e25-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="21e25-141">`do!`oluşturucu türünde `Bind(x, f)` üye tarafından tanımlanır, burada `f` bir `unit`.</span><span class="sxs-lookup"><span data-stu-id="21e25-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="21e25-142">Anahtar `yield` kelime, hesaplama ifadesinden bir değeri döndürmeiçindir, böylece aşağıdaki <xref:System.Collections.Generic.IEnumerable%601>ler olarak tüketilebilir:</span><span class="sxs-lookup"><span data-stu-id="21e25-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="21e25-143">Çoğu durumda, arayanlar tarafından atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="21e25-144">Atlatır'ın `yield` en yaygın yolu `->` işleçtir:</span><span class="sxs-lookup"><span data-stu-id="21e25-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="21e25-145">Birçok farklı değer verebilecek daha karmaşık ifadeler için ve belki de koşullu olarak, anahtar sözcüğü atlayarak şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="21e25-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="21e25-146">[C#'daki verim anahtar sözcüğünde](../../csharp/language-reference/keywords/yield.md)olduğu gibi, hesaplama ifadesindeki her öğe, yinelenirken geri verilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="21e25-147">`yield`oluşturucu türünde `Yield(x)` üye tarafından tanımlanır, geri verim için öğe nerede. `x`</span><span class="sxs-lookup"><span data-stu-id="21e25-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="21e25-148">Anahtar `yield!` kelime, bir hesaplama ifadesinden değerler koleksiyonunu düzleştirmek içindir:</span><span class="sxs-lookup"><span data-stu-id="21e25-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="21e25-149">Değerlendirildiğinde, tarafından `yield!` çağrılan hesaplama ifadesi, öğelerini birer birer geri vererek sonucu düzleştirmek zorunda kalarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="21e25-150">`yield!`değer koleksiyonu `YieldFrom(x)` nun bulunduğu `x` oluşturucu türündeki üye tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21e25-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="21e25-151">`yield`Aksine, `yield!` açıkça belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="21e25-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="21e25-152">Davranışı hesaplama ifadelerinde örtük değildir.</span><span class="sxs-lookup"><span data-stu-id="21e25-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="21e25-153">`return` Anahtar kelime, hesaplama ifadesine karşılık gelen türdeki bir değeri sarar.</span><span class="sxs-lookup"><span data-stu-id="21e25-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="21e25-154">Bir hesaplama ifadesini `yield`"tamamlamak" için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="21e25-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="21e25-155">`return`oluşturucu türünde `Return(x)` üye tarafından tanımlanır, nerede `x` kaydırmak için öğedir.</span><span class="sxs-lookup"><span data-stu-id="21e25-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="21e25-156">`return!` Anahtar kelime bir hesaplama ifadesinin değerini fark eder ve hesaplama ifadesine karşılık gelen türle sonuçlanan sarar:</span><span class="sxs-lookup"><span data-stu-id="21e25-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="21e25-157">`return!`oluşturucu türünde `ReturnFrom(x)` üye tarafından tanımlanır, başka bir hesaplama ifadesi nerede. `x`</span><span class="sxs-lookup"><span data-stu-id="21e25-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="21e25-158">Anahtar `match!` kelime, sonucu yla ilgili başka bir hesaplama ifadesi ve desen eşleşmesine bir çağrı nın satır satırını koymanızı sağlar:</span><span class="sxs-lookup"><span data-stu-id="21e25-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="21e25-159">Bir hesaplama ifadesini çağırırken `match!`, '' gibi `let!`çağrının sonucunu fark edecektir.</span><span class="sxs-lookup"><span data-stu-id="21e25-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="21e25-160">Bu genellikle sonucun [isteğe bağlı](options.md)olduğu bir hesaplama ifadesini ararken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21e25-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="21e25-161">Yerleşik hesaplama ifadeleri</span><span class="sxs-lookup"><span data-stu-id="21e25-161">Built-in computation expressions</span></span>

<span data-ttu-id="21e25-162">F# çekirdek kitaplığı üç yerleşik hesaplama deyimi tanımlar: [Sıralı İfadeler,](sequences.md) [Eşzamanlı İş Akışları](asynchronous-workflows.md)ve Sorgu [İfadeleri.](query-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="21e25-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="21e25-163">Yeni Bir Hesaplama İfadesi Türü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="21e25-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="21e25-164">Bir oluşturucu sınıf oluşturarak ve sınıfta belirli özel yöntemleri tanımlayarak kendi hesaplama ifadelerinizin özelliklerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e25-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="21e25-165">Oluşturucu sınıf isteğe bağlı olarak aşağıdaki tabloda listelenen yöntemleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="21e25-166">Aşağıdaki tabloda iş akışı oluşturucu sınıfında kullanılabilecek yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21e25-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="21e25-167">**Yöntem**</span><span class="sxs-lookup"><span data-stu-id="21e25-167">**Method**</span></span>|<span data-ttu-id="21e25-168">**Tipik imza(lar)**</span><span class="sxs-lookup"><span data-stu-id="21e25-168">**Typical signature(s)**</span></span>|<span data-ttu-id="21e25-169">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="21e25-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="21e25-170">Çağrılan `let!` ve `do!` hesaplama ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="21e25-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="21e25-171">Bir hesaplama ifadesini işlev olarak sarar.</span><span class="sxs-lookup"><span data-stu-id="21e25-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="21e25-172">Hesaplama `return` ifadelerinde çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="21e25-173">Hesaplama `return!` ifadelerinde çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="21e25-174">`M<'T> -> M<'T>` veya</span><span class="sxs-lookup"><span data-stu-id="21e25-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="21e25-175">Bir hesaplama ifadesini yürütür.</span><span class="sxs-lookup"><span data-stu-id="21e25-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="21e25-176">`M<'T> * M<'T> -> M<'T>` veya</span><span class="sxs-lookup"><span data-stu-id="21e25-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="21e25-177">Hesaplama ifadelerinde sıralama için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="21e25-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` veya</span><span class="sxs-lookup"><span data-stu-id="21e25-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="21e25-179">Hesaplama `for...do` ifadelerinde ifadeler için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="21e25-180">Hesaplama `try...finally` ifadelerinde ifadeler için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="21e25-181">Hesaplama `try...with` ifadelerinde ifadeler için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="21e25-182">Hesaplama `use` ifadelerinde bağlama lar için çağrıda bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="21e25-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="21e25-183">Hesaplama `while...do` ifadelerinde ifadeler için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="21e25-184">Hesaplama `yield` ifadelerinde ifadeler için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="21e25-185">Hesaplama `yield!` ifadelerinde ifadeler için çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="21e25-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="21e25-186">Hesaplama ifadelerinde `else` `if...then` ifadelerin boş dalları için çağrıda bulundu.</span><span class="sxs-lookup"><span data-stu-id="21e25-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="21e25-187">Hesaplama ifadesinin `Run` üyeye tırnak olarak geçirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21e25-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="21e25-188">Bir hesaplamanın tüm örneklerini bir teklife çevirir.</span><span class="sxs-lookup"><span data-stu-id="21e25-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="21e25-189">Oluşturucu sınıfındaki yöntemlerin çoğu, `M<'T>` genellikle, örneğin eşzamanlı iş akışları ve dizi iş akışları `Async<'T>` için birleştirilen hesaplama türünü karakterize eden ayrı `Seq<'T>` tanımlanmış bir tür olan bir yapıyı kullanır ve döndürer.</span><span class="sxs-lookup"><span data-stu-id="21e25-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="21e25-190">Bu yöntemlerin imzaları, bir yapıdan döndürülen iş akışı nesnesinin bir sonrakine geçirilebilmesini sağlamak için birbiriyle birleştirilmesini ve iç içe geçmelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="21e25-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="21e25-191">Derleyici, bir hesaplama ifadesini ayrıştırdığında, önceki tablodaki yöntemleri ve hesaplama ifadesindeki kodu kullanarak ifadeyi iç içe geçmiş işlev çağrıları dizisine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="21e25-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="21e25-192">İç içe ifade aşağıdaki formdadır:</span><span class="sxs-lookup"><span data-stu-id="21e25-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="21e25-193">Yukarıdaki kodda, hesaplama `Run` ifade `Delay` oluşturucu sınıfında tanımlanmamışsa yapılan çağrılar atlanır ve atlanır.</span><span class="sxs-lookup"><span data-stu-id="21e25-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="21e25-194">Hesaplama ifadesinin gövdesi, burada belirtildiği gibi, `{| cexpr |}`aşağıdaki tabloda açıklanan çeviriler tarafından oluşturucu sınıfın yöntemlerini içeren çağrılara çevrilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="21e25-195">Hesaplama ifadesi, `{| cexpr |}` F# ifadesinin bulunduğu `expr` ve `cexpr` bir hesaplama ifadesi olduğu bu çevirilere göre özyinelemeli olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="21e25-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="21e25-196">İfadeler</span><span class="sxs-lookup"><span data-stu-id="21e25-196">Expression</span></span>|<span data-ttu-id="21e25-197">Çeviri</span><span class="sxs-lookup"><span data-stu-id="21e25-197">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="21e25-198">Önceki tabloda, `other-expr` tabloda başka türlü listelenmemiş bir ifade açıklanır.</span><span class="sxs-lookup"><span data-stu-id="21e25-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="21e25-199">Oluşturucu sınıfın tüm yöntemleri uygulaması ve önceki tabloda listelenen tüm çevirileri desteklemesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="21e25-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="21e25-200">Uygulanmayan yapılar, bu tür hesaplama ifadelerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21e25-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="21e25-201">Örneğin, hesaplama ifadelerinizdeki anahtar kelimeyi `use` desteklemek istemiyorsanız, oluşturucu sınıfınızdaki tanımı `Use` atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e25-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="21e25-202">Aşağıdaki kod örneği, bir hesaplamayı bir adım adım değerlendirilebilecek bir dizi adım olarak kapsülleyen bir hesaplama ifadesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="21e25-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="21e25-203">Ayrımcı bir birlik `OkOrException`türü, şimdiye kadar değerlendirildiği ifadenin hata durumunu kodlar.</span><span class="sxs-lookup"><span data-stu-id="21e25-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="21e25-204">Bu kod, bazı oluşturucu yöntemlerinin ortak uygulama uygulamaları gibi hesaplama ifadelerinizde kullanabileceğiniz birkaç tipik desen gösterir.</span><span class="sxs-lookup"><span data-stu-id="21e25-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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
        | Done value -> func value
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
// returns "Done 7"
comp |> step |> step |> step |> step
```

<span data-ttu-id="21e25-205">Bir hesaplama ifadesi, ifadenin döndürdüğü altta yatan bir türü vardır.</span><span class="sxs-lookup"><span data-stu-id="21e25-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="21e25-206">Temel tür, hesaplanmış bir sonucu veya gerçekleştirilebilecek gecikmiş bir hesaplamayı temsil edebilir veya bir tür koleksiyon aracılığıyla yinelenmenin bir yolunu sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="21e25-207">Önceki örnekte, altta yatan tür **Sonunda**oldu.</span><span class="sxs-lookup"><span data-stu-id="21e25-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="21e25-208">Bir sıra ifade için, <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>temel türü .</span><span class="sxs-lookup"><span data-stu-id="21e25-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21e25-209">Sorgu ifadesi için, temel <xref:System.Linq.IQueryable?displayProperty=nameWithType>tür .</span><span class="sxs-lookup"><span data-stu-id="21e25-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="21e25-210">Eşzamanlı bir iş akışı için, temel [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)tür .</span><span class="sxs-lookup"><span data-stu-id="21e25-210">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="21e25-211">Nesne, `Async` sonucu hesaplamak için gerçekleştirilecek çalışmayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21e25-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="21e25-212">Örneğin, bir [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) hesaplama yürütmek ve sonucu döndürmek için arayın.</span><span class="sxs-lookup"><span data-stu-id="21e25-212">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="21e25-213">Özel İşlemler</span><span class="sxs-lookup"><span data-stu-id="21e25-213">Custom Operations</span></span>

<span data-ttu-id="21e25-214">Bir hesaplama ifadesinde özel bir işlem tanımlayabilir ve bir hesaplama ifadesinde işleç olarak özel bir işlem kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e25-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="21e25-215">Örneğin, sorgu ifadesine bir sorgu işleci ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21e25-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="21e25-216">Özel bir işlem tanımladığınızda, hesaplama ifadesinde Verim ve For yöntemlerini tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="21e25-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="21e25-217">Özel bir işlem tanımlamak için, hesaplama ifadesi için bir oluşturucu sınıfına koyun ve sonra [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="21e25-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="21e25-218">Bu öznitelik, özel bir işlemde kullanılacak ad olan bir bağımsız değişken olarak bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="21e25-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="21e25-219">Bu ad, hesaplama ifadesinin açılış kıvırcık ayraç başında kapsamına girer.</span><span class="sxs-lookup"><span data-stu-id="21e25-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="21e25-220">Bu nedenle, bu blokta özel bir işlemle aynı ada sahip tanımlayıcılar kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="21e25-220">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="21e25-221">Örneğin, sorgu ifadeleri gibi `all` `last` tanımlayıcıların kullanılmasından kaçının.</span><span class="sxs-lookup"><span data-stu-id="21e25-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="21e25-222">Yeni Özel İşlemlerle mevcut Oluşturucuları Genişletme</span><span class="sxs-lookup"><span data-stu-id="21e25-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="21e25-223">Zaten bir oluşturucu sınıfınvarsa, özel işlemleri bu oluşturucu sınıfın dışından genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="21e25-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="21e25-224">Uzantıları modüller halinde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="21e25-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="21e25-225">Ad alanları, aynı dosya ve türün tanımlandığı aynı ad alanı bildirim grubu dışında uzantı üyeleri içeremez.</span><span class="sxs-lookup"><span data-stu-id="21e25-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="21e25-226">Aşağıdaki örnek, varolan `Microsoft.FSharp.Linq.QueryBuilder` sınıfın uzantısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21e25-226">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="21e25-227">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21e25-227">See also</span></span>

- [<span data-ttu-id="21e25-228">F# Dil Referansı</span><span class="sxs-lookup"><span data-stu-id="21e25-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="21e25-229">Zaman Uyumsuz İş Akışları</span><span class="sxs-lookup"><span data-stu-id="21e25-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="21e25-230">Diziler</span><span class="sxs-lookup"><span data-stu-id="21e25-230">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="21e25-231">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="21e25-231">Query Expressions</span></span>](query-expressions.md)
