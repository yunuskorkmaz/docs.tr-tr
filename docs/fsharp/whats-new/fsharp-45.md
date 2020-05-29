---
title: 'F # 4,5-F # kılavuzundaki yenilikler'
description: "F # 4,5 ' de bulunan yeni özelliklere genel bakış alın."
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202359"
---
# <a name="whats-new-in-f-45"></a>F # 4,5 ' deki yenilikler

F # 4,5, F # diline birden çok geliştirme ekler. Bu özelliklerin birçoğu, F # ' ta verimli kod yazmanızı sağlamak için birlikte eklenmiştir ve ayrıca bu kodun güvenli olmasını sağlar. Bunun yapılması, bu yapılar kullanılırken dile birkaç kavram ve önemli miktarda derleyici analizini ekleme anlamına gelir.

## <a name="get-started"></a>başlarken

F # 4,5 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda mevcuttur. Daha fazla bilgi edinmek için [F # ile çalışmaya](../get-started/index.md) başlayın.

## <a name="span-and-byref-like-structs"></a>Span ve ByRef benzeri yapılar

<xref:System.Span%601>.NET Core 'da tanıtılan tür, artık f # 4,5 ile başlayan f # ' da izin verilen kesin olarak belirlenmiş bir şekilde bellekteki arabellekleri temsil etmenize olanak tanır. Aşağıdaki örnek, <xref:System.Span%601> farklı arabellek temsilleri ile bir üzerinde çalışan bir işlevi nasıl yeniden kullanabileceğinizi gösterir:

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

Bunun önemli bir yönü, yayılma ve diğer [ByRef benzeri yapıların](../language-reference/structures.md#byreflike-structs) , kullanımlarını beklenmedik şekilde bulacağınız yöntemlerle sınırlayan, derleyicinin gerçekleştirdiği çok rigıd statik analizine sahip olmasını sağlar. Bu, F # 4,5 ' de sunulan performans, ifade ve güvenlik arasındaki temel zorunluluğunu getirir.

## <a name="revamped-byrefs"></a>Revaed ByRef 'ler

F # 4,5 ' den önce, F # ' ta [Byrefs](../language-reference/byrefs.md) güvenli değildi ve çok sayıda uygulama için ses geri alındı. F # 4,5 ' de ve ayrıca, span ve ByRef benzeri yapılar için yapılan aynı statik analizler de, ByRef 'ler etrafında ses sorunları ele alındı.

### <a name="inreft-and-outreft"></a>ınref< 'T> ve outref< 'T>

Salt okunurdur, salt yazılır ve okuma/yazma yönetilen işaretçisinin kavramını göstermek için F # 4,5, `inref<'T>` `outref<'T>` sırasıyla salt okunurdur ve salt yazılır işaretçileri temsil edecek olan türleri tanıtır. Her birinin farklı anlamları vardır. Örneğin, bir öğesine yazamaz `inref<'T>` :

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Varsayılan olarak, tür çıkarımı, `inref<'T>` zaten değişebilir olarak bildirilmemiş olmadığı sürece, yönetilen işaretçileri gerçek F # kodu ile satır içinde olacak şekilde çıkarmış olur. Bir şeyi yazılabilir yapmak için, `mutable` adresini onu işleyen bir işleve veya üyeye geçirmeden önce bir tür bildirmeniz gerekir. Daha fazla bilgi için bkz. [Byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>ReadOnly yapılar

F # 4,5 ile başlayarak, bir yapısına şu şekilde açıklama ekleyebilirsiniz <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> :

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Bu, yapıda kesilebilir üye bildirmesinin yanı sıra F # ve C# ' nin bir derlemeden tüketilirken onu ReadOnly olarak görmesini sağlayan meta verileri yayar. Daha fazla bilgi için bkz. [ReadOnly yapılar](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Void işaretçileri

`voidptr`Türü, aşağıdaki işlevlerde olduğu gibi F # 4,5 ' a eklenir:

* `NativePtr.ofVoidPtr`void işaretçiyi yerel bir int işaretçisine dönüştürmek için
* `NativePtr.toVoidPtr`Yerel bir int işaretçisini void işaretçiye dönüştürmek için

Bu, void işaretçilerin kullanıldığı bir yerel bileşenle birlikte çalışırken yararlıdır.

## <a name="the-match-keyword"></a>`match!` anahtar sözcüğü

`match!`Anahtar sözcüğü, bir hesaplama ifadesi içindeyken model eşleştirmeyi geliştirir:

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

Dizi, liste ve sıra ifadeleri içindeki başka bir diğerinin devraldığı türlerin karıştırma, genellikle türetilmiş herhangi bir türü ya da ile üst türüne yukarı atama yapmak için gereklidir `:>` `upcast` . Bu, aşağıda gösterildiği gibi gevşek bir şekilde yapılır:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Dizi ve liste ifadeleri için girinti ayırma

F # 4,5 ' den önce, yöntem çağrılarına bağımsız değişken olarak geçirildiğinde dizi ve liste ifadelerini aşırı girintilendirmek gerekir. Bu artık gerekli değildir:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
