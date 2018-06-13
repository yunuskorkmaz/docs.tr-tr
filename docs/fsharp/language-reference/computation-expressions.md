---
title: Hesaplama İfadeleri (F#)
description: "Hesaplamalar F sıralı ve denetim akışı yapıları ve bağlamaları kullanılarak birleştirilen #'de yazma için uygun sözdizimini oluşturmayı öğrenin."
ms.date: 05/16/2016
ms.openlocfilehash: a4ddb3fde284452bc901c5270551611e43742c1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566619"
---
# <a name="computation-expressions"></a>Hesaplama İfadeleri

F # hesaplama ifadeleri sıralı ve denetim akışı yapıları ve bağlamaları kullanılarak birleştirilen hesaplamalar yazmak için uygun bir sözdizimi sağlar. İçin kullanışlı bir söz dizimi sağlamak için kullanılabilir *monads*, verileri, Denetim ve işlevsel programlarda yan etkileri yönetmek için kullanılan bir işlev programlama özelliği.


## <a name="built-in-workflows"></a>Yerleşik iş akışları
Sequence ifadeleri bir zaman uyumsuz iş akışları ve sorgu ifadeleri gibi bir hesaplama ifadesi örnektir. Daha fazla bilgi için bkz: [sıraları](sequences.md), [zaman uyumsuz iş akışları](asynchronous-workflows.md), ve [sorgu ifadeleri](query-expressions.md).

Belirli özellikler sequence ifadeleri ve zaman uyumsuz iş akışları için ortaktır ve hesaplama ifadesi temel sözdizimi gösterilmektedir:

```fsharp
builder-name { expression }
```

Önceki sözdizimi verilen ifade hesaplama ifadesi tarafından belirtilen bir türdeki belirtir *Oluşturucu adını*. Hesaplama ifadesi gibi yerleşik bir iş akışı olabilir `seq` veya `async`, ya da tanımladığınız bir şey olabilir. *Oluşturucu adını* olarak bilinen özel bir türünün bir örneği tanımlayıcısıdır *Oluşturucu türüyle*. Oluşturucusu türü nasıl ifade yürütür denetleyen hesaplama ifadesi parçasının, diğer bir deyişle, kod birleştirilen biçimini yöneten özel yöntemler tanımlayan bir sınıf türüdür. Oluşturucu sınıfı açıklamak için başka bir, döngüler ve bağlamaları gibi birçok F # yapıları, işlem özelleştirmenizi sağlar söylemek için yoludur.

Hesaplama ifadeleri iki tür bazı ortak dil yapıları için kullanılabilir. Değişken yapıları kullanarak çağırabileceği bir! (bang) belirli anahtar sözcükleri gibi soneki `let!`, `do!`ve benzeri. Bu özel formlar bu işlemlerin normal yerleşik davranışını değiştirmek için oluşturucu sınıfında tanımlanan belirli işlevleri neden. Bu formlar benzer `yield!` biçiminde `yield` dizisi ifadelerinde kullanılan anahtar sözcük. Daha fazla bilgi için bkz: [sıraları](sequences.md).


## <a name="creating-a-new-type-of-computation-expression"></a>Yeni bir hesaplama ifadesi türü oluşturma
Oluşturucu sınıfı oluşturarak ve sınıf üzerinde belirli özel yöntemlerini tanımlama kendi hesaplama ifadeleri özelliklerini tanımlayabilirsiniz. Oluşturucu sınıfı, isteğe bağlı olarak aşağıdaki tabloda listelendiği gibi yöntemleri tanımlayabilirsiniz.

Aşağıdaki tabloda, bir iş akışı Oluşturucu sınıfta kullanılabilir yöntemleri açıklar.


|**Yöntemi**|**Tipik imza**|**Açıklama**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|İçin adlı `let!` ve `do!` hesaplama ifadelerde.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Hesaplama ifadesi bir işlevi olarak sarmalar.|
|`Return`|`'T -> M<'T>`|İçin adlı `return` hesaplama ifadelerde.|
|`ReturnFrom`|`M<'T> -> M<'T>`|İçin adlı `return!` hesaplama ifadelerde.|
|`Run`|`M<'T> -> M<'T>` Veya<br /><br />`M<'T> -> 'T`|Hesaplama ifadesi yürütür.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` Veya<br /><br />`M<unit> * M<'T> -> M<'T>`|Hesaplama ifadeleri sıralaması için çağrılır.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` Veya<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|İçin adlı `for...do` hesaplama ifadeleri ifadelerinde.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|İçin adlı `try...finally` hesaplama ifadeleri ifadelerinde.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|İçin adlı `try...with` hesaplama ifadeleri ifadelerinde.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|İçin adlı `use` hesaplama ifadeleri bağlama.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|İçin adlı `while...do` hesaplama ifadeleri ifadelerinde.|
|`Yield`|`'T -> M<'T>`|İçin adlı `yield` hesaplama ifadeleri ifadelerinde.|
|`YieldFrom`|`M<'T> -> M<'T>`|İçin adlı `yield!` hesaplama ifadeleri ifadelerinde.|
|`Zero`|`unit -> M<'T>`|İçin boş adlı `else` , dallandırır `if...then` hesaplama ifadeleri ifadelerinde.|
Birçok Oluşturucu sınıftaki yöntemlerin kullanın ve dönüş bir `M<'T>` genellikle birleştirilen, hesaplamalar tür örneğin belirtir ayrı olarak tanımlanan bir tür olduğundan, yapı `Async<'T>` zaman uyumsuz iş akışları için ve `Seq<'T>` Sıralı iş akışları. Böylece bir yapı döndürülen iş akışı nesnesi sonraki geçirilebilir bu yöntemleri imzalarını birleştirilmiş ve birbirleri ile iç içe geçmiş için etkinleştirin. Hesaplama ifadesi ayrıştırırken derleyici, yukarıdaki tabloda yöntemlere ve hesaplama ifadesi kodu kullanarak, bir dizi iç içe geçmiş işlev çağrısı ifade dönüştürür.

İç içe geçmiş ifade aşağıdaki şekildedir:

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Yukarıdaki kodda, çağrıları `Run` ve `Delay` hesaplama ifadesi Oluşturucu sınıfında tanımlanmazsa göz ardı edilir. Burada olarak gösterilen hesaplama ifadesi gövdesini `{| cexpr |}`, oluşturucu sınıfının yöntemlerini içeren çağrıları aşağıdaki tabloda açıklanan çevirileri tarafından çevrilir. Hesaplama ifadesi `{| cexpr |}` bu çevirileri göre tanımlanan yinelemeli olarak eşleştirilir nerede `expr` F # ifade olan ve `cexpr` hesaplama ifadesi.



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
|<code>{&#124; while expr do cexpr &#124;}</code>|<code>builder.While(fun () -> expr), builder.Delay({&#124;cexpr &#124;})</code>|
|<code>{&#124; try cexpr with &#124; pattern_i -> expr_i &#124;}</code>|<code>builder.TryWith(builder.Delay({&#124; cexpr &#124;}), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{&#124; try cexpr finally expr &#124;}</code>|<code>builder.TryFinally(builder.Delay( {&#124; cexpr &#124;}), (fun () -> expr))</code>|
|<code>{&#124; cexpr1; cexpr2 &#124;}</code>|<code>builder.Combine({&#124;cexpr1 &#124;}, {&#124; cexpr2 &#124;})</code>|
|<code>{&#124; other-expr; cexpr &#124;}</code>|<code>expr; {&#124; cexpr &#124;}</code>|
|<code>{&#124; other-expr &#124;}</code>|`expr; builder.Zero()`|
Önceki tabloda `other-expr` Aksi takdirde tabloda listelenmeyen bir ifade açıklar. Oluşturucu sınıfı, tüm yöntemleri uygulamak ve tüm önceki tabloda listelenen çevirileri desteklemek gerekmez. Uygulanmamıştır bu yapıları hesaplama türü ifadelerinde kullanılamaz. Örneğin desteklemek istemiyorsanız `use` hesaplama ifadeleri anahtar sözcük, tanımını atlamak `Use` Oluşturucu sınıfınızda.

Aşağıdaki kod örneği, bir dizi olabilir adımı aynı anda tek bir adımda hesaplanan olarak bir hesaplama yalıtan bir hesaplama ifadesi gösterilir. Bir birleşim türü, ayrılmış `OkOrException`, ifade hata durumunu kadarki hesaplanan olarak kodlar. Bu kodu Oluşturucu yöntemlerin bazıları Demirbaş uygulamaları gibi hesaplama ifadeleri kullanabileceğiniz birkaç tipik desenleri gösterir.

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

Bir hesaplama ifadesi ifade döndürür bir temel türe sahip. Temel alınan tür gerçekleştirilebilir Gecikmeli bir hesaplama veya hesaplanan bir sonucu gösterebilir veya bazı tür bir koleksiyon yineleme yolunu sağlayabilir. Önceki örnekte, temel alınan tür idi **sonunda**. Bir sıra ifadesi için temel türdür <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Bir sorgu ifadesi için temel türdür <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Asychronous iş akışı için temel türdür [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). `Async` Nesnesi sonucu hesaplamak için gerçekleştirilecek iş temsil eder. Örneğin, [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) bir hesaplama çalıştırmak ve sonucu döndürür.

## <a name="custom-operations"></a>Özel işlemler
Hesaplama ifadesi üzerinde özel bir işlemi tanımlamak ve bir işleç bir hesaplama ifadesinde olarak özel bir işlemi kullanın. Örneğin, sorgu ifadesinde bir sorgu işleci içerebilir. Özel bir işlemi tanımladığınızda, verim tanımlamanız gerekir ve hesaplama ifadesi yöntemleri için. Özel bir işlemi tanımlamak için hesaplama ifadesi Oluşturucu sınıfında koyabilir ve ardından uygulama [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Bu öznitelik, bir özel işleminde kullanılacak adı bir bağımsız değişken olarak bir dize alır. Bu ad büyük ayracını hesaplama ifadesi başlangıcında kapsam içine gelir. Bu nedenle, bu bloğa özel bir işlemi ile aynı ada sahip tanımlayıcıları kullanmamalısınız. Örneğin, tanımlayıcılar gibi kullanmaktan kaçının `all` veya `last` sorgu ifadelerinde.

## <a name="see-also"></a>Ayrıca Bkz.
[F# Dili Başvurusu](index.md)

[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)

[Diziler](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)

[Sorgu İfadeleri](query-expressions.md)
