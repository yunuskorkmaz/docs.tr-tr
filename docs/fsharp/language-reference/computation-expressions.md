---
title: Hesaplama İfadeleri
description: "F # ' da, denetim akışı yapıları ve bağlamaları kullanılarak sıralanmış ve birleştirilebilir hesaplamalar yazmak için uygun sözdizimi oluşturmayı öğrenin."
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: 1649d8c57ea9e025d40ef6d39d92b96795964150
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812165"
---
# <a name="computation-expressions"></a>Hesaplama İfadeleri

F # içindeki hesaplama ifadeleri, denetim akışı yapıları ve bağlamaları kullanılarak sıralanmak ve birleştirilebilecek hesaplamalar yazmak için kullanışlı bir sözdizimi sağlar. Hesaplama ifadesinin türüne bağlı olarak, monads, monoıd 'ler, Monad dönüştürücüler ve uygulama ve uygulama bilklerini ifade etmek için bir yol olarak düşünülebilir. Bununla birlikte, diğer dillerden farklı olarak (Haskell içindeki *Do gösterimi* gibi), bunlar tek bir soyutlama 'e bağlı değildir ve kolay ve içeriğe duyarlı bir sözdizimi gerçekleştirmek için makrolara veya diğer meta programlama formlarına güvenmeyin.

## <a name="overview"></a>Genel Bakış

Hesaplamalar birçok form alabilir. En yaygın hesaplama biçimi, anlaşılması ve değiştirilmesi kolay olan tek iş parçacıklı yürütmektir. Ancak, tüm hesaplama biçimleri tek iş parçacıklı yürütme kadar basittir. Bazı örnekler:

- Belirleyici olmayan hesaplamalar
- Zaman uyumsuz hesaplamalar
- Etkili hesaplamalar
- Genel hesaplamalar

Daha genel olarak, bir uygulamanın belirli bölümlerinde gerçekleştirmeniz gereken *bağlama duyarlı* hesaplamalar vardır. Bağlama duyarlı kod yazmak zor olabilir. bu sayede, bu şekilde, belirli bir bağlam dışındaki hesaplamalar, bunu yapmaktan kaçınmak için soyut hale gelir. Bu soyutlamalar genellikle kendi kendinize yazmak zordur. Bu, F # ' ın **Hesaplama ifadeleri**olarak adlandırılan genelleştirilmiş bir yoludur.

Hesaplama ifadeleri, bağlama duyarlı hesaplamaları kodlamak için Tekdüzen bir sözdizimi ve soyutlama modeli sunar.

Her hesaplama ifadesi bir *Oluşturucu* türü tarafından desteklenir. Oluşturucu türü hesaplama ifadesi için kullanılabilir işlemleri tanımlar. Bkz. özel bir hesaplama ifadesinin nasıl oluşturulacağını gösteren [Yeni bir hesaplama Ifadesi türü oluşturma](computation-expressions.md#creating-a-new-type-of-computation-expression).

### <a name="syntax-overview"></a>Sözdizimine genel bakış

Tüm hesaplama ifadeleri aşağıdaki biçimdedir:

```fsharp
builder-expr { cexper }
```

, `builder-expr` Hesaplama ifadesini tanımlayan bir Oluşturucu türünün adıdır ve `cexper` Hesaplama ifadesinin ifade gövdesidir. Örneğin, `async` hesaplama ifade kodu şöyle görünebilir:

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

Bu anahtar sözcüklerin her biri ve diğer standart F # anahtar sözcükleri yalnızca, bir hesaplama ifadesinde, yalnızca bir destek Oluşturucu türünde tanımlıysa kullanılabilir. Bunun tek istisnası, bu, `match!` `let!` sonuç üzerinde bir kalıp eşleşmesi tarafından kullanılması için kendi sözdizimsel cukr.

Oluşturucu türü, hesaplama ifadesinin parçalarının birleştirilme biçimini yöneten özel yöntemleri tanımlayan bir nesnedir; diğer bir deyişle, yöntemi hesaplama ifadesinin nasıl davranacağını denetler. Bir Oluşturucu sınıfını tanımlamanın diğer bir yolu da döngüler ve bağlamalar gibi birçok F # yapıının işlemini özelleştirmenizi sağlar.

### `let!`

`let!`Anahtar sözcüğü bir çağrının sonucunu başka bir hesaplama ifadesine bir ada bağlar:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

İle bir hesaplama ifadesine çağrı bağlarsanız `let` Hesaplama ifadesinin sonucunu elde edersiniz. Bunun yerine, *gerçekleştirilmemiş* çağrının değerini o hesaplama ifadesine bağlacaksınız. `let!`Sonuca bağlamak için kullanın.

`let!` , `Bind(x, f)` Oluşturucu türündeki üye tarafından tanımlanır.

### `do!`

`do!`Anahtar sözcüğü, benzeri tür döndüren bir hesaplama ifadesini çağırmak içindir `unit` ( `Zero` Oluşturucu üzerinde üye tarafından tanımlanır):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

[Zaman uyumsuz iş akışı](asynchronous-workflows.md)için bu tür olur `Async<unit>` . Diğer hesaplama ifadeleri için türün büyük olasılıkla olması olasıdır `CExpType<unit>` .

`do!` , `Bind(x, f)` Oluşturucu türündeki üye tarafından tanımlanır, burada `f` bir oluşturur `unit` .

### `yield`

`yield`Anahtar sözcüğü, bir değer olarak tüketilebilmesi için hesaplama ifadesinden bir değer döndürmektir <xref:System.Collections.Generic.IEnumerable%601> :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Çoğu durumda, çağıranlar tarafından atlanabilir. Atlamak için en yaygın yöntem `yield` `->` işleçtir:

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

[C# ' deki yield anahtar kelimesiyle](../../csharp/language-reference/keywords/yield.md)olduğu gibi, hesaplama ifadesindeki her öğe yinelene kadar geri getirilir.

`yield``Yield(x)`, Oluşturucu türündeki üye tarafından tanımlanır; burada, `x` geri alınacak öğedir.

### `yield!`

`yield!`Anahtar sözcüğü, bir hesaplama ifadesinden bir değer koleksiyonunu düzleştirme için kullanılır:

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

Değerlendirildiğinde, tarafından çağrılan hesaplama ifadesinde `yield!` kendi öğeleri bir tane geri alınır ve bu, sonucu düzleştirme.

`yield!``YieldFrom(x)`, `x` bir değer koleksiyonu olan Oluşturucu türündeki üye tarafından tanımlanır.

Aksine `yield` , `yield!` açıkça belirtilmesi gerekir. Hesaplama ifadelerinde, davranışı örtük değildir.

### `return`

`return`Anahtar sözcüğü, hesaplama ifadesine karşılık gelen türdeki bir değeri sarmalar. Kullanılarak hesaplama ifadelerinden `yield` , bir hesaplama ifadesini "tamamlaması" için kullanılır:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return``Return(x)`, Oluşturucu türündeki üye tarafından tanımlanır; burada, `x` kaydırabileceğiniz öğedir.

### `return!`

`return!`Anahtar sözcüğü bir hesaplama ifadesinin değerini yeniden ayırır ve bu sonucu hesaplama ifadesine karşılık gelen türde kaydırır:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!``ReturnFrom(x)`, Oluşturucu türündeki üye tarafından tanımlanır; burada `x` başka bir hesaplama ifadesi bulunur.

### `match!`

`match!`Anahtar sözcüğü, başka bir hesaplama ifadesine çağrı ve sonuç olarak bir model eşleşmesi sağlar:

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

İle bir hesaplama ifadesi çağrılırken `match!` , bunun gibi çağrının sonucu oluşur `let!` . Bu, genellikle sonucun [isteğe bağlı](options.md)olduğu bir hesaplama ifadesi çağrılırken kullanılır.

## <a name="built-in-computation-expressions"></a>Yerleşik hesaplama ifadeleri

F # Core kitaplığı üç yerleşik hesaplama ifadesi tanımlar: [dizi ifadeleri](sequences.md), [zaman uyumsuz Iş akışları](asynchronous-workflows.md)ve [sorgu ifadeleri](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Yeni bir hesaplama Ifadesi türü oluşturuluyor

Bir Oluşturucu sınıfı oluşturup sınıf üzerinde belirli özel yöntemleri tanımlayarak kendi hesaplama ifadelerinizin özelliklerini tanımlayabilirsiniz. Oluşturucu sınıfı, isteğe bağlı olarak aşağıdaki tabloda listelenen yöntemleri tanımlayabilir.

Aşağıdaki tabloda, bir iş akışı Oluşturucu sınıfında kullanılabilecek yöntemler açıklanmıştır.

|**Yöntem**|**Tipik imza (ler)**|**Açıklama**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|`let!`Hesaplama ifadelerinde ve için çağırılır `do!` .|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Bir hesaplama ifadesini işlev olarak kaydırır.|
|`Return`|`'T -> M<'T>`|`return`Hesaplama ifadelerinde için çağırılır.|
|`ReturnFrom`|`M<'T> -> M<'T>`|`return!`Hesaplama ifadelerinde için çağırılır.|
|`Run`|`M<'T> -> M<'T>` veya<br /><br />`M<'T> -> 'T`|Bir hesaplama ifadesi yürütür.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` veya<br /><br />`M<unit> * M<'T> -> M<'T>`|Hesaplama ifadelerinde sıralama için çağırılır.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` veya<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|`for...do`Hesaplama ifadelerinde ifadeler için çağırılır.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|`try...finally`Hesaplama ifadelerinde ifadeler için çağırılır.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|`try...with`Hesaplama ifadelerinde ifadeler için çağırılır.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|`use`Hesaplama ifadelerinde bağlamalar için çağırılır.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|`while...do`Hesaplama ifadelerinde ifadeler için çağırılır.|
|`Yield`|`'T -> M<'T>`|`yield`Hesaplama ifadelerinde ifadeler için çağırılır.|
|`YieldFrom`|`M<'T> -> M<'T>`|`yield!`Hesaplama ifadelerinde ifadeler için çağırılır.|
|`Zero`|`unit -> M<'T>`|`else`Hesaplama ifadelerinde ifadelerin boş dalları için çağırılır `if...then` .|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Hesaplama ifadesinin `Run` üyeye bir teklif olarak geçtiğini gösterir. Bir hesaplamanın tüm örneklerini bir teklife çevirir.|

Bir Oluşturucu sınıfındaki yöntemlerin birçoğu, `M<'T>` genellikle, örneğin `Async<'T>` zaman uyumsuz iş akışları ve sıra iş akışları için, birleştirilmekte olan hesaplamaların türünü belirleyen ayrı bir tanımlı tür olan bir yapı kullanır ve döndürür `Seq<'T>` . Bu yöntemlerin imzaları, bunların birbirleriyle birlikte birleştirilmelerini ve iç içe aktarılmasını sağlar, böylece bir yapıdan döndürülen iş akışı nesnesinin bir sonrakine geçirilmesi gerekir. Derleyici, bir hesaplama ifadesini ayrıştırdığında, önceki tablodaki yöntemleri ve hesaplama ifadesindeki kodu kullanarak, ifadeyi iç içe geçmiş işlev çağrılarının dizisine dönüştürür.

İç içe geçmiş ifade aşağıdaki biçimdedir:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Yukarıdaki kodda, `Run` ve çağrıları `Delay` Hesaplama ifadesi Oluşturucu sınıfında tanımlanmamışsa atlanır. Burada olarak belirtilen hesaplama ifadesinin gövdesi, `{| cexpr |}` Aşağıdaki tabloda açıklanan Çeviriler tarafından Oluşturucu sınıfının yöntemlerini içeren çağrılara çevrilir. Hesaplama ifadesi `{| cexpr |}` `expr` bir F # ifadesi olduğu ve `cexpr` bir hesaplama ifadesi olduğu bu çevirilerine göre yinelemeli olarak tanımlanır.

|Expression|Çeviri|
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

Önceki tabloda, `other-expr` tabloda başka bir şekilde listelenmeyen bir ifade açıklanmaktadır. Bir Oluşturucu sınıfının tüm yöntemleri uygulaması ve önceki tabloda listelenen tüm çevirileri desteklemesi gerekmez. Uygulanmayan yapılar, bu türün hesaplama ifadelerinde kullanılamaz. Örneğin, `use` Hesaplama ifadelerinizin anahtar sözcüğünü desteklemek istemiyorsanız, `Use` Oluşturucu sınıfınızdaki tanımını atlayabilirsiniz.

Aşağıdaki kod örneği, bir hesaplamayı tek seferde bir adım değerlendirilebilecek bir dizi adım olarak kapsülleyen bir hesaplama ifadesi gösterir. Ayrılmış bir birleşim türü `OkOrException` olan, ifadenin hata durumunu şu ana kadar değerlendirilen şekilde kodluyor. Bu kod, bazı Oluşturucu metotlarının ortak uygulamaları gibi hesaplama ifadelerinizi kullanabileceğiniz birkaç tipik deseni gösterir.

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

Hesaplama ifadesinde, ifadenin döndürdüğü temel bir tür vardır. Temel alınan tür, gerçekleştirilebilecek bir sonucu veya bir Gecikmeli hesaplamayı temsil edebilir veya bazı koleksiyon türleri arasında yineleme yapmak için bir yol sağlayabilir. Önceki örnekte, temel alınan tür **sonunda**. Bir dizi ifadesi için, temel alınan tür olur <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> . Bir sorgu ifadesi için, temel alınan tür olur <xref:System.Linq.IQueryable?displayProperty=nameWithType> . Zaman uyumsuz bir iş akışı için, temel alınan tür olur [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) . `Async`Nesnesi, sonucu hesaplamak için gerçekleştirilecek işi temsil eder. Örneğin, [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) bir hesaplama yürütmek ve sonucu döndürmek için öğesini çağırın.

## <a name="custom-operations"></a>Özel İşlemler

Hesaplama ifadesinde özel bir işlem tanımlayabilir ve bir hesaplama ifadesinde bir işleç olarak özel bir işlem kullanabilirsiniz. Örneğin, sorgu ifadesine bir sorgu işleci ekleyebilirsiniz. Özel bir işlem tanımladığınızda, hesaplama ifadesinde yield ve yöntemleri tanımlamanız gerekir. Özel bir işlem tanımlamak için, bunu hesaplama ifadesi için bir Oluşturucu sınıfına koyun ve ardından öğesini uygulayın [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) . Bu öznitelik bir dizeyi bir özel işlemde kullanılacak olan bir bağımsız değişken olarak alır. Bu ad, hesaplama ifadesinin açma küme ayracı başlangıcında kapsama girer. Bu nedenle, bu bloktaki özel bir işlemle aynı ada sahip tanımlayıcılar kullanmamanız gerekir. Örneğin, `all` sorgu ifadelerinde veya gibi tanımlayıcıların kullanılmasını önleyin `last` .

### <a name="extending-existing-builders-with-new-custom-operations"></a>Mevcut oluşturucuları yeni özel Işlemlerle genişletme

Zaten bir Oluşturucu sınıfınız varsa, özel işlemleri bu Oluşturucu sınıfının dışından genişletilebilir. Uzantılar modüllerde bildirilmelidir. Ad alanları, aynı dosya ve türün tanımlandığı aynı ad alanı bildirim grubu dışında uzantı üyeleri içeremez.

Aşağıdaki örnek, varolan sınıfının uzantısını gösterir `FSharp.Linq.QueryBuilder` .

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
- [Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)
- [Diziler](sequences.md)
- [Sorgu İfadeleri](query-expressions.md)
