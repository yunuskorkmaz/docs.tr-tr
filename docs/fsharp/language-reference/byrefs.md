---
title: Zkratka
description: Byref ve byref-like türleri hakkında F#, alt düzey programlama için kullanılır.
ms.date: 09/02/2018
ms.openlocfilehash: c0bad26672fbb9eb315eee1c3e275183ddeb9297
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055371"
---
# <a name="byrefs"></a>Zkratka

F#düşük düzeydeki programlama alanında baş iki önemli özellik alanlarını sahiptir:

* `byref` / `inref` / `outref` Yönetilen işaretçiler türlerinden. Böylece, çalışma zamanında geçersiz bir program derlenemez kullanım kısıtlamaları sahiptirler.
* A `byref`-olan yapı gibi bir [yapısı](structures.md) benzer semantiğe ve aynı derleme zamanı kısıtlamalara sahip `byref<'T>`. Bir örnek <xref:System.Span%601>.

## <a name="syntax"></a>Sözdizimi

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>ByRef ve inref outref

Üç tür vardır `byref`:

* `inref<'T>`, temeldeki değeri okumak için yönetilen bir işaretçi.
* `outref<'T>`, temel alınan değeri yazmak için yönetilen bir işaretçi.
* `byref<'T>`, temeldeki değer yazma ve okuma için yönetilen bir işaretçi.

A `byref<'T>` nerede geçirilebilir bir `inref<'T>` beklenir. Benzer şekilde, bir `byref<'T>` nerede geçirilebilir bir `outref<'T>` beklenir.

## <a name="using-byrefs"></a>Zkratka kullanma

Kullanılacak bir `inref<'T>`, bir işaretçi değeri ile almanız gereken `&`:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    
let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

İşaretçiyi kullanarak yazmak için bir `outref<'T>` veya `byref<'T>`, almak için bir işaretçi değeri de yapmalısınız `mutable`.

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

İşaretçiyi, okuma yerine yalnızca yazıyorsanız kullanmayı `outref<'T>` yerine `byref<'T>`.

### <a name="inref-semantics"></a>Inref semantiği

Aşağıdaki kodu göz önünde bulundurun:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Anlamsal olarak, bu aşağıdaki gelir:

* Sahibi `x` işaretçi yalnızca kullanabilir, değeri okunamıyor.
* Herhangi bir işaretçi için alınan `struct` iç içe alanlar içinde `SomeStruct` türü verilen `inref<_>`.

Aşağıdakileri de geçerlidir:

* Diğer adlar yazma erişimine sahip değil veya diğer iş parçacıkları çekilmeye yoktur `x`.
* Çekilmeye yoktur, `SomeStruct` tarafından virtue, sabittir `x` olan bir `inref`.

Ancak, F# değer türleri **olan** değişmezse, `this` işaretçi olarak çıkarılan bir `inref`.

Tüm bu kuralların birlikte sahibi anlamına bir `inref` işaretçi işaret edilen bellek hemen içeriğini değiştiremez.

### <a name="outref-semantics"></a>Outref semantiği

Amacı `outref<'T>` işaretçi gelen yalnızca okunmalıdır belirtmektir. Beklenmedik bir şekilde, `outref<'T>` değer adını rağmen temel alınan okuma izin verir. Bu, uyumluluk amacıyla kullanılır. Anlamsal olarak, `outref<'T>` farklı değildir `byref<'T>`.

### <a name="interop-with-c"></a>C ile birlikte çalışma\#

C# destekler `in ref` ve `out ref` yanı sıra anahtar sözcükleri `ref` döndürür. Aşağıdaki tabloda nasıl F# ne yorumlar C# gösterir:

|C# yapısı|F#algılar|
|------------|---------|
|`ref` dönüş değeri|`outref<'T>`|
|`ref readonly` dönüş değeri|`inref<'T>`|
|`in ref` parametre|`inref<'T>`|
|`out ref` parametre|`outref<'T>`|

Aşağıdaki tabloda neler gösterilmektedir F# gösterir:

|F#yapısı|Yayılan yapısı|
|------------|-----------------|
|`inref<'T>` Bağımsız değişken|`[In]` bağımsız değişken özniteliği|
|`inref<'T>` return|`modreq` öznitelik değeri|
|`inref<'T>` soyut yuvası veya uygulama|`modreq` bağımsız değişken veya dönüş|
|`outref<'T>` Bağımsız değişken|`[Out]` bağımsız değişken özniteliği|

### <a name="type-inference-and-overloading-rules"></a>Tür çıkarımı ve kuralları aşırı yükleme

Bir `inref<'T>` türü tarafından çıkarılan F# derleyici aşağıdaki durumlarda:

1. Olan bir .NET parametre veya dönüş türü bir `IsReadOnly` özniteliği.
2. `this` Değişebilir hiçbir alan bir yapı türü işaretçisi.
3. Bir bellek konumunun adresini başka bir türetilmiş `inref<_>` işaretçi.

Örtük bir adres, bir `inref` alınır, bir yükleme türünde bir bağımsız değişken ile `SomeType` türünde bir bağımsız değişken bir aşırı yüklemesi için tercih edilen `inref<SomeType>`. Örneğin:

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

Her iki durumda da alma aşırı `System.DateTime` alma aşırı yerine çözümlendiği `inref<System.DateTime>`.

## <a name="byref-like-structs"></a>ByRef benzeri yapılar

Ek olarak `byref` / `inref` / `outref` sorularının cevabını, uyması için kendi yapılar tanımlayabilirsiniz `byref`-semantiği ister. Bunun <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliği:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` değil gelmez `Struct`. Her ikisi de türünde bulunmalıdır.

Bir "`byref`-gibi" yapıda F# yığın bağlı değer türüdür. Bu, hiçbir zaman yönetilen yığında ayrılır. A `byref`-gibi yaşam süresi ve yakalama olmayan hakkında güçlü denetimleri kümesiyle zorlanmış olarak yapı yüksek performanslı programlama için kullanışlıdır. Kurallar şunlardır:

* İşlev parametrelerini, yöntem parametreleri, yerel değişkenler döner kullanılabilirler.
* Statik olamaz veya bir sınıf ya da normal yapı üyelerinin örneği.
* Herhangi bir kapanış yapısı tarafından yakalanamıyor (`async` yöntemlerde veya lambda ifadelerinde).
* Genel parametre olarak kullanılamaz.

Bu son noktası için çok önemlidir F# ardışık düzen stili programlamada, olarak `|>` giriş türlerinden parametreleştiren genel bir işlevdir. Bu kısıtlama için rahat olmalıdır `|>` gelecekte satır içidir ve satır içi olmayan genel işlev çağrıları, gövdesinde yapmaz.

Bu kurallar çok kesin kullanımını kısıtlıyor olsa da, bunlar promise yüksek performanslı bilgi işlem güvenli bir şekilde karşılamak için bunu yapın.

## <a name="byref-returns"></a>ByRef dönüşleri

ByRef döndüğü F# işlevleri veya üyeleri kullanılabilir üretilen ve tüketilen. Tüketildiğinde bir `byref`-yöntemi döndürmek, örtük olarak başvurusu kaldırılmış bir değerdir. Örneğin:

```fsharp
let safeSum(bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

let sum = safeSum(mySpanOfBytes)
printfn "%d" sum // 'sum' is of type 'int'
```

Zincirleme birden çok çağrı yoluyla bir başvurusu geçirme gibi örtük başvuru önlemek için `&x` (burada `x` değerdir).

Bir geri dönmek de doğrudan atayabilir `byref`. Aşağıdaki (kesinlik temelli yüksek oranda) programı göz önünde bulundurun:

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override __.ToString() = String.Join(' ', nums)

    member __.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

Bu çıktı.

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Zkratka için kapsam belirleme

A `let`-ilişkili değeri, tanımlandığı kapsamı aşıyor, başvuru sahip olamaz. Örneğin, aşağıdaki izin verilmiyor:

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

Bu iyileştirmeler açıp ile derleme yaparsanız bağlı olarak farklı sonuçlar alma engeller.
