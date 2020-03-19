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
# <a name="computation-expressions"></a>Hesaplama İfadeleri

F#'daki hesaplama ifadeleri, denetim akışı yapıları ve bağlamaları kullanılarak sıralanabilen ve birleştirilebilen hesaplamalar yazmak için kullanışlı bir sözdizimi sağlar. Hesaplama ifade türüne bağlı olarak, onlar monads, monoids, monad transformatörler ve aplikatif functors ifade etmek için bir yol olarak düşünülebilir. Ancak, diğer dillerin (Haskell'daki *do-notation* gibi) aksine, tek bir soyutlamayla bağlı değildirler ve uygun ve içeriğe duyarlı bir sözdizimini gerçekleştirmek için makrolara veya diğer meta programlama biçimlerine güvenmezler.

## <a name="overview"></a>Genel Bakış

Hesaplamalar çeşitli şekillerde olabilir. En yaygın hesaplama biçimi, anlaşılması ve değiştirilmesi kolay tek iş parçacığı yürütmedir. Ancak, tüm hesaplama biçimleri tek iş parçacığı yürütme kadar basit değildir. Bazı örnekler:

- Deterministik olmayan hesaplamalar
- Asynchronous hesaplamaları
- Etkili hesaplamalar
- Üretici hesaplamaları

Daha genel olarak, bir uygulamanın belirli bölümlerinde gerçekleştirmeniz gereken *içeriğe duyarlı* hesaplamalar vardır. İçeriğe duyarlı kod yazmak zor olabilir, çünkü bunu yapmanızı engellemek için soyutlamalar olmadan belirli bir bağlamın dışında hesaplamaları "sızdırmak" kolaydır. Bu soyutlamalar genellikle kendiniz yazmak zor, bu yüzden F # sözde **hesaplama ifadeleri**yapmak için genelleştirilmiş bir yolu vardır.

Hesaplama ifadeleri, içeriğe duyarlı hesaplamaları kodlamak için tek biçimli bir sözdizimi ve soyutlama modeli sunar.

Her hesaplama ifadesi bir *oluşturucu* türü tarafından desteklenen. Oluşturucu türü, hesaplama ifadesi için kullanılabilen işlemleri tanımlar. Bkz. Özel bir hesaplama ifadesinin nasıl oluşturulup oluşturulturunu gösteren [Yeni Bir Hesaplama İfadesi Türü Oluşturma.](computation-expressions.md#creating-a-new-type-of-computation-expression)

### <a name="syntax-overview"></a>Sözdizimine genel bakış

Tüm hesaplama ifadeleri aşağıdaki formu vardır:

```fsharp
builder-expr { cexper }
```

nerede `builder-expr` hesaplama ifadesini tanımlayan bir oluşturucu türünün adıdır `cexper` ve hesaplama ifadesinin ifade gövdesidir. Örneğin, `async` hesaplama ifade kodu şu şekilde görünebilir:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Önceki örnekte gösterildiği gibi, bir hesaplama ifadesi içinde özel, ek sözdizimi vardır. Aşağıdaki ifade formları hesaplama ifadeleri ile mümkündür:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Bu anahtar kelimelerin her biri ve diğer standart F# anahtar kelimeleri yalnızca destek oluşturucu türünde tanımlanmışsa, bir hesaplama ifadesinde kullanılabilir. Bunun tek `match!`istisnası, kendisi sonucu bir desen maç `let!` takip kullanımı için sözdizimli şeker olmasıdır.

Oluşturucu türü, hesaplama ifadesinin parçalarının birleştirilmesi yöntemini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir de, yöntemleri hesaplama ifadesinin nasıl olacağını denetler. Oluşturucu sınıfını tanımlamanın başka bir yolu da, döngüler ve bağlamalar gibi birçok F# yapısının çalışmasını özelleştirmenize olanak sağladığını söylemektir.

### `let!`

Anahtar `let!` kelime, bir ada yapılan bir çağrının sonucunu başka bir hesaplama ifadesine bağlar:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Aramayı bir hesaplama ifadesine `let`bağlarsanız, hesaplama ifadesinin sonucunu alamazsınız. Bunun yerine, *gerçekleşmemiş* çağrının değerini bu hesaplama ifadesine bağlamış olursunuz. Sonuca `let!` bağlamak için kullanın.

`let!`oluşturucu türünde `Bind(x, f)` üye tarafından tanımlanır.

### `do!`

Anahtar `do!` kelime, (oluşturucudaki `Zero` üye tarafından `unit`tanımlanan) benzer bir türü döndüren bir hesaplama ifadesini çağırmak içindir:

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

[Async iş akışı](asynchronous-workflows.md)için, `Async<unit>`bu tür . Diğer hesaplama ifadeleri için, tür `CExpType<unit>`.

`do!`oluşturucu türünde `Bind(x, f)` üye tarafından tanımlanır, burada `f` bir `unit`.

### `yield`

Anahtar `yield` kelime, hesaplama ifadesinden bir değeri döndürmeiçindir, böylece aşağıdaki <xref:System.Collections.Generic.IEnumerable%601>ler olarak tüketilebilir:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Çoğu durumda, arayanlar tarafından atlanabilir. Atlatır'ın `yield` en yaygın yolu `->` işleçtir:

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

Birçok farklı değer verebilecek daha karmaşık ifadeler için ve belki de koşullu olarak, anahtar sözcüğü atlayarak şunları yapabilir:

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

[C#'daki verim anahtar sözcüğünde](../../csharp/language-reference/keywords/yield.md)olduğu gibi, hesaplama ifadesindeki her öğe, yinelenirken geri verilir.

`yield`oluşturucu türünde `Yield(x)` üye tarafından tanımlanır, geri verim için öğe nerede. `x`

### `yield!`

Anahtar `yield!` kelime, bir hesaplama ifadesinden değerler koleksiyonunu düzleştirmek içindir:

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

Değerlendirildiğinde, tarafından `yield!` çağrılan hesaplama ifadesi, öğelerini birer birer geri vererek sonucu düzleştirmek zorunda kalarak elde edilir.

`yield!`değer koleksiyonu `YieldFrom(x)` nun bulunduğu `x` oluşturucu türündeki üye tarafından tanımlanır.

`yield`Aksine, `yield!` açıkça belirtilmelidir. Davranışı hesaplama ifadelerinde örtük değildir.

### `return`

`return` Anahtar kelime, hesaplama ifadesine karşılık gelen türdeki bir değeri sarar. Bir hesaplama ifadesini `yield`"tamamlamak" için kullanılır:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`oluşturucu türünde `Return(x)` üye tarafından tanımlanır, nerede `x` kaydırmak için öğedir.

### `return!`

`return!` Anahtar kelime bir hesaplama ifadesinin değerini fark eder ve hesaplama ifadesine karşılık gelen türle sonuçlanan sarar:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`oluşturucu türünde `ReturnFrom(x)` üye tarafından tanımlanır, başka bir hesaplama ifadesi nerede. `x`

### `match!`

Anahtar `match!` kelime, sonucu yla ilgili başka bir hesaplama ifadesi ve desen eşleşmesine bir çağrı nın satır satırını koymanızı sağlar:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Bir hesaplama ifadesini çağırırken `match!`, '' gibi `let!`çağrının sonucunu fark edecektir. Bu genellikle sonucun [isteğe bağlı](options.md)olduğu bir hesaplama ifadesini ararken kullanılır.

## <a name="built-in-computation-expressions"></a>Yerleşik hesaplama ifadeleri

F# çekirdek kitaplığı üç yerleşik hesaplama deyimi tanımlar: [Sıralı İfadeler,](sequences.md) [Eşzamanlı İş Akışları](asynchronous-workflows.md)ve Sorgu [İfadeleri.](query-expressions.md)

## <a name="creating-a-new-type-of-computation-expression"></a>Yeni Bir Hesaplama İfadesi Türü Oluşturma

Bir oluşturucu sınıf oluşturarak ve sınıfta belirli özel yöntemleri tanımlayarak kendi hesaplama ifadelerinizin özelliklerini tanımlayabilirsiniz. Oluşturucu sınıf isteğe bağlı olarak aşağıdaki tabloda listelenen yöntemleri tanımlayabilir.

Aşağıdaki tabloda iş akışı oluşturucu sınıfında kullanılabilecek yöntemler açıklanmaktadır.

|**Yöntem**|**Tipik imza(lar)**|**Açıklama**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Çağrılan `let!` ve `do!` hesaplama ifadeleri.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Bir hesaplama ifadesini işlev olarak sarar.|
|`Return`|`'T -> M<'T>`|Hesaplama `return` ifadelerinde çağrıldı.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Hesaplama `return!` ifadelerinde çağrıldı.|
|`Run`|`M<'T> -> M<'T>` veya<br /><br />`M<'T> -> 'T`|Bir hesaplama ifadesini yürütür.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` veya<br /><br />`M<unit> * M<'T> -> M<'T>`|Hesaplama ifadelerinde sıralama için çağrıldı.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` veya<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Hesaplama `for...do` ifadelerinde ifadeler için çağrıldı.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Hesaplama `try...finally` ifadelerinde ifadeler için çağrıldı.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Hesaplama `try...with` ifadelerinde ifadeler için çağrıldı.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Hesaplama `use` ifadelerinde bağlama lar için çağrıda bulunuldu.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Hesaplama `while...do` ifadelerinde ifadeler için çağrıldı.|
|`Yield`|`'T -> M<'T>`|Hesaplama `yield` ifadelerinde ifadeler için çağrıldı.|
|`YieldFrom`|`M<'T> -> M<'T>`|Hesaplama `yield!` ifadelerinde ifadeler için çağrıldı.|
|`Zero`|`unit -> M<'T>`|Hesaplama ifadelerinde `else` `if...then` ifadelerin boş dalları için çağrıda bulundu.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Hesaplama ifadesinin `Run` üyeye tırnak olarak geçirildiğini gösterir. Bir hesaplamanın tüm örneklerini bir teklife çevirir.|

Oluşturucu sınıfındaki yöntemlerin çoğu, `M<'T>` genellikle, örneğin eşzamanlı iş akışları ve dizi iş akışları `Async<'T>` için birleştirilen hesaplama türünü karakterize eden ayrı `Seq<'T>` tanımlanmış bir tür olan bir yapıyı kullanır ve döndürer. Bu yöntemlerin imzaları, bir yapıdan döndürülen iş akışı nesnesinin bir sonrakine geçirilebilmesini sağlamak için birbiriyle birleştirilmesini ve iç içe geçmelerini sağlar. Derleyici, bir hesaplama ifadesini ayrıştırdığında, önceki tablodaki yöntemleri ve hesaplama ifadesindeki kodu kullanarak ifadeyi iç içe geçmiş işlev çağrıları dizisine dönüştürür.

İç içe ifade aşağıdaki formdadır:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Yukarıdaki kodda, hesaplama `Run` ifade `Delay` oluşturucu sınıfında tanımlanmamışsa yapılan çağrılar atlanır ve atlanır. Hesaplama ifadesinin gövdesi, burada belirtildiği gibi, `{| cexpr |}`aşağıdaki tabloda açıklanan çeviriler tarafından oluşturucu sınıfın yöntemlerini içeren çağrılara çevrilir. Hesaplama ifadesi, `{| cexpr |}` F# ifadesinin bulunduğu `expr` ve `cexpr` bir hesaplama ifadesi olduğu bu çevirilere göre özyinelemeli olarak tanımlanır.

|İfadeler|Çeviri|
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

Önceki tabloda, `other-expr` tabloda başka türlü listelenmemiş bir ifade açıklanır. Oluşturucu sınıfın tüm yöntemleri uygulaması ve önceki tabloda listelenen tüm çevirileri desteklemesi gerekmez. Uygulanmayan yapılar, bu tür hesaplama ifadelerinde kullanılamaz. Örneğin, hesaplama ifadelerinizdeki anahtar kelimeyi `use` desteklemek istemiyorsanız, oluşturucu sınıfınızdaki tanımı `Use` atlayabilirsiniz.

Aşağıdaki kod örneği, bir hesaplamayı bir adım adım değerlendirilebilecek bir dizi adım olarak kapsülleyen bir hesaplama ifadesini gösterir. Ayrımcı bir birlik `OkOrException`türü, şimdiye kadar değerlendirildiği ifadenin hata durumunu kodlar. Bu kod, bazı oluşturucu yöntemlerinin ortak uygulama uygulamaları gibi hesaplama ifadelerinizde kullanabileceğiniz birkaç tipik desen gösterir.

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

Bir hesaplama ifadesi, ifadenin döndürdüğü altta yatan bir türü vardır. Temel tür, hesaplanmış bir sonucu veya gerçekleştirilebilecek gecikmiş bir hesaplamayı temsil edebilir veya bir tür koleksiyon aracılığıyla yinelenmenin bir yolunu sağlayabilir. Önceki örnekte, altta yatan tür **Sonunda**oldu. Bir sıra ifade için, <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>temel türü . Sorgu ifadesi için, temel <xref:System.Linq.IQueryable?displayProperty=nameWithType>tür . Eşzamanlı bir iş akışı için, temel [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)tür . Nesne, `Async` sonucu hesaplamak için gerçekleştirilecek çalışmayı temsil eder. Örneğin, bir [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) hesaplama yürütmek ve sonucu döndürmek için arayın.

## <a name="custom-operations"></a>Özel İşlemler

Bir hesaplama ifadesinde özel bir işlem tanımlayabilir ve bir hesaplama ifadesinde işleç olarak özel bir işlem kullanabilirsiniz. Örneğin, sorgu ifadesine bir sorgu işleci ekleyebilirsiniz. Özel bir işlem tanımladığınızda, hesaplama ifadesinde Verim ve For yöntemlerini tanımlamanız gerekir. Özel bir işlem tanımlamak için, hesaplama ifadesi için bir oluşturucu sınıfına koyun ve sonra [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Bu öznitelik, özel bir işlemde kullanılacak ad olan bir bağımsız değişken olarak bir dize alır. Bu ad, hesaplama ifadesinin açılış kıvırcık ayraç başında kapsamına girer. Bu nedenle, bu blokta özel bir işlemle aynı ada sahip tanımlayıcılar kullanmamalısınız. Örneğin, sorgu ifadeleri gibi `all` `last` tanımlayıcıların kullanılmasından kaçının.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Yeni Özel İşlemlerle mevcut Oluşturucuları Genişletme

Zaten bir oluşturucu sınıfınvarsa, özel işlemleri bu oluşturucu sınıfın dışından genişletilebilir. Uzantıları modüller halinde bildirilmelidir. Ad alanları, aynı dosya ve türün tanımlandığı aynı ad alanı bildirim grubu dışında uzantı üyeleri içeremez.

Aşağıdaki örnek, varolan `Microsoft.FSharp.Linq.QueryBuilder` sınıfın uzantısını gösterir.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
- [Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)
- [Diziler](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Sorgu İfadeleri](query-expressions.md)
