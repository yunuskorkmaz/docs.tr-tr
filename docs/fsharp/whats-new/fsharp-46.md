---
title: F# 4,6 F# kılavuzundaki yenilikler
description: 4,6 ' de F# bulunan yeni özelliklere genel bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 620c1edd8ea212fee306a02d5844b6b322808251
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980398"
---
# <a name="whats-new-in-f-46"></a><span data-ttu-id="89c04-103">F# 4,6 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="89c04-103">What's new in F# 4.6</span></span>

<span data-ttu-id="89c04-104">F#4,6, F# dile birden çok geliştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="89c04-104">F# 4.6 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="89c04-105">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="89c04-105">Get started</span></span>

<span data-ttu-id="89c04-106">F#4,6 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89c04-106">F# 4.6 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="89c04-107">Daha fazla bilgi edinmek için [ile F# çalışmaya](../get-started/index.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="89c04-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="anonymous-records"></a><span data-ttu-id="89c04-108">Anonim kayıtlar</span><span class="sxs-lookup"><span data-stu-id="89c04-108">Anonymous records</span></span>

<span data-ttu-id="89c04-109">[Anonim kayıtlar](../language-reference/anonymous-records.md) 4,6 ' de F# tanıtılan yeni F# tür türüdür.</span><span class="sxs-lookup"><span data-stu-id="89c04-109">[Anonymous records](../language-reference/anonymous-records.md) are a new kind of F# type introduced in F# 4.6.</span></span> <span data-ttu-id="89c04-110">Kullanılmadan önce bildirilmesini gerektirmeyen adlandırılmış değerlerin basit toplamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="89c04-110">They are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="89c04-111">Bunları yapılar veya başvuru türleri olarak bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89c04-111">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="89c04-112">Bunlar varsayılan olarak başvuru türlerdir.</span><span class="sxs-lookup"><span data-stu-id="89c04-112">They're reference types by default.</span></span>

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

<span data-ttu-id="89c04-113">Ayrıca, değer türlerini gruplandırmak istediğiniz ve performansa duyarlı senaryolarda çalışırken, için yapı olarak da bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="89c04-113">They can also be declared as structs for when you want to group value types and are operating in performance-sensitive scenarios:</span></span>

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

<span data-ttu-id="89c04-114">Bunlar oldukça güçlüdür ve çok sayıda senaryoda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="89c04-114">They're quite powerful and can be used in numerous scenarios.</span></span> <span data-ttu-id="89c04-115">[Anonim kayıtlar](../language-reference/anonymous-records.md)hakkında daha fazla bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="89c04-115">Learn more at [Anonymous records](../language-reference/anonymous-records.md).</span></span>

## <a name="valueoption-functions"></a><span data-ttu-id="89c04-116">ValueOption işlevleri</span><span class="sxs-lookup"><span data-stu-id="89c04-116">ValueOption functions</span></span>

<span data-ttu-id="89c04-117">4,5 ' de F# eklenen valueoption türüne artık seçenek türü ile "modüle göre bağlantılı işlev eşliği" vardır.</span><span class="sxs-lookup"><span data-stu-id="89c04-117">The ValueOption type added in F# 4.5 now has "module-bound function parity" with the Option type.</span></span> <span data-ttu-id="89c04-118">Daha yaygın olarak kullanılan birkaç örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="89c04-118">Some of the more commonly-used examples are as follows:</span></span>

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> ValueNone
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> ValueSome

let reversedString = strOpt |> ValueOption.bind reverse
```

<span data-ttu-id="89c04-119">Bu, ValueOption 'in bir değer türünün performansı artırdığı senaryolarda yalnızca LIKE seçeneğinin kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="89c04-119">This allows for ValueOption to be used just like Option in scenarios where having a value type improves performance.</span></span>
