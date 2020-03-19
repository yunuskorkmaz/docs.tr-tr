---
title: ByRef’ler
description: Düşük seviyeli programlama için kullanılan F#'daki byref ve byref benzeri türleri hakkında bilgi edinin.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187047"
---
# <a name="byrefs"></a>ByRef’ler

F# düşük düzeyprogramlama alanında anlaşma iki ana özellik alanları vardır:

* `byref` / Yönetilen `inref` / işaretçiler olan `outref` türler. Çalışma zamanında geçersiz olan bir programı derleyemiyorsanız, kullanımla ilgili kısıtlamaları vardır.
* Benzer `byref`semantik ve aynı derleme zamanı kısıtlamaları olan bir [yapıdır](structures.md) `byref<'T>`- struct gibi . Bir <xref:System.Span%601>örnek.

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

## <a name="byref-inref-and-outref"></a>Byref, inref ve outref

Üç şekli `byref`vardır:

* `inref<'T>`, temel değeri okumak için yönetilen bir işaretçi.
* `outref<'T>`, temel değere yazmak için yönetilen bir işaretçi.
* `byref<'T>`, temel değeri okumak ve yazmak için yönetilen bir işaretçi.

Bir `byref<'T>` beklenen yerde `inref<'T>` geçirilebilir. Benzer şekilde, `byref<'T>` bir beklenen `outref<'T>` yerde geçirilebilir.

## <a name="using-byrefs"></a>Byrefs kullanma

Bir , `inref<'T>`bir işaretçi değeri almak `&`için gereken bir kullanmak için:

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Bir `outref<'T>` veya `byref<'T>`kullanarak işaretçiye yazmak için `mutable`, ayrıca bir işaretçi kapmak değeri yapmak gerekir.

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

İşaretçiyi okumak yerine yalnızca yazıyorsanız, `outref<'T>` 'yi `byref<'T>`yerine kullanmayı düşünün.

### <a name="inref-semantics"></a>İnref semantik

Aşağıdaki kodu inceleyin:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Semantically, bu aşağıdaki anlamına gelir:

* `x` İşaretçinin sahibi yalnızca değeri okumak için kullanabilir.
* İç `struct` `SomeStruct` içe yuvalanmış alanlara edinilen `inref<_>`işaretçilere tür verilir.

Aşağıdaki ler de doğrudur:

* Diğer iş parçacıklarının veya diğer adların `x`yazma erişiminin olmadığı ima edilmez.
* Bir `SomeStruct` `x` varlık nedeniyle değişmez bir ima `inref`yoktur.

Ancak, **değişmez** olan F# değer türleri `this` için işaretçi . `inref`

Tüm bu kurallar birlikte, bir `inref` işaretçinin sahibinin işaret edilen belleğin hemen içeriğini değiştiremeyeceği anlamına gelir.

### <a name="outref-semantics"></a>Outref semantik

`outref<'T>` Amaç, işaretçinin yalnızca yazılması gerektiğini belirtmektir. Beklenmedik bir `outref<'T>` şekilde, adından da aynı sıcanda temel değeri okumaya izin verir. Bu uyumluluk amaçlıdır. Semantik olarak, `outref<'T>` farklı `byref<'T>`değil.

### <a name="interop-with-c"></a>C ile Interop\#

C# ve `in ref` `out ref` anahtar kelimeleri destekler, döner ek `ref` olarak. Aşağıdaki tablo, F#'ın C#'ın ne yaksalar yayıştırdığını nasıl yorumladığını gösterir:

|C# yapı|F# çıkarımları|
|------------|---------|
|`ref`iade değeri|`outref<'T>`|
|`ref readonly`iade değeri|`inref<'T>`|
|`in ref`Parametre|`inref<'T>`|
|`out ref`Parametre|`outref<'T>`|

Aşağıdaki tablo, F#'nın ne yaksalar yayıştırolduğunu gösterir:

|F# yapısı|Yayılan yapı|
|------------|-----------------|
|`inref<'T>` bağımsız değişkeni|`[In]`bağımsız değişkene öznitelik|
|`inref<'T>`Dönüş|`modreq`değere öznitelik|
|`inref<'T>`soyut yuva veya uygulamada|`modreq`bağımsız değişken veya dönüş|
|`outref<'T>` bağımsız değişkeni|`[Out]`bağımsız değişkene öznitelik|

### <a name="type-inference-and-overloading-rules"></a>Tür çıkarım ve aşırı yükleme kuralları

Bir `inref<'T>` tür aşağıdaki durumlarda F# derleyicisi tarafından çıkarılır:

1. `IsReadOnly` Bir .NET parametresi veya özniteliği olan iade türü.
2. Mutable alanları olmayan bir yapı türündeki `this` işaretçi.
3. Başka `inref<_>` bir işaretçiden türetilen bellek konumunun adresi.

Bir `inref` örtük adres alınırken, türü `SomeType` bağımsız değişkeni olan aşırı yük, türünden `inref<SomeType>`bir bağımsız değişkeniçeren aşırı yüke tercih edilir. Örnek:

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

Her iki durumda da, `System.DateTime` aşırı yüklemeler alma `inref<System.DateTime>`yerine çözülür.

## <a name="byref-like-structs"></a>Byref benzeri structs

`byref` / `inref` Üçlüye / ek olarak, semantik gibi lere uyabilen `byref`kendi yapılarınızı tanımlayabilirsiniz. `outref` Bu öznitelik <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> ile yapılır:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`anlamına `Struct`gelmez. Her ikisi de türünde mevcut olmalıdır.

F#'daki "-like"`byref`struct, yığına bağlı bir değer türüdür. Yönetilen yığına hiçbir zaman ayrılmaz. Bir `byref`-benzeri yapı, yaşam boyu ve yakalamama ile ilgili güçlü denetimler kümesiyle uygulandığından, yüksek performanslı programlama için yararlıdır. Kurallar şunlardır:

* İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem döndürürler olarak kullanılabilirler.
* Bunlar statik veya bir sınıfın veya normal yapının örnek üyeleri olamaz.
* Herhangi bir kapatma yapısı (yöntemler`async` veya lambda ifadeleri) tarafından ele geçirilemezler.
* Genel bir parametre olarak kullanılamazlar.

Bu son nokta, giriş türlerini parametreize `|>` eden genel bir işlev olduğu gibi F# ardışık ardışık programlama için çok önemlidir. Bu kısıtlama gelecekte `|>` için rahat olabilir, çünkü satır içi dir ve gövdesinde çizgisiz genel işlevlere herhangi bir çağrı yapmaz.

Bu kurallar kullanımı güçlü bir şekilde kısıtlasa da, bunu yüksek performanslı bilgi işlem sözünü güvenli bir şekilde yerine getirmek için yapar.

## <a name="byref-returns"></a>Byref döndürür

Byref F# işlevlerinden döner veya üye üretilebilir ve tüketilebilir. `byref`-returning yöntemi tüketirken, değer örtülü olarak dereferenced. Örnek:

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

Bir değer byref döndürmek için, değeri içeren değişkenin geçerli kapsamdan daha uzun yaşaması gerekir.
Ayrıca, byref dönmek `&value` için, kullanın (değer geçerli kapsamdaha uzun yaşayan bir değişkendir).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Birden çok zincirleme arama yoluyla bir başvuru nun geçirilmesi `&x` gibi `x` örtük dereference'ı önlemek için kullanın (değer nerededir).

Ayrıca doğrudan bir dönüş `byref`atayabilirsiniz. Aşağıdaki (son derece zorunlu) programı göz önünde bulundurun:

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

## <a name="scoping-for-byrefs"></a>Byrefs için kapsam

Bağlı `let`bir değer, referansını tanımlandığı kapsamı aşamaz. Örneğin, aşağıdakiler izin verilmez:

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

Bu, optimizasyonlarla derlep girmediğinize bağlı olarak farklı sonuçlar elde etmenizi önler.
