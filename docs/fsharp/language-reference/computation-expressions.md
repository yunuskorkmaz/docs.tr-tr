---
title: Hesaplama İfadeleri
description: "' De F# denetim akışı yapıları ve bağlamaları kullanılarak sıralanmak ve birleştirilebilecek hesaplamalar yazmak için uygun bir sözdizimi oluşturmayı öğrenin."
ms.date: 03/15/2019
ms.openlocfilehash: 9222be5a585914761d3001d6649b196030eec05e
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083051"
---
# <a name="computation-expressions"></a><span data-ttu-id="87adf-103">Hesaplama İfadeleri</span><span class="sxs-lookup"><span data-stu-id="87adf-103">Computation Expressions</span></span>

<span data-ttu-id="87adf-104">İçindeki F# hesaplama ifadeleri, denetim akışı yapıları ve bağlamaları kullanılarak sıralanmak ve birleştirilebilecek hesaplamalar yazmak için kullanışlı bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="87adf-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="87adf-105">Hesaplama ifadesinin türüne bağlı olarak, monads, monoıd 'ler, Monad dönüştürücüler ve uygulama ve uygulama bilklerini ifade etmek için bir yol olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="87adf-106">Bununla birlikte, diğer dillerden farklı olarak (Haskell içindeki *Do gösterimi* gibi), bunlar tek bir soyutlama 'e bağlı değildir ve kolay ve içeriğe duyarlı bir sözdizimi gerçekleştirmek için makrolara veya diğer meta programlama formlarına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="87adf-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="87adf-107">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="87adf-107">Overview</span></span>

<span data-ttu-id="87adf-108">Hesaplamalar birçok form alabilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-108">Computations can take many forms.</span></span> <span data-ttu-id="87adf-109">En yaygın hesaplama biçimi, anlaşılması ve değiştirilmesi kolay olan tek iş parçacıklı yürütmektir.</span><span class="sxs-lookup"><span data-stu-id="87adf-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="87adf-110">Ancak, tüm hesaplama biçimleri tek iş parçacıklı yürütme kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="87adf-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="87adf-111">Bazı örnekler:</span><span class="sxs-lookup"><span data-stu-id="87adf-111">Some examples include:</span></span>

- <span data-ttu-id="87adf-112">Belirleyici olmayan hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="87adf-112">Non-deterministic computations</span></span>
- <span data-ttu-id="87adf-113">Zaman uyumsuz hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="87adf-113">Asynchronous computations</span></span>
- <span data-ttu-id="87adf-114">Etkili hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="87adf-114">Effectful computations</span></span>
- <span data-ttu-id="87adf-115">Genel hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="87adf-115">Generative computations</span></span>

<span data-ttu-id="87adf-116">Daha genel olarak, bir uygulamanın belirli bölümlerinde gerçekleştirmeniz gereken *bağlama duyarlı* hesaplamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="87adf-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="87adf-117">Bağlama duyarlı kod yazmak zor olabilir. bu sayede, bu şekilde, belirli bir bağlam dışındaki hesaplamalar, bunu yapmaktan kaçınmak için soyut hale gelir.</span><span class="sxs-lookup"><span data-stu-id="87adf-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="87adf-118">Bu soyutlamalar genellikle kendi kendinize yazmak zordur ve F# bu nedenle **Hesaplama ifadeleri**olarak adlandırılan genelleştirilmiş bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="87adf-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="87adf-119">Hesaplama ifadeleri, bağlama duyarlı hesaplamaları kodlamak için Tekdüzen bir sözdizimi ve soyutlama modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="87adf-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="87adf-120">Her hesaplama ifadesi bir *Oluşturucu* türü tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="87adf-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="87adf-121">Oluşturucu türü hesaplama ifadesi için kullanılabilir işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87adf-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="87adf-122">Bkz. özel bir hesaplama ifadesinin nasıl oluşturulacağını gösteren [Yeni bir hesaplama Ifadesi türü oluşturma](computation-expressions.md#creating-a-new-type-of-computation-expression).</span><span class="sxs-lookup"><span data-stu-id="87adf-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="87adf-123">Sözdizimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="87adf-123">Syntax overview</span></span>

<span data-ttu-id="87adf-124">Tüm hesaplama ifadeleri aşağıdaki biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="87adf-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="87adf-125">, hesaplama ifadesini tanımlayan bir Oluşturucu türünün adıdır ve `cexper` hesaplama ifadesinin ifade gövdesidir. `builder-expr`</span><span class="sxs-lookup"><span data-stu-id="87adf-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="87adf-126">Örneğin, `async` hesaplama ifade kodu şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="87adf-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="87adf-127">Önceki örnekte gösterildiği gibi, bir hesaplama ifadesinde bulunan özel, ek bir sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="87adf-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="87adf-128">Aşağıdaki ifade formları hesaplama ifadelerinde mümkündür:</span><span class="sxs-lookup"><span data-stu-id="87adf-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="87adf-129">Bu anahtar sözcüklerin her biri ve diğer standart F# anahtar sözcükler yalnızca, bir hesaplama ifadesinde, yalnızca bir destek Oluşturucu türünde tanımlıysa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="87adf-130">Bunun tek istisnası `match!`, bu, sonuç üzerinde bir kalıp eşleşmesi tarafından `let!` kullanılması için kendi sözdizimsel cukr.</span><span class="sxs-lookup"><span data-stu-id="87adf-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="87adf-131">Oluşturucu türü, hesaplama ifadesinin parçalarının birleştirilme biçimini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir deyişle, yöntemi hesaplama ifadesinin nasıl davranacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="87adf-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="87adf-132">Bir Oluşturucu sınıfını tanımlamanın başka bir yolu da, döngüler ve bağlamalar gibi birçok F# yapı işlemini özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="87adf-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="87adf-133">`let!` Anahtar sözcüğü bir çağrının sonucunu başka bir hesaplama ifadesine bir ada bağlar:</span><span class="sxs-lookup"><span data-stu-id="87adf-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="87adf-134">İle `let`bir hesaplama ifadesine çağrı bağlarsanız hesaplama ifadesinin sonucunu elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="87adf-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="87adf-135">Bunun yerine, *gerçekleştirilmemiş* çağrının değerini o hesaplama ifadesine bağlacaksınız.</span><span class="sxs-lookup"><span data-stu-id="87adf-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="87adf-136">Sonuca `let!` bağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="87adf-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="87adf-137">`let!`, Oluşturucu türündeki `Bind(x, f)` üye tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="87adf-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="87adf-138">Anahtar sözcüğü, benzeri `unit` `Zero` tür döndüren bir hesaplama ifadesini çağırmak içindir (Oluşturucu üzerinde üye tarafından tanımlanır): `do!`</span><span class="sxs-lookup"><span data-stu-id="87adf-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="87adf-139">[Zaman uyumsuz iş akışı](asynchronous-workflows.md)için bu tür olur `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="87adf-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="87adf-140">Diğer hesaplama ifadeleri için türün büyük olasılıkla olması `CExpType<unit>`olasıdır.</span><span class="sxs-lookup"><span data-stu-id="87adf-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="87adf-141">`do!`, Oluşturucu türündeki `Bind(x, f)` üye tarafından tanımlanır, burada `f` bir `unit`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="87adf-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="87adf-142">Anahtar sözcüğü, bir <xref:System.Collections.Generic.IEnumerable%601>değer olarak tüketilebilmesi için hesaplama ifadesinden bir değer döndürmektir: `yield`</span><span class="sxs-lookup"><span data-stu-id="87adf-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="87adf-143">[İçindeki C#yield anahtar kelimesiyle ](../../csharp/language-reference/keywords/yield.md)olduğu gibi, hesaplama ifadesindeki her öğe yinelene kadar geri getirilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="87adf-144">`yield`, Oluşturucu türündeki `Yield(x)` üye tarafından tanımlanır; burada `x` , geri alınacak öğedir.</span><span class="sxs-lookup"><span data-stu-id="87adf-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="87adf-145">`yield!` Anahtar sözcüğü, bir hesaplama ifadesinden bir değer koleksiyonunu düzleştirme için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="87adf-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="87adf-146">Değerlendirildiğinde, tarafından `yield!` çağrılan hesaplama ifadesinde kendi öğeleri bir tane geri alınır ve bu, sonucu düzleştirme.</span><span class="sxs-lookup"><span data-stu-id="87adf-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="87adf-147">`yield!`, bir değer koleksiyonu `YieldFrom(x)` olanOluşturucutüründekiüyetarafındantanımlanır.`x`</span><span class="sxs-lookup"><span data-stu-id="87adf-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="87adf-148">`return` Anahtar sözcüğü, hesaplama ifadesine karşılık gelen türdeki bir değeri sarmalar.</span><span class="sxs-lookup"><span data-stu-id="87adf-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="87adf-149">Kullanılarak `yield`hesaplama ifadelerinden, bir hesaplama ifadesini "tamamlaması" için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="87adf-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="87adf-150">`return`, Oluşturucu türündeki `Return(x)` üye tarafından tanımlanır; burada, kaydırabileceğiniz `x` öğedir.</span><span class="sxs-lookup"><span data-stu-id="87adf-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="87adf-151">`return!` Anahtar sözcüğü bir hesaplama ifadesinin değerini yeniden ayırır ve bu sonucu hesaplama ifadesine karşılık gelen türde kaydırır:</span><span class="sxs-lookup"><span data-stu-id="87adf-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="87adf-152">`return!`, Oluşturucu türündeki `ReturnFrom(x)` üye tarafından tanımlanır; burada `x` başka bir hesaplama ifadesi bulunur.</span><span class="sxs-lookup"><span data-stu-id="87adf-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="87adf-153">`match!` Anahtar sözcüğü 4,5 ile F# başlayarak, başka bir hesaplama ifadesine bir çağrı ve sonuç olarak bir model eşleşmesi sağlar:</span><span class="sxs-lookup"><span data-stu-id="87adf-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="87adf-154">İle `match!`bir hesaplama ifadesi çağrılırken, bunun gibi `let!`çağrının sonucu oluşur.</span><span class="sxs-lookup"><span data-stu-id="87adf-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="87adf-155">Bu, genellikle sonucun [isteğe bağlı](options.md)olduğu bir hesaplama ifadesi çağrılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="87adf-156">Yerleşik hesaplama ifadeleri</span><span class="sxs-lookup"><span data-stu-id="87adf-156">Built-in computation expressions</span></span>

<span data-ttu-id="87adf-157">Çekirdek F# kitaplık, üç yerleşik hesaplama ifadesi tanımlar: [Dizi ifadeleri](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [sorgu ifadeleri](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="87adf-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="87adf-158">Yeni bir hesaplama Ifadesi türü oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="87adf-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="87adf-159">Bir Oluşturucu sınıfı oluşturup sınıf üzerinde belirli özel yöntemleri tanımlayarak kendi hesaplama ifadelerinizin özelliklerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87adf-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="87adf-160">Oluşturucu sınıfı, isteğe bağlı olarak aşağıdaki tabloda listelenen yöntemleri tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="87adf-161">Aşağıdaki tabloda, bir iş akışı Oluşturucu sınıfında kullanılabilecek yöntemler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="87adf-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="87adf-162">**Yöntemi**</span><span class="sxs-lookup"><span data-stu-id="87adf-162">**Method**</span></span>|<span data-ttu-id="87adf-163">**Tipik imza (ler)**</span><span class="sxs-lookup"><span data-stu-id="87adf-163">**Typical signature(s)**</span></span>|<span data-ttu-id="87adf-164">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="87adf-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="87adf-165">Hesaplama ifadelerinde `let!` ve `do!` için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="87adf-166">Bir hesaplama ifadesini işlev olarak kaydırır.</span><span class="sxs-lookup"><span data-stu-id="87adf-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="87adf-167">Hesaplama ifadelerinde `return` için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="87adf-168">Hesaplama ifadelerinde `return!` için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="87adf-169">`M<'T> -> M<'T>`veya</span><span class="sxs-lookup"><span data-stu-id="87adf-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="87adf-170">Bir hesaplama ifadesi yürütür.</span><span class="sxs-lookup"><span data-stu-id="87adf-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="87adf-171">`M<'T> * M<'T> -> M<'T>`veya</span><span class="sxs-lookup"><span data-stu-id="87adf-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="87adf-172">Hesaplama ifadelerinde sıralama için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="87adf-173">`seq<'T> * ('T -> M<'U>) -> M<'U>`veya</span><span class="sxs-lookup"><span data-stu-id="87adf-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="87adf-174">Hesaplama ifadelerinde `for...do` ifadeler için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="87adf-175">Hesaplama ifadelerinde `try...finally` ifadeler için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="87adf-176">Hesaplama ifadelerinde `try...with` ifadeler için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="87adf-177">Hesaplama ifadelerinde `use` bağlamalar için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="87adf-178">Hesaplama ifadelerinde `while...do` ifadeler için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="87adf-179">Hesaplama ifadelerinde `yield` ifadeler için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="87adf-180">Hesaplama ifadelerinde `yield!` ifadeler için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="87adf-181">Hesaplama ifadelerinde `if...then` ifadelerin `else` boş dalları için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="87adf-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="87adf-182">Hesaplama ifadesinin `Run` üyeye bir teklif olarak geçtiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="87adf-182">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="87adf-183">Bir hesaplamanın tüm örneklerini bir teklife çevirir.</span><span class="sxs-lookup"><span data-stu-id="87adf-183">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="87adf-184">Bir Oluşturucu sınıfındaki yöntemlerin birçoğu kullanır ve bir `M<'T>` yapı döndürür; Örneğin, zaman uyumsuz iş akışları için, örneğin, `Async<'T>` zaman uyumsuz iş akışları ve `Seq<'T>` sıralı iş akışları için.</span><span class="sxs-lookup"><span data-stu-id="87adf-184">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="87adf-185">Bu yöntemlerin imzaları, bunların birbirleriyle birlikte birleştirilmelerini ve iç içe aktarılmasını sağlar, böylece bir yapıdan döndürülen iş akışı nesnesinin bir sonrakine geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="87adf-185">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="87adf-186">Derleyici, bir hesaplama ifadesini ayrıştırdığında, önceki tablodaki yöntemleri ve hesaplama ifadesindeki kodu kullanarak, ifadeyi iç içe geçmiş işlev çağrılarının dizisine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="87adf-186">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="87adf-187">İç içe geçmiş ifade aşağıdaki biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="87adf-187">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="87adf-188">Yukarıdaki kodda, `Run` ve `Delay` çağrıları hesaplama ifadesi Oluşturucu sınıfında tanımlanmamışsa atlanır.</span><span class="sxs-lookup"><span data-stu-id="87adf-188">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="87adf-189">Burada olarak `{| cexpr |}`belirtilen hesaplama ifadesinin gövdesi, aşağıdaki tabloda açıklanan Çeviriler tarafından Oluşturucu sınıfının yöntemlerini içeren çağrılara çevrilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-189">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="87adf-190">Hesaplama ifadesi `{| cexpr |}` bir `expr` F# ifade ve`cexpr` bir hesaplama ifadesi olduğu bu çevirilerine göre yinelemeli olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="87adf-190">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="87adf-191">İfade</span><span class="sxs-lookup"><span data-stu-id="87adf-191">Expression</span></span>|<span data-ttu-id="87adf-192">Çeviri</span><span class="sxs-lookup"><span data-stu-id="87adf-192">Translation</span></span>|
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
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
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

<span data-ttu-id="87adf-193">Önceki tabloda, `other-expr` tabloda başka bir şekilde listelenmeyen bir ifade açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87adf-193">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="87adf-194">Bir Oluşturucu sınıfının tüm yöntemleri uygulaması ve önceki tabloda listelenen tüm çevirileri desteklemesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="87adf-194">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="87adf-195">Uygulanmayan yapılar, bu türün hesaplama ifadelerinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="87adf-195">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="87adf-196">Örneğin, hesaplama ifadelerinizin `use` anahtar sözcüğünü desteklemek istemiyorsanız, Oluşturucu sınıfınızdaki `Use` tanımını atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87adf-196">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="87adf-197">Aşağıdaki kod örneği, bir hesaplamayı tek seferde bir adım değerlendirilebilecek bir dizi adım olarak kapsülleyen bir hesaplama ifadesi gösterir.</span><span class="sxs-lookup"><span data-stu-id="87adf-197">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="87adf-198">Ayrılmış bir birleşim türü `OkOrException`olan, ifadenin hata durumunu şu ana kadar değerlendirilen şekilde kodluyor.</span><span class="sxs-lookup"><span data-stu-id="87adf-198">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="87adf-199">Bu kod, bazı Oluşturucu metotlarının ortak uygulamaları gibi hesaplama ifadelerinizi kullanabileceğiniz birkaç tipik deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="87adf-199">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="87adf-200">Hesaplama ifadesinde, ifadenin döndürdüğü temel bir tür vardır.</span><span class="sxs-lookup"><span data-stu-id="87adf-200">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="87adf-201">Temel alınan tür, gerçekleştirilebilecek bir sonucu veya bir Gecikmeli hesaplamayı temsil edebilir veya bazı koleksiyon türleri arasında yineleme yapmak için bir yol sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-201">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="87adf-202">Önceki örnekte, temel alınan tür **sonunda**.</span><span class="sxs-lookup"><span data-stu-id="87adf-202">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="87adf-203">Bir dizi ifadesi için, temel alınan tür olur <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87adf-203">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87adf-204">Bir sorgu ifadesi için, temel alınan tür olur <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87adf-204">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87adf-205">Zaman uyumsuz bir iş akışı için, temel alınan [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)tür olur.</span><span class="sxs-lookup"><span data-stu-id="87adf-205">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="87adf-206">`Async` Nesnesi, sonucu hesaplamak için gerçekleştirilecek işi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="87adf-206">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="87adf-207">Örneğin, bir hesaplama yürütmek [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) ve sonucu döndürmek için öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="87adf-207">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="87adf-208">Özel Işlemler</span><span class="sxs-lookup"><span data-stu-id="87adf-208">Custom Operations</span></span>

<span data-ttu-id="87adf-209">Hesaplama ifadesinde özel bir işlem tanımlayabilir ve bir hesaplama ifadesinde bir işleç olarak özel bir işlem kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87adf-209">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="87adf-210">Örneğin, sorgu ifadesine bir sorgu işleci ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87adf-210">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="87adf-211">Özel bir işlem tanımladığınızda, hesaplama ifadesinde yield ve yöntemleri tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87adf-211">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="87adf-212">Özel bir işlem tanımlamak için, bunu hesaplama ifadesi için bir Oluşturucu sınıfına koyun ve ardından öğesini uygulayın [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="87adf-212">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="87adf-213">Bu öznitelik bir dizeyi bir özel işlemde kullanılacak olan bir bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="87adf-213">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="87adf-214">Bu ad, hesaplama ifadesinin açma küme ayracı başlangıcında kapsama girer.</span><span class="sxs-lookup"><span data-stu-id="87adf-214">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="87adf-215">Bu nedenle, bu bloktaki özel bir işlemle aynı ada sahip tanımlayıcılar kullanmamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87adf-215">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="87adf-216">Örneğin, sorgu ifadelerinde veya `all` `last` gibi tanımlayıcıların kullanılmasını önleyin.</span><span class="sxs-lookup"><span data-stu-id="87adf-216">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="87adf-217">Mevcut oluşturucuları yeni özel Işlemlerle genişletme</span><span class="sxs-lookup"><span data-stu-id="87adf-217">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="87adf-218">Zaten bir Oluşturucu sınıfınız varsa, özel işlemleri bu Oluşturucu sınıfının dışından genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="87adf-218">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="87adf-219">Uzantılar modüllerde bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="87adf-219">Extensions must be declared in modules.</span></span> <span data-ttu-id="87adf-220">Ad alanları, aynı dosya ve türün tanımlandığı aynı ad alanı bildirim grubu dışında uzantı üyeleri içeremez.</span><span class="sxs-lookup"><span data-stu-id="87adf-220">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="87adf-221">Aşağıdaki örnek, varolan `Microsoft.FSharp.Linq.QueryBuilder` sınıfının uzantısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="87adf-221">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="87adf-222">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87adf-222">See also</span></span>

- [<span data-ttu-id="87adf-223">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="87adf-223">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="87adf-224">Zaman Uyumsuz İş Akışları</span><span class="sxs-lookup"><span data-stu-id="87adf-224">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="87adf-225">Diziler</span><span class="sxs-lookup"><span data-stu-id="87adf-225">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="87adf-226">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="87adf-226">Query Expressions</span></span>](query-expressions.md)
