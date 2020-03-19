---
title: F# 4.5 -F# Kılavuzu'ndaki yenilikler
description: F# 4.5'te bulunan yeni özelliklere genel bir bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186129"
---
# <a name="whats-new-in-f-45"></a>F# 4.5'teki yenilikler

F# 4.5, F# diline birden fazla iyileştirme ekler. Bu özelliklerin çoğu, f# ile verimli kod yazmanızı sağlarken aynı zamanda bu kodun güvenli olmasını sağlamak için bir araya getirildi. Bunu yapmak, bu yapıları kullanırken dile birkaç kavram ve önemli miktarda derleyici çözümlemesi eklemek anlamına gelir.

## <a name="get-started"></a>Kullanmaya başlayın

F# 4.5 tüm .NET Core dağıtımlarında ve Visual Studio araçlamalarında mevcuttur. Daha fazla bilgi edinmek için [F# ile başlayın.](../get-started/index.md)

## <a name="span-and-byref-like-structs"></a>Span ve byref benzeri structs

.NET Core'da tanıtılan <xref:System.Span%601> tür, bellekteki arabellekleri güçlü bir şekilde temsil etmenizi sağlar ve f# 4.5 ile başlayarak F# ile izin verilir. Aşağıdaki örnek, farklı arabellek gösterimleri <xref:System.Span%601> ile çalışan bir işlevi nasıl yeniden kullanabileceğinizi gösterir:

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

Bunun önemli bir yönü, Span ve diğer [byref benzeri structs](../language-reference/structures.md#byreflike-structs) beklenmeyen bulabileceğiniz şekillerde kullanımlarını kısıtlayan derleyici tarafından gerçekleştirilen çok katı statik analiz olmasıdır. Bu, F# 4.5'te sunulan performans, ifade ve güvenlik arasındaki temel dengedir.

## <a name="revamped-byrefs"></a>Yenilenen byrefs

F# 4.5'den önce, F# [byrefs](../language-reference/byrefs.md) güvensiz ve çok sayıda uygulama için sağlıksız edildi. Byrefs etrafında sağlamlık sorunları F # 4.5 ele alınmıştır ve span ve byref benzeri structs için yapılan aynı statik analiz de uygulanmıştır.

### <a name="inreft-and-outreft"></a>inref<'T> ve outref<'T>

Yalnızca okuma, yalnızca yazma ve okuma/yazma yönetilen işaretçisi kavramını temsil etmek için, F# 4.5 sırasıyla salt okunur ve yalnızca yazma işaretçilerini temsil etmek için `inref<'T>`, türleri `outref<'T>` tanıtır. Her birinin farklı anlambilimi var. Örneğin, bir `inref<'T>`yazamazsınız:

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Varsayılan olarak, bir şey zaten değişken olarak `inref<'T>` bildirilmedikçe, tür çıkarım, F# kodunun değişmez yapısına uygun olarak yönetilen işaretçilerçıkaracaktır. Bir şeyi yazılabilir hale getirmek için, bir `mutable` türü, adresini onu manipüle eden bir işleve veya üyeye geçirmeden önce olduğu gibi bildirmeniz gerekir. Daha fazla bilgi için [Byrefs'](../language-reference/byrefs.md)e bakın.

## <a name="readonly-structs"></a>Yalnızca okuma structs

F# 4.5 ile başlayarak, bir yapıya şu <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> şekilde açıklama ekleyebilirsiniz:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

Bu, yapıda mutable bir üye ilan etmenizi sağlar ve F# ve C# bir derleme tüketilen zaman okunmuş olarak tedavi etmek için izin meta veri yakar. Daha fazla bilgi için [readOnly structs'a](../language-reference/structures.md#readonly-structs)bakın.

## <a name="void-pointers"></a>Geçersiz işaretçiler

F# 4.5'e `voidptr` aşağıdaki işlevler gibi türü eklenir:

* `NativePtr.ofVoidPtr`geçersiz bir işaretçiyi yerel int işaretçisine dönüştürmek için
* `NativePtr.toVoidPtr`bir int işaretçisini geçersiz bir işaretçiye dönüştürmek için

Bu, geçersiz işaretçileri kullanan yerel bir bileşenle çalışırken yararlıdır.

## <a name="the-match-keyword"></a>`match!` anahtar sözcüğü

Anahtar `match!` kelime, bir hesaplama ifadesinin içindeyken desen eşleştirmesini geliştirir:

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

Bu, genellikle karıştırma seçeneklerini (veya diğer türleri) async gibi hesaplama ifadeleriyle içeren kodu kısaltmanızı sağlar. Daha fazla bilgi için, [maç bakın!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Dizi, liste ve sıra lı ifadelerde rahat upcasting gereksinimleri

Bir dizi, liste ve dizi ifadeleri içinde başka bir devralabilir karıştırma türleri geleneksel olarak kendi üst `:>` türüne `upcast`veya . Bu şimdi rahat, aşağıdaki gibi gösterilmiştir:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Dizi ve liste ifadeleri için girintinasyon gevşemesi

F# 4.5'den önce, yöntem çağrılarına bağımsız değişken olarak geçtiğinde aşırı girintisli dizi ve liste ifadeleri gerekiyordu. Bu artık gerekli değildir:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
