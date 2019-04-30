---
title: Hesaplama İfadeleri
description: Yazma hesaplamalar için uygun söz dizimini oluşturmayı F# olması sıralı ve birleşik kullanarak denetleyebilir, akışı yapılarını ve bağlamalar.
ms.date: 03/15/2019
ms.openlocfilehash: 3c2abb5c6204309fc8d5215a53ce8af46c01d218
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766070"
---
# <a name="computation-expressions"></a>Hesaplama İfadeleri

Hesaplama ifadeleri F# sıralı ve denetim akışı yapılarını ve bağlamalar kullanılarak birleştirilen hesaplamalar yazmak için kullanışlı bir söz dizimi sağlar. Hesaplama ifadesi türüne bağlı olarak bunlar, monadları, monoids monad dönüştürücüler ve applicative işlev nesneleri ifade etmenin bir yolu olarak düşünülebilir. Ancak, diğer diller aksine (gibi *gösterimi* Haskell içinde), tek bir soyutlama bağlı değil ve makroları veya diğer tür güvenmeyin azaltılarak kullanışlı ve bağlama duyarlı bir söz dizimi gerçekleştirmek için.

## <a name="overview"></a>Genel Bakış

Hesaplamaları birçok biçimde olabilir. En yaygın hesaplamanın anlamak ve değiştirilmesi kolay olan tek iş parçacıklı yürütme biçimidir. Ancak, tüm biçimlerinin hesaplama tek iş parçacıklı yürütme basit değildir. Bazı örnekler:

* Belirleyici olmayan hesaplamaları
* Zaman uyumsuz hesaplamalar
* Effectful hesaplamaları
* Games'in hesaplamaları

Daha genel vardır *bağlama duyarlı* hesaplamalar bir uygulamanın bazı bölümlerini gerçekleştirmeniz gerekir. Belirli bir bağlam olmadan bunu yapmasını önlemek için soyutlama dışında "sızıntısı" hesaplamalar kolay olduğundan bağlama duyarlı kod yazma, zor olabilir. Bu soyutlama genellikle kendiniz tarafından olmasının nedeni yazmak zor F# yorumun yapmak için genelleştirilmiş bir yolu yoktur **hesaplama ifadeleri**.

Hesaplama ifadeleri, bağlama duyarlı hesaplamalar kodlaması için Tekdüzen bir söz dizimi ve Özet modeli sunar.

Her hesaplama ifadesi tarafından yedeklenen bir *Oluşturucu* türü. Oluşturucu türü hesaplama ifadesi için kullanılabilen işlemleri tanımlar. Bkz: [yeni bir tür, hesaplama ifadesi oluşturma](computation-expressions.md#creating-a-new-type-of-computation-expression), özel hesaplama ifadesi oluşturma işlemini gösterir.

### <a name="syntax-overview"></a>Söz dizimi genel bakış

Tüm hesaplama ifadeleri, aşağıdaki biçime sahiptir:

```
builder-expr { cexper }
```

Burada `builder-expr` hesaplama ifadesi tanımlayan bir oluşturucu türüne adıdır ve `cexper` hesaplama ifadesi ifade gövdesi. Örneğin, `async` hesaplama ifadesi kod şuna benzeyebilir:

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Özel, ek bir söz dizimi bir hesaplama ifadesi içinde mevcut değildir önceki örnekte gösterildiği gibi. Hesaplama ifadeleri ile aşağıdaki ifade biçimleri desteklenir:

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Her biri bu anahtar sözcükler ve diğer standart F# anahtar sözcükler yalnızca bir hesaplama ifadesinde kullanılabilir yedekleme Oluşturucu türü tanımlanmışsa. Bunun tek özel durum `match!`, kendisi kullanımına yönelik söz dizimi sugar `let!` sonucuna bir desen eşleşmesi tarafından izlenen.

Oluşturucu türü hesaplama ifadesi parçalarını birleştirilir biçimini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir deyişle, hesaplama ifadesi nasıl davranacağını metotlarını denetler. Bir oluşturucu sınıf tanımlamak için başka bir çoğu işlemi özelleştirmenize olanak sağlayan söylemek yoludur F# , döngüler ve bağlamalar gibi oluşturur.

### `let!`

`let!` Anahtar sözcüğü bir ad ile başka bir hesaplama ifadesi için bir çağrı sonucunu bağlar:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Bir hesaplama ifadesi ile çağrı bağlama `let`, hesaplama ifadesi sonucu almazsınız. Bunun yerine, değeri bağlı *gerçekleşmemiş* çağırmak için hesaplama ifadesi. Kullanım `let!` sonucu bağlamak için.

`let!` tarafından tanımlanan `Bind(x, f)` üyesi Oluşturucu türü.

### `do!`

`do!` Anahtar sözcüğü, bir hesaplama ifadesi çağıran döndürür bir `unit`-ister türü (tarafından tanımlanan `Zero` üyesi oluşturucu üzerinde):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

İçin [zaman uyumsuz iş akışı](asynchronous-workflows.md), bu tür `Async<unit>`. Türü diğer hesaplama ifadeleri için büyük olasılıkla `CExpType<unit>`.

`do!` tarafından tanımlanan `Bind(x, f)` Oluşturucu türü üyesinde burada `f` üreten bir `unit`.

### `yield`

`yield` Anahtar sözcüğü, böylece olarak kullanılabilecek bir değer hesaplama ifadesinden döndürmek için bir <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Olduğu gibi [C# anahtar sözcüğü yield](../../csharp/language-reference/keywords/yield.md), hesaplama ifadesi içindeki her öğeyi geri yinelendiğinde olarak oluşturulur.

`yield` tarafından tanımlanan `Yield(x)` Oluşturucu türü üyesinde burada `x` geri yield öğedir.

### `yield!`

`yield!` Anahtar sözcüğü, bir hesaplama ifadesi değerleri koleksiyonunu düzleştirme için:

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

Hesaplama ifadesi değerlendirildiğinde, çağıran `yield!` öğelerinden geri bir sonuç düzleştirme tek, veriyor olması.

`yield!` tarafından tanımlanan `YieldFrom(x)` Oluşturucu türü üyesinde burada `x` değerleri oluşan bir koleksiyondur.

### `return`

`return` Anahtar sözcüğü hesaplama ifadesi için karşılık gelen türünde bir değeri sarar. Hesaplama ifadeleri kullanarak yanı sıra `yield`, "bir hesaplama ifadesi tamamlamak için" kullanılır:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` tarafından tanımlanan `Return(x)` Oluşturucu türü üyesinde burada `x` sarmalamak için öğesi.

### `return!`

`return!` Anahtar sözcüğü bir hesaplama ifadesi değerini fark etti ve hesaplama ifadesi için karşılık gelen türü sonucu sarmalar:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` tarafından tanımlanan `ReturnFrom(x)` Oluşturucu türü üyesinde burada `x` başka bir hesaplama ifadesi.

### `match!`

İle başlayarak F# 4.5 `match!` anahtar sözcüğü verir satır içi bir çağrı sonucunu üzerinde başka bir hesaplama ifadesi ve desen eşleştirme için:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Bir hesaplama ifadesi ile çağrılırken `match!`, gibi çağrısının sonucuna fark edeceksiniz `let!`. Bu genellikle bir hesaplama ifadesi sonucu olduğu çağrıldığında kullanılır bir [isteğe bağlı](options.md).

## <a name="built-in-computation-expressions"></a>Yerleşik hesaplama ifadeleri

F# Çekirdek kitaplığı, üç yerleşik hesaplama ifadeleri tanımlar: [Sequence ifadeleri](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [sorgu ifadelerinde](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Yeni bir hesaplama ifadesi türü oluşturma

Builder sınıfı oluşturarak ve sınıf üzerinde belirli özel yöntemler tanımlayarak kendi hesaplama ifadeleri özelliklerini tanımlayabilirsiniz. Builder sınıfı, isteğe bağlı olarak aşağıdaki tabloda listelendiği gibi yöntemleri tanımlayabilirsiniz.

Aşağıdaki tablo, bir iş akışı Oluşturucu sınıfta kullanılabilir yöntemleri açıklar.

|**Yöntemi**|**Tipik bir imza**|**Açıklama**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|İçin adlı `let!` ve `do!` hesaplama ifadeleri de.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Bir hesaplama ifadesi bir işlev olarak sarmalar.|
|`Return`|`'T -> M<'T>`|İçin adlı `return` hesaplama ifadeleri de.|
|`ReturnFrom`|`M<'T> -> M<'T>`|İçin adlı `return!` hesaplama ifadeleri de.|
|`Run`|`M<'T> -> M<'T>` veya<br /><br />`M<'T> -> 'T`|Hesaplama ifadesi yürütür.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` veya<br /><br />`M<unit> * M<'T> -> M<'T>`|Hesaplama ifadeleri sıralama için çağrılır.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` veya<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|İçin adlı `for...do` hesaplama ifadeleri ifadelerinde.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|İçin adlı `try...finally` hesaplama ifadeleri ifadelerinde.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|İçin adlı `try...with` hesaplama ifadeleri ifadelerinde.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|İçin adlı `use` hesaplama ifadeleri bağlarında.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|İçin adlı `while...do` hesaplama ifadeleri ifadelerinde.|
|`Yield`|`'T -> M<'T>`|İçin adlı `yield` hesaplama ifadeleri ifadelerinde.|
|`YieldFrom`|`M<'T> -> M<'T>`|İçin adlı `yield!` hesaplama ifadeleri ifadelerinde.|
|`Zero`|`unit -> M<'T>`|İçin boş olarak adlandırılan `else` , dallar `if...then` hesaplama ifadeleri ifadelerinde.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Hesaplama deyimine geçirilecek gösterir `Run` üyesi olarak bir teklif. Bu, tüm tırnak içine bir hesaplama örneklerini çevirir.|

Bir oluşturucu sınıftaki yöntemlerin birçoğu kullanın ve dönüş bir `M<'T>` genellikle örneğin birleştirilmeye, hesaplamalar türünü belirtir ayrı olarak tanımlanan bir tür olan yapı `Async<'T>` zaman uyumsuz iş akışları için ve `Seq<'T>` Sıralı iş akışları. Bu yöntem imzalarını birleştirilir ve birbirleri ile iç içe geçmiş kendisine etkinleştirin; böylelikle bir yapı döndürülen iş akışı nesnesinin sonraki geçirilebilir. Derleyici, bir hesaplama ifade ayrıştırırken, yukarıdaki tabloda yöntemleri ve hesaplama ifadesi kodu kullanarak, iç içe geçmiş işlev çağrıları bir dizi ifade dönüştürür.

İç içe geçmiş ifade aşağıdaki şekildedir:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Yukarıdaki kodda, çağrıları `Run` ve `Delay` hesaplama ifadesi Oluşturucu sınıfta tanımlı değil göz ardı edilir. Olarak burada belirtilen hesaplama ifadesi gövdesinin `{| cexpr |}`, aşağıdaki tabloda açıklanan çevirileri tarafından Oluşturucu sınıfının yöntemlerini içeren çağırıyor çevrilir. Hesaplama ifadesi `{| cexpr |}` tanımlı yinelemeli olarak bu çevirileri göre olduğundan burada `expr` olduğu bir F# ifade ve `cexpr` hesaplama ifadesi.

|İfade|Çeviri|
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
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr, builder.Delay({&#124;cexpr &#124;}))</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|

Önceki tabloda `other-expr` tabloda listelenmeyen bir ifade açıklar. Bir oluşturucu sınıf tüm yöntemleri uygulayın ve tüm önceki tabloda listelenen çevirileri destek gerekmez. Uygulanmaz bu yapıları hesaplama türü ifadelerinde kullanılamaz. Örneğin desteklemek istemiyorsanız, `use` anahtar sözcüğü, hesaplama ifadeleri de tanımını çıkarabilirsiniz `Use` Oluşturucu sınıfınızdaki.

Aşağıdaki kod örneği, bir hesaplama olabilecek bir dizi aynı anda tek bir adımda değerlendirilen olarak kapsülleyen bir hesaplama ifadesi gösterir. Bir ayırt edici birleşim türü `OkOrException`, ifade hata durumunu şimdiye değerlendirilen olarak kodlar. Bu kod Oluşturucu yöntemleri bazı ortak uygulamalar gibi hesaplama ifadeleri kullanabileceğiniz birkaç tipik desenleri gösterir.

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

Hesaplama ifadesi ifade döndürür bir temel türü vardır. Temel alınan türü, hesaplanan bir sonuç ya da gerçekleştirilebilir Gecikmeli bir hesaplama gösterebilir veya bazı koleksiyon türü yineleme yapmak için bir yol sağlayabilir. Önceki örnekte, temel türde **sonunda**. Bir sıralama ifadesi için temel türdür <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Bir sorgu ifadesi için temel türdür <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Zaman uyumsuz bir iş akışı için temel türdür [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` Nesne sonucu hesaplamak için gerçekleştirilecek işin temsil eder. Örneğin, çağrı [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) hesaplama çalıştırmak ve sonucu döndürür.

## <a name="custom-operations"></a>Özel işlemler

Hesaplama ifadesi üzerinde özel bir işlemi tanımlar ve bir işleç bir hesaplama ifadesi olarak özel bir işlemi kullanın. Örneğin, bir sorgu ifadesinde bir sorgu işleci içerebilir. Özel bir işlemi tanımlarken Yield tanımlamanız gerekir ve hesaplama ifadesi yöntemleri. Özel bir işlemi tanımlamak için hesaplama ifadesi için bir oluşturucu sınıf koyun ve ardından uygulama [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Bu öznitelik, bir özel işleminde kullanılacak adı olan bir bağımsız değişkeni olarak bir dize alır. Bu ad, açılış kaşlı ayracından hesaplama deyimine başlangıcında kapsama gelir. Bu nedenle, bu bloğunda bir özel işlem olarak aynı ada sahip tanımlayıcılar kullanmamalısınız. Örneğin, tanımlayıcıların gibi kullanmaktan kaçının `all` veya `last` sorgu ifadelerinde.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Mevcut oluşturucular yeni özel işlemleri ile genişletme

Bir oluşturucu sınıf zaten varsa, kendi özel işlemler öğesinden Bu oluşturucu sınıf dışında genişletilebilir. Uzantılar, modüller bildirilmelidir. Ad alanları, aynı dosya ve tür tanımlandığı ad alanı bildirimi grubu dışında uzantı üyeleri içeremez.

Aşağıdaki örnek, varolan uzantısı gösterir `Microsoft.FSharp.Linq.QueryBuilder` sınıfı.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)
- [Diziler](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Sorgu İfadeleri](query-expressions.md)
