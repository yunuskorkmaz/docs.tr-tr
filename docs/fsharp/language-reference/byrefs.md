---
title: ByRef’ler
description: 'F # içinde, alt düzey programlama için kullanılan ByRef ve ByRef benzeri türler hakkında bilgi edinin.'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740321"
---
# <a name="byrefs"></a>ByRef’ler

F #, alt düzey programlama alanında ele alan iki önemli özellik alanına sahiptir:

* `byref` / `inref` / `outref` Yönetilen işaretçiler olan türler. Çalışma zamanında geçersiz bir program derleyememesi için kullanım kısıtlamalarına sahiptir.
* `byref`Benzer semantiğe ve aynı derleme zamanı kısıtlamalarına sahip olan bir [Yapı](structures.md) olan, benzeri bir struct `byref<'T>` . Örnek olarak bir örnektir <xref:System.Span%601> .

## <a name="syntax"></a>Syntax

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

Üç biçimi vardır `byref` :

* `inref<'T>`, temel alınan değeri okumak için yönetilen bir işaretçidir.
* `outref<'T>`, temel alınan değere yazmak için yönetilen bir işaretçidir.
* `byref<'T>`, temel alınan değeri okumak ve yazmak için yönetilen bir işaretçidir.

Bir olması `byref<'T>` `inref<'T>` beklendiğinde geçirilebilir. Benzer şekilde, bir `byref<'T>` beklenen yerde bir de geçirilebilir `outref<'T>` .

## <a name="using-byrefs"></a>ByRef 'ler kullanma

Kullanmak için bir `inref<'T>` işaretçi değeri almanız gerekir `&` :

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Bir veya kullanarak işaretçiye yazmak için `outref<'T>` `byref<'T>` bir işaretçi aldığınız değeri de yapmalısınız `mutable` .

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

Yalnızca işaretçiyi okumak yerine yazıyorsanız, yerine kullanmayı göz önünde bulundurun `outref<'T>` `byref<'T>` .

### <a name="inref-semantics"></a>Inref semantiği

Aşağıdaki kodu inceleyin:

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Anlam, bu, aşağıdakiler anlamına gelir:

* `x`İşaretçinin sahibi yalnızca değeri okumak için kullanabilir.
* `struct`İçinde iç içe geçmiş alanlara alınan herhangi bir işaretçiye `SomeStruct` tür verilir `inref<_>` .

Aşağıdakiler de doğrudur:

* Diğer iş parçacıklarının veya diğer adların yazma erişimine sahip olmadığı kesin değildir `x` .
* ' A `SomeStruct` kadar sabit olan bir engel yoktur `x` `inref` .

Ancak **, sabit olan** F # değer türleri için, `this` işaretçi bir olarak algılanır `inref` .

Tüm bu kuralların birlikte bir işaretçi sahibinin, `inref` işaret edilen belleğin hemen içeriğini değiştirebileceğine ilişkin anlamına gelir.

### <a name="outref-semantics"></a>Outref semantiği

Amacı, `outref<'T>` işaretçinin yalnızca üzerine yazılması gerektiğini gösterir. Beklenmedik şekilde, `outref<'T>` ada rağmen temel alınan değerin okunmasına izin verir. Bu uyumluluk amaçlıdır. Anlamsal olarak, `outref<'T>` şundan farklı değildir `byref<'T>` .

### <a name="interop-with-c"></a>C ile birlikte çalışma\#

C#, `in ref` `out ref` dönüşe ek olarak ve anahtar sözcüklerini destekler `ref` . Aşağıdaki tabloda, F # ' ın C# ' ın nasıl yorumlayacağı gösterilmektedir:

|C# yapısı|F # anlar|
|------------|---------|
|`ref` dönüş değeri|`outref<'T>`|
|`ref readonly` dönüş değeri|`inref<'T>`|
|`in ref` parametresinin|`inref<'T>`|
|`out ref` parametresinin|`outref<'T>`|

Aşağıdaki tabloda, hangi F # yayar gösterilmektedir:

|F # yapısı|Yayınlanan Yapı|
|------------|-----------------|
|`inref<'T>` bağımsız değişkeni|`[In]` bağımsız değişkende özniteliği|
|`inref<'T>` döndürülmesini|`modreq` değer üzerinde öznitelik|
|`inref<'T>` Soyut yuva veya uygulamada|`modreq` bağımsız değişkende veya dönüşte|
|`outref<'T>` bağımsız değişkeni|`[Out]` bağımsız değişkende özniteliği|

### <a name="type-inference-and-overloading-rules"></a>Tür çıkarımı ve aşırı yükleme kuralları

Bir `inref<'T>` tür, F # derleyicisi tarafından aşağıdaki durumlarda algılanır:

1. Özniteliği olan bir .NET parametresi veya dönüş türü `IsReadOnly` .
2. `this`Değişebilir alanı olmayan bir struct türündeki işaretçi.
3. Başka bir işaretçiden türetilmiş bellek konumunun adresi `inref<_>` .

Örtük bir adresi `inref` çekilirken, türü bağımsız değişkenine sahip bir aşırı yükleme, `SomeType` türünde bir bağımsız değişkenle bir aşırı yüklemeye tercih edilir `inref<SomeType>` . Örnek:

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

Her iki durumda da, alma aşırı yüklemeler yerine, bu aşırı yüklemeler `System.DateTime` çözümlenmelidir `inref<System.DateTime>` .

## <a name="byref-like-structs"></a>ByRef benzeri yapılar

Trio 'ya ek olarak `byref` / `inref` / `outref` , benzer semantiğe uygun olan kendi yapı birimlerinizi tanımlayabilirsiniz `byref` . Bu, <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> özniteliğiyle yapılır:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` göstermez `Struct` . Her ikisi de türünde bulunmalıdır.

`byref`F # içinde "-LIKE" yapısı, yığın bağlantılı bir değer türüdür. Yönetilen yığında hiçbir şekilde ayrılmadı. Bir `byref` -LIKE yapısı, yoğun ömür ve yakalama olmayan bir güçlü denetim kümesiyle zorlandığından, yüksek performanslı programlama için yararlıdır. Kurallar şunlardır:

* İşlev parametreleri, yöntem parametreleri, yerel değişkenler, yöntem geri dönüş olarak kullanılabilirler.
* Bunlar statik veya bir sınıfın ya da normal yapının örnek üyeleri olamaz.
* Bunlar herhangi bir kapanış yapısı ( `async` Yöntemler veya lambda ifadeleri) tarafından yakalanamaz.
* Genel parametre olarak kullanılamaz.

Bu son nokta, F # ardışık düzen stili programlama için önemlidir. Bu, `|>` giriş türlerini parametreleştiren genel bir işlevdir. Bu kısıtlama `|>` gelecekte, satır içi olduğu için gevşek olabilir ve gövdesinde satır içi olmayan genel işlevlere hiçbir çağrı yapmaz.

Bu kurallar kullanımı kesin olarak kısıtlıyor olsa da, yüksek performanslı bilgi işlem taahhüdünü güvenli bir şekilde yerine getirmek için bu işlemleri yapılır.

## <a name="byref-returns"></a>ByRef dönüşler

F # işlevlerinden ByRef dönüşler veya Üyeler üretilebilir ve tüketilebilir. Bir `byref` döndüren yöntemi kullanırken, değer örtük olarak başvurulduğunu. Örnek:

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
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

Birden çok zincirleme çağrı yoluyla başvuru geçirme gibi örtük başvuruya engel olmak için kullanın `&x` (burada `x` değeri).

Ayrıca, bir dönüşe doğrudan atayabilirsiniz `byref` . Aşağıdaki (son derece kesinlik düzeyi) programı göz önünde bulundurun:

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
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

Bu çıktı.

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>ByRef 'ler için kapsam

Bir `let` -bağlanacak değerin başvurusu tanımlandığı kapsamı aşamaz. Örneğin, aşağıdakilere izin verilmez:

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
