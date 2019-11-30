---
title: F# 4,6 F# kılavuzundaki yenilikler
description: 4,6 ' de F# bulunan yeni özelliklere genel bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 81d3e988d044cb16f8ec079118fd0ede2dabc587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644084"
---
# <a name="whats-new-in-f-46"></a>F# 4,6 sürümündeki yenilikler

F#4,6, F# dile birden çok geliştirme ekler.

## <a name="get-started"></a>Kullanmaya başlayın

F#4,6 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda kullanılabilir. Daha fazla bilgi edinmek için [ile F# çalışmaya](../get-started/index.md) başlayın.

## <a name="anonymous-records"></a>Anonim kayıtlar

[Anonim kayıtlar](../language-reference/anonymous-records.md) 4,6 ' de F# tanıtılan yeni F# tür türüdür. Kullanılmadan önce bildirilmesini gerektirmeyen adlandırılmış değerlerin basit toplamaları vardır. Bunları yapılar veya başvuru türleri olarak bildirebilirsiniz. Bunlar varsayılan olarak başvuru türlerdir.

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Ayrıca, değer türlerini gruplandırmak istediğiniz ve performansa duyarlı senaryolarda çalışırken, için yapı olarak da bildirilemez:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Bunlar oldukça güçlüdür ve çok sayıda senaryoda kullanılabilir. [Anonim kayıtlar](../language-reference/anonymous-records.md)hakkında daha fazla bilgi edinin.

## <a name="valueoption-functions"></a>ValueOption işlevleri

4,5 ' de F# eklenen valueoption türüne artık seçenek türü ile "modüle göre bağlantılı işlev eşliği" vardır. Daha yaygın olarak kullanılan birkaç örnek aşağıda verilmiştir:

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> None
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> Some

let reversedString = strOpt |> Option.bind reverse
```

Bu, ValueOption 'in bir değer türünün performansı artırdığı senaryolarda yalnızca LIKE seçeneğinin kullanılmasını sağlar.
