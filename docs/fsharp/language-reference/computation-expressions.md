---
title: Hesaplama İfadeleri
description: "' De F# denetim akışı yapıları ve bağlamaları kullanılarak sıralanmak ve birleştirilebilecek hesaplamalar yazmak için uygun bir sözdizimi oluşturmayı öğrenin."
ms.date: 11/04/2019
ms.openlocfilehash: c9ac0454221782a7ccb3d41850ca6aba4e20a72a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976782"
---
# <a name="computation-expressions"></a>Hesaplama İfadeleri

İçindeki F# hesaplama ifadeleri, denetim akışı yapıları ve bağlamaları kullanılarak sıralanmak ve birleştirilebilecek hesaplamalar yazmak için kullanışlı bir sözdizimi sağlar. Hesaplama ifadesinin türüne bağlı olarak, monads, monoıd 'ler, Monad dönüştürücüler ve uygulama ve uygulama bilklerini ifade etmek için bir yol olarak düşünülebilir. Bununla birlikte, diğer dillerden farklı olarak (Haskell içindeki *Do gösterimi* gibi), bunlar tek bir soyutlama 'e bağlı değildir ve kolay ve içeriğe duyarlı bir sözdizimi gerçekleştirmek için makrolara veya diğer meta programlama formlarına güvenmeyin.

## <a name="overview"></a>Genel bakış

Hesaplamalar birçok form alabilir. En yaygın hesaplama biçimi, anlaşılması ve değiştirilmesi kolay olan tek iş parçacıklı yürütmektir. Ancak, tüm hesaplama biçimleri tek iş parçacıklı yürütme kadar basittir. Bazı örnekler şunlardır:

- Belirleyici olmayan hesaplamalar
- Zaman uyumsuz hesaplamalar
- Etkili hesaplamalar
- Genel hesaplamalar

Daha genel olarak, bir uygulamanın belirli bölümlerinde gerçekleştirmeniz gereken *bağlama duyarlı* hesaplamalar vardır. Bağlama duyarlı kod yazmak zor olabilir. bu sayede, bu şekilde, belirli bir bağlam dışındaki hesaplamalar, bunu yapmaktan kaçınmak için soyut hale gelir. Bu soyutlamalar genellikle kendi kendinize yazmak zordur ve F# bu nedenle **Hesaplama ifadeleri**olarak adlandırılan genelleştirilmiş bir yoldur.

Hesaplama ifadeleri, bağlama duyarlı hesaplamaları kodlamak için Tekdüzen bir sözdizimi ve soyutlama modeli sunar.

Her hesaplama ifadesi bir *Oluşturucu* türü tarafından desteklenir. Oluşturucu türü hesaplama ifadesi için kullanılabilir işlemleri tanımlar. Bkz. özel bir hesaplama ifadesinin nasıl oluşturulacağını gösteren [Yeni bir hesaplama Ifadesi türü oluşturma](computation-expressions.md#creating-a-new-type-of-computation-expression).

### <a name="syntax-overview"></a>Sözdizimine genel bakış

Tüm hesaplama ifadeleri aşağıdaki biçimdedir:

```fsharp
builder-expr { cexper }
```

Burada `builder-expr` hesaplama ifadesini tanımlayan bir Oluşturucu türünün adıdır ve `cexper` hesaplama ifadesinin ifade gövdesidir. Örneğin, `async` hesaplama ifade kodu şöyle görünebilir:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Önceki örnekte gösterildiği gibi, bir hesaplama ifadesinde bulunan özel, ek bir sözdizimi vardır. Aşağıdaki ifade formları hesaplama ifadelerinde mümkündür:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Bu anahtar sözcüklerin her biri ve diğer standart F# anahtar sözcükler yalnızca, bir hesaplama ifadesinde, yalnızca bir destek Oluşturucu türünde tanımlıysa kullanılabilir. Bunun tek istisnası, `let!` kullanımı için kendi sözdizimi olan ve sonuç üzerinde bir kalıp eşleşmesi olan `match!`.

Oluşturucu türü, hesaplama ifadesinin parçalarının birleştirilme biçimini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir deyişle, yöntemi hesaplama ifadesinin nasıl davranacağını denetler. Bir Oluşturucu sınıfını tanımlamanın başka bir yolu da, döngüler ve bağlamalar gibi birçok F# yapı işlemini özelleştirmenizi sağlar.

### `let!`

`let!` anahtar sözcüğü, bir çağrının sonucunu başka bir hesaplama ifadesine bir ada bağlar:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

`let`ile bir hesaplama ifadesine çağrı bağlarsanız hesaplama ifadesinin sonucunu elde edersiniz. Bunun yerine, *gerçekleştirilmemiş* çağrının değerini o hesaplama ifadesine bağlacaksınız. Sonuca bağlamak için `let!` kullanın.

`let!`, Oluşturucu türündeki `Bind(x, f)` üyesi tarafından tanımlanır.

### `do!`

`do!` anahtar sözcüğü, `unit`benzeri bir tür döndüren bir hesaplama ifadesi çağırmak içindir (Oluşturucu üzerinde `Zero` üyesi tarafından tanımlanır):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

[Zaman uyumsuz iş akışı](asynchronous-workflows.md)için bu tür `Async<unit>`. Diğer hesaplama ifadeleri için türün `CExpType<unit>`olması olasıdır.

`do!`, Oluşturucu türünde `Bind(x, f)` üyesi tarafından tanımlanır; burada `f` bir `unit`üretir.

### `yield`

`yield` anahtar sözcüğü, bir <xref:System.Collections.Generic.IEnumerable%601>olarak tüketilebilmesi için hesaplama ifadesinden bir değer döndürmektir:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Çoğu durumda, çağıranlar tarafından atlanabilir. `yield` atlamak için en yaygın yol `->` işleçtir:

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

Birçok farklı değer sağlayan daha karmaşık ifadeler ve belki de koşulsuz olarak anahtar sözcüğü atlayarak şunları yapabilirsiniz:

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

[İçindeki C#yield anahtar kelimesiyle ](../../csharp/language-reference/keywords/yield.md)olduğu gibi, hesaplama ifadesindeki her öğe yinelene kadar geri getirilir.

`yield`, Oluşturucu türünde `Yield(x)` üyesi tarafından tanımlanır; burada `x`, geri alınacak öğedir.

### `yield!`

`yield!` anahtar sözcüğü, bir hesaplama ifadesinden bir değer koleksiyonunu düzleştirme için kullanılır:

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

Değerlendirildiğinde, `yield!` tarafından çağrılan hesaplama ifadesi, öğeleri bir tane geri dönerek, sonucu düzleştirilir.

`yield!`, Oluşturucu türünde `YieldFrom(x)` üyesi tarafından tanımlanır; burada `x` bir değerler koleksiyonudur.

`yield`aksine, `yield!` açıkça belirtilmelidir. Hesaplama ifadelerinde, davranışı örtük değildir.

### `return`

`return` anahtar sözcüğü, hesaplama ifadesine karşılık gelen türdeki bir değeri kaydırır. Hesaplama ifadelerinden `yield`kullanarak, bir hesaplama ifadesini "tamamlaması" için kullanılır:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`, Oluşturucu türünde `Return(x)` üyesi tarafından tanımlanır; burada `x`, kaydırabileceğiniz öğedir.

### `return!`

`return!` anahtar sözcüğü bir hesaplama ifadesinin değerini ve bu sonucu hesaplama ifadesine karşılık gelen türde kaydırır.

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`, Oluşturucu türü üzerinde `ReturnFrom(x)` üyesi tarafından tanımlanır; burada `x` başka bir hesaplama ifadesi olur.

### `match!`

4,5 ile F# başlayarak`match!`anahtar sözcüğü, başka bir hesaplama ifadesine bir çağrı ve bunun sonucunda bir model eşleşmesi sağlar:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

`match!`ile bir hesaplama ifadesi çağrılırken, `let!`gibi çağrının sonucu oluşur. Bu, genellikle sonucun [isteğe bağlı](options.md)olduğu bir hesaplama ifadesi çağrılırken kullanılır.

## <a name="built-in-computation-expressions"></a>Yerleşik hesaplama ifadeleri

F# Çekirdek kitaplık üç yerleşik hesaplama ifadesi tanımlar: [dizi ifadeleri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md)ve [sorgu ifadeleri](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Yeni bir hesaplama Ifadesi türü oluşturuluyor

Bir Oluşturucu sınıfı oluşturup sınıf üzerinde belirli özel yöntemleri tanımlayarak kendi hesaplama ifadelerinizin özelliklerini tanımlayabilirsiniz. Oluşturucu sınıfı, isteğe bağlı olarak aşağıdaki tabloda listelenen yöntemleri tanımlayabilir.

Aşağıdaki tabloda, bir iş akışı Oluşturucu sınıfında kullanılabilecek yöntemler açıklanmıştır.

|**Yöntemidir**|**Tipik imza (ler)**|**Açıklama**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Hesaplama ifadelerinde `let!` ve `do!` için çağırılır.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Bir hesaplama ifadesini işlev olarak kaydırır.|
|`Return`|`'T -> M<'T>`|Hesaplama ifadelerinde `return` için çağırılır.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Hesaplama ifadelerinde `return!` için çağırılır.|
|`Run`|`M<'T> -> M<'T>` veya<br /><br />`M<'T> -> 'T`|Bir hesaplama ifadesi yürütür.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` veya<br /><br />`M<unit> * M<'T> -> M<'T>`|Hesaplama ifadelerinde sıralama için çağırılır.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` veya<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Hesaplama ifadelerinde `for...do` ifadeleri için çağırılır.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Hesaplama ifadelerinde `try...finally` ifadeleri için çağırılır.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Hesaplama ifadelerinde `try...with` ifadeleri için çağırılır.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Hesaplama ifadelerinde `use` bağlamaları için çağırılır.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Hesaplama ifadelerinde `while...do` ifadeleri için çağırılır.|
|`Yield`|`'T -> M<'T>`|Hesaplama ifadelerinde `yield` ifadeleri için çağırılır.|
|`YieldFrom`|`M<'T> -> M<'T>`|Hesaplama ifadelerinde `yield!` ifadeleri için çağırılır.|
|`Zero`|`unit -> M<'T>`|Hesaplama ifadelerinde `if...then` ifadelerinin boş `else` dalları için çağırılır.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Hesaplama ifadesinin `Run` üyesine alıntı olarak geçtiğini gösterir. Bir hesaplamanın tüm örneklerini bir teklife çevirir.|

Bir Oluşturucu sınıfındaki yöntemlerin birçoğu kullanır ve bir `M<'T>` yapısı döndürür. Bu, örneğin, zaman uyumsuz iş akışları için `Async<'T>` ve sıra için `Seq<'T>`, genellikle ayrı bir tanımlı tür oluşturur. sürdürülen. Bu yöntemlerin imzaları, bunların birbirleriyle birlikte birleştirilmelerini ve iç içe aktarılmasını sağlar, böylece bir yapıdan döndürülen iş akışı nesnesinin bir sonrakine geçirilmesi gerekir. Derleyici, bir hesaplama ifadesini ayrıştırdığında, önceki tablodaki yöntemleri ve hesaplama ifadesindeki kodu kullanarak, ifadeyi iç içe geçmiş işlev çağrılarının dizisine dönüştürür.

İç içe geçmiş ifade aşağıdaki biçimdedir:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Yukarıdaki kodda, hesaplama ifadesi Oluşturucu sınıfında tanımlanmamışsa `Run` ve `Delay` çağrıları atlanır. `{| cexpr |}`olarak belirtilen hesaplama ifadesinin gövdesi, aşağıdaki tabloda açıklanan Çeviriler tarafından Oluşturucu sınıfının yöntemlerini içeren çağrılara çevrilir. Hesaplama ifadesi `{| cexpr |}`, `expr` bir F# ifade olduğu ve`cexpr`bir hesaplama ifadesi olduğu bu çevirilerine göre özyinelemeli olarak tanımlanır.

|İfade|İde|
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

Önceki tabloda, `other-expr` tabloda listelenmeyen bir ifadeyi açıklar. Bir Oluşturucu sınıfının tüm yöntemleri uygulaması ve önceki tabloda listelenen tüm çevirileri desteklemesi gerekmez. Uygulanmayan yapılar, bu türün hesaplama ifadelerinde kullanılamaz. Örneğin, hesaplama ifadelerinizin `use` anahtar sözcüğünü desteklemek istemiyorsanız, Oluşturucu sınıfınızdaki `Use` tanımını atlayabilirsiniz.

Aşağıdaki kod örneği, bir hesaplamayı tek seferde bir adım değerlendirilebilecek bir dizi adım olarak kapsülleyen bir hesaplama ifadesi gösterir. Ayrılmış bir birleşim türü, `OkOrException`, ifadenin hata durumunu şu ana kadar değerlendirilen şekilde kodluyor. Bu kod, bazı Oluşturucu metotlarının ortak uygulamaları gibi hesaplama ifadelerinizi kullanabileceğiniz birkaç tipik deseni gösterir.

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

Hesaplama ifadesinde, ifadenin döndürdüğü temel bir tür vardır. Temel alınan tür, gerçekleştirilebilecek bir sonucu veya bir Gecikmeli hesaplamayı temsil edebilir veya bazı koleksiyon türleri arasında yineleme yapmak için bir yol sağlayabilir. Önceki örnekte, temel alınan tür **sonunda**. Bir dizi ifadesi için, temel alınan tür <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Bir sorgu ifadesi için, temel alınan tür <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Zaman uyumsuz bir iş akışı için, temel alınan tür [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` nesnesi, sonucu hesaplamak için gerçekleştirilecek işi temsil eder. Örneğin, bir hesaplamayı yürütmek için [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) çağırır ve sonucu döndürür.

## <a name="custom-operations"></a>Özel İşlemler

Hesaplama ifadesinde özel bir işlem tanımlayabilir ve bir hesaplama ifadesinde bir işleç olarak özel bir işlem kullanabilirsiniz. Örneğin, sorgu ifadesine bir sorgu işleci ekleyebilirsiniz. Özel bir işlem tanımladığınızda, hesaplama ifadesinde yield ve yöntemleri tanımlamanız gerekir. Özel bir işlem tanımlamak için, bunu hesaplama ifadesi için bir Oluşturucu sınıfına koyun ve ardından [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)uygulayın. Bu öznitelik bir dizeyi bir özel işlemde kullanılacak olan bir bağımsız değişken olarak alır. Bu ad, hesaplama ifadesinin açma küme ayracı başlangıcında kapsama girer. Bu nedenle, bu bloktaki özel bir işlemle aynı ada sahip tanımlayıcılar kullanmamanız gerekir. Örneğin, sorgu ifadelerinde `all` veya `last` gibi tanımlayıcıların kullanılmasını önleyin.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Mevcut oluşturucuları yeni özel Işlemlerle genişletme

Zaten bir Oluşturucu sınıfınız varsa, özel işlemleri bu Oluşturucu sınıfının dışından genişletilebilir. Uzantılar modüllerde bildirilmelidir. Ad alanları, aynı dosya ve türün tanımlandığı aynı ad alanı bildirim grubu dışında uzantı üyeleri içeremez.

Aşağıdaki örnek, varolan `Microsoft.FSharp.Linq.QueryBuilder` sınıfının uzantısını gösterir.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)
- [Diziler](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Sorgu İfadeleri](query-expressions.md)
