---
title: F# 4,5 F# kılavuzundaki yenilikler
description: 4,5 ' de F# bulunan yeni özelliklere genel bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 780b33a564432aae5ec99c70ff8620988b553fd1
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644112"
---
# <a name="whats-new-in-f-45"></a>F# 4,5 sürümündeki yenilikler

F#4,5, F# dile birden çok geliştirme ekler. Bu özelliklerin birçoğu, içinde F# verimli kod yazmanızı sağlamak için birlikte eklenmiştir ve ayrıca bu kodun güvende olmasını sağlar. Bunun yapılması, bu yapılar kullanılırken dile birkaç kavram ve önemli miktarda derleyici analizini ekleme anlamına gelir.

## <a name="get-started"></a>Kullanmaya başlayın

F#4,5 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda kullanılabilir. Daha fazla bilgi edinmek için [ile F# çalışmaya](../get-started/index.md) başlayın.

## <a name="span-and-byref-like-structs"></a>Span ve ByRef benzeri yapılar

.NET Core 'da tanıtılan <xref:System.Span%601> türü, bellek içi arabellekleri kesin belirlenmiş bir şekilde temsil etmenize olanak tanır. buna artık 4,5 ile F# F# başlayarak izin verilir. Aşağıdaki örnek, farklı arabellek gösterimlerine sahip bir <xref:System.Span%601> çalışan bir işlevi nasıl yeniden kullanabileceğinizi gösterir:

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do 
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

Bunun önemli bir yönü, yayılma ve diğer [ByRef benzeri yapıların](../language-reference/structures.md#byreflike-structs) , kullanımlarını beklenmedik şekilde bulacağınız yöntemlerle sınırlayan, derleyicinin gerçekleştirdiği çok rigıd statik analizine sahip olmasını sağlar. Bu, performans, ifade ve 4,5 ' de F# tanıtılan güvenlik arasındaki temel zorunluluğunu getirir.

## <a name="revamped-byrefs"></a>Revaed ByRef 'ler

4,5 ' den önce, içindeki F# [byrefs](../language-reference/byrefs.md) güvenli değil ve çok sayıda uygulama için ses geri alındı. F# 4,5 ' de F# ve ayrıca, span ve ByRef benzeri yapılar için yapılan aynı statik analizler, ByRef 'ler etrafında elde edilen sorunları ele alındı.

### <a name="inreft-and-outreft"></a>ınref < 'T > ve outref < 'T >

Salt okunurdur, salt yazılır ve okuma/yazma yönetilen işaretçisinin kavramını göstermek için F# 4,5, sırasıyla salt okunurdur ve salt yazılır işaretçileri temsil edecek `inref<'T>``outref<'T>` türlerini tanıtır. Her birinin farklı anlamları vardır. Örneğin, bir `inref<'T>`yazılamaz:

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Varsayılan olarak, tür çıkarımı, zaten değişebilir olarak bildirilmemiş olmadığı sürece, yönetilen işaretçileri `inref<'T>` sabit F# koda göre satır içinde olacak şekilde çıkarmış olur. Bir şeyi yazılabilir yapmak için, adresini onu işleyen bir işleve veya üyeye geçirmeden önce `mutable` olarak bir tür bildirmeniz gerekir. Daha fazla bilgi için bkz. [Byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>ReadOnly yapılar

4,5 ' F# den başlayarak, <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> bir yapısına şu şekilde açıklama ekleyebilirsiniz:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Bu, yapıda kesilebilir üye bildirmesinin yanı sıra bir derlemeden tüketilirken onu ReadOnly olarak F# ele C# almasına izin veren meta verileri yayar. Daha fazla bilgi için bkz. [ReadOnly yapılar](../language-reference/structures.md#readonly-structs)

## <a name="void-pointers"></a>Void işaretçileri

`voidptr` türü, aşağıdaki işlevlerde olduğu F# gibi 4,5 ' e eklenir:

* void işaretçiyi yerel bir int işaretçisine dönüştürmek için `NativePtr.ofVoidPtr`
* Yerel bir int işaretçisini void işaretçiye dönüştürmek için `NativePtr.toVoidPtr`

Bu, void işaretçilerin kullanıldığı bir yerel bileşenle birlikte çalışırken yararlıdır.

## <a name="the-match-keyword"></a>`match!` anahtar sözcüğü

`match!` anahtar sözcüğü, bir hesaplama ifadesi içindeyken model eşleştirmeyi geliştirir:

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }
    
// Now you can use 'match!'
let funcWithString (s: string) =
    async { 
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

Bu, genellikle zaman uyumsuz gibi hesaplama ifadelerle seçenekleri (veya diğer türleri) kapsayan kodu kısaltmaya olanak tanır. Daha fazla bilgi için bkz. [Match!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Dizi, liste ve dizi ifadelerinde gevşek yukarı atama gereksinimleri

Dizi, liste ve dizi ifadelerinin içinden bir diğerinden kalıtımla albileceği türler, herhangi bir türetilmiş türü `:>` veya `upcast`ile üst türüne yukarı dönüştürmeyi gerektirir. Bu, aşağıda gösterildiği gibi gevşek bir şekilde yapılır:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Dizi ve liste ifadeleri için girinti ayırma

F# 4,5 ' dan önce, yöntem çağrılarına bağımsız değişken olarak geçirildiğinde dizi ve liste ifadelerini aşırı girintilendirmek gerekir. Bu artık gerekli değildir:

```fsharp
module NoExcessiveIndenting = 
    System.Console.WriteLine(format="{0}", arg = [| 
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
