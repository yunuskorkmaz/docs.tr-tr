---
title: ByRef’ler
description: İçindeki F#ByRef ve ByRef benzeri türler hakkında bilgi edinin ve bu, alt düzey programlama için kullanılır.
ms.date: 11/04/2019
ms.openlocfilehash: 2d98d325dc4ad26548fb2cc6aa5b872e152ee0a8
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092794"
---
# <a name="byrefs"></a>ByRef’ler

F#, alt düzey programlama alanında ele alan iki önemli özellik alanına sahiptir:

* `byref`/`inref`yönetilen işaretçiler olan /`outref` türler. Çalışma zamanında geçersiz bir program derleyememesi için kullanım kısıtlamalarına sahiptir.
* Benzer semantiğini ve `byref<'T>`aynı derleme zamanı kısıtlamalarını [içeren `byref`benzeri bir yapı](structures.md) . Bir örnek <xref:System.Span%601>.

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

## <a name="byref-inref-and-outref"></a>ByRef, ınref ve outref

Üç `byref`biçimi vardır:

* temel alınan değeri okumak için yönetilen bir işaretçi `inref<'T>`.
* temel alınan değere yazmak için yönetilen bir işaretçi olan `outref<'T>`.
* temel alınan değeri okumak ve yazmak için yönetilen bir işaretçi olan `byref<'T>`.

Bir `inref<'T>` beklendiğinde `byref<'T>` geçirilebilir. Benzer şekilde, bir `outref<'T>` beklenildiği bir `byref<'T>` geçirilebilir.

## <a name="using-byrefs"></a>ByRef 'ler kullanma

`inref<'T>`kullanmak için, `&`bir işaretçi değeri almanız gerekir:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

`outref<'T>` veya `byref<'T>`kullanarak işaretçiye yazmak için, `mutable`işaretçiyi aldığınız değeri de yapmalısınız.

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

Yalnızca işaretçiyi okumak yerine yazıyorsanız, `byref<'T>`yerine `outref<'T>` kullanmayı göz önünde bulundurun.

### <a name="inref-semantics"></a>Inref semantiği

Aşağıdaki kodu göz önünde bulundurun:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Anlam, bu, aşağıdakiler anlamına gelir:

* `x` işaretçisinin sahibi yalnızca değeri okumak için kullanabilir.
* `SomeStruct` içinde iç içe `struct` alanlara alınan herhangi bir işaretçiye `inref<_>`türü verilir.

Aşağıdakiler de doğrudur:

* Diğer iş parçacıklarının veya diğer adların `x`için yazma erişimine sahip olmadığı kesin değildir.
* `SomeStruct` `inref``x` sanallaştırılan bir sorun yoktur.

Ancak, sabit F# olan değer türleri için `this` işaretçisi bir `inref`olarak algılanır.

Tüm bu kuralların birlikte bir `inref` işaretçisinin sahibi, işaret edilen belleğin hemen içeriğini değiştiremeyebilir.

### <a name="outref-semantics"></a>Outref semantiği

`outref<'T>` amacı, işaretçinin yalnızca yazılması gerektiğini gösterir. Beklenmedik şekilde, `outref<'T>` ada rağmen temel alınan değerin okunmasına izin verir. Bu uyumluluk amaçlıdır. Anlamsal, `outref<'T>` `byref<'T>`farklı değildir.

### <a name="interop-with-c"></a>C\# ile birlikte çalışma

C#`ref` dönüşe ek olarak `in ref` ve `out ref` anahtar sözcüklerini destekler. Aşağıdaki tabloda, ne F# C# kadar yorumlama yapılacağı gösterilmektedir:

|C#oluşturma|F#algılar|
|------------|---------|
|`ref` dönüş değeri|`outref<'T>`|
|`ref readonly` dönüş değeri|`inref<'T>`|
|`in ref` parametresi|`inref<'T>`|
|`out ref` parametresi|`outref<'T>`|

Aşağıdaki tabloda neler F# olduğu gösterilmektedir:

|F#oluşturma|Yayınlanan Yapı|
|------------|-----------------|
|`inref<'T>` bağımsız değişkeni|bağımsız değişkende `[In]` özniteliği|
|`inref<'T>` dön|değer üzerinde `modreq` özniteliği|
|Soyut yuva veya uygulamada `inref<'T>`|bağımsız değişkende veya dönüşte `modreq`|
|`outref<'T>` bağımsız değişkeni|bağımsız değişkende `[Out]` özniteliği|

### <a name="type-inference-and-overloading-rules"></a>Tür çıkarımı ve aşırı yükleme kuralları

Aşağıdaki durumlarda F# derleyici tarafından bir `inref<'T>` türü algılanır:

1. Bir `IsReadOnly` özniteliği olan bir .NET parametresi veya dönüş türü.
2. `this` işaretçisi, değişebilir alanları olmayan bir struct türü üzerinde.
3. Başka bir `inref<_>` işaretçisinden türetilen bir bellek konumunun adresi.

`inref` örtük bir adresi çekilirken, `inref<SomeType>`türünde bir bağımsız değişkenle birlikte `SomeType` türünde bağımsız değişkene sahip bir aşırı yükleme tercih edilir. Örneğin:

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

Her iki durumda da, `inref<System.DateTime>`alan aşırı yüklemeler yerine `System.DateTime` alan aşırı yüklemeler çözümlenir.

## <a name="byref-like-structs"></a>ByRef benzeri yapılar

`byref`/`inref`/`outref` Trio 'ya ek olarak, `byref`benzer anlamlarına uygun olan kendi yapı birimlerinizi tanımlayabilirsiniz. Bu, <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliğiyle yapılır:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` `Struct`göstermez. Her ikisi de türünde bulunmalıdır.

İçindeki F# "`byref`-LIKE" yapısı, yığın bağlantılı bir değer türüdür. Yönetilen yığında hiçbir şekilde ayrılmadı. `byref`benzeri bir yapı, yoğun ömür ve yakalama olmayan bir dizi güçlü denetim ile zorlandığından, yüksek performanslı programlama için yararlıdır. Kurallar şunlardır:

* İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem geri dönüş olarak kullanılabilirler.
* Bunlar statik veya bir sınıfın ya da normal yapının örnek üyeleri olamaz.
* Bunlar herhangi bir kapanış yapısı (`async` Yöntemler veya lambda ifadeleri) tarafından yakalanamaz.
* Genel parametre olarak kullanılamaz.

Bu son nokta, işlem hattı F# stili programlama için önemlidir. `|>`, giriş türlerini parametreleştiren genel bir işlevdir. Bu kısıtlama, gelecekte `|>` için gevşek olabilir ve gövdesinde satır içi olmayan genel işlevlere hiçbir çağrı yapmaz.

Bu kurallar kullanımı kesin olarak kısıtlıyor olsa da, yüksek performanslı bilgi işlem taahhüdünü güvenli bir şekilde yerine getirmek için bu işlemleri yapılır.

## <a name="byref-returns"></a>ByRef dönüşler

ByRef, F# işlevlerden veya üyelerin üretilebilir ve tüketilebilmesi için kullanılır. `byref`döndüren bir yöntemi kullanırken, değer örtük olarak başvurulduğunu. Örneğin:

```fsharp
let squareAndPrint (data : byref<int>) = 
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

ByRef değeri döndürmek için değeri içeren değişken geçerli kapsamdan daha uzun bir süre etkin olmalıdır.
Ayrıca, ByRef döndürmek için `&value` (değeri geçerli kapsamdan daha uzun süre bulunan bir değişkendir) kullanın.

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Birden çok zincirleme çağrı yoluyla başvuru geçirme gibi örtük başvuru yapmaktan kaçınmak için `&x` (`x` değerdir) kullanın.

Ayrıca, bir dönüş `byref`doğrudan atayabilirsiniz. Aşağıdaki (son derece kesinlik düzeyi) programı göz önünde bulundurun:

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
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

## <a name="scoping-for-byrefs"></a>ByRef 'ler için kapsam

`let`ilişkili bir değerin başvurusu tanımlandığı kapsamı aşamaz. Örneğin, aşağıdakilere izin verilmez:

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

Bu, iyileştirmelere göre derlemenize bağlı olarak farklı sonuçlar almanızı önler.
