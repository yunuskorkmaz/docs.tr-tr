---
title: F# 4,7 F# kılavuzundaki yenilikler
description: 4,7 ' de F# bulunan yeni özelliklere genel bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 203b258466cb9f1f50215ecf8884e92e7e86416b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644070"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="639c1-103">F# 4,7 sürümündeki yenilikler</span><span class="sxs-lookup"><span data-stu-id="639c1-103">What's new in F# 4.7</span></span>

<span data-ttu-id="639c1-104">F#4,7, F# dile birden çok geliştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="639c1-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="639c1-105">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="639c1-105">Get started</span></span>

<span data-ttu-id="639c1-106">F#4,7 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="639c1-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="639c1-107">Daha fazla bilgi edinmek için [ile F# çalışmaya](../get-started/index.md) başlayın.</span><span class="sxs-lookup"><span data-stu-id="639c1-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="639c1-108">Dil sürümü</span><span class="sxs-lookup"><span data-stu-id="639c1-108">Language version</span></span>

<span data-ttu-id="639c1-109">4,7 F# derleyicisi, etkin dil sürümünüzü proje dosyanızdaki bir özellik aracılığıyla ayarlamanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="639c1-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="639c1-110">`4.6`, `4.7`, `latest`ve `preview`değerlerine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="639c1-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="639c1-111">Varsayılan, `latest` değeridir.</span><span class="sxs-lookup"><span data-stu-id="639c1-111">The default is `latest`.</span></span>

<span data-ttu-id="639c1-112">`preview`olarak ayarlarsanız, derleyici, derleyicide uygulanan tüm F# Önizleme özelliklerini etkinleştireceğinize sahip olur.</span><span class="sxs-lookup"><span data-stu-id="639c1-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="639c1-113">Örtük olarak verir</span><span class="sxs-lookup"><span data-stu-id="639c1-113">Implicit yields</span></span>

<span data-ttu-id="639c1-114">Artık türün çıkarsanbileceği diziler, listeler, diziler veya hesaplama ifadelerinde `yield` anahtar sözcüğünü uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="639c1-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="639c1-115">Aşağıdaki örnekte her iki ifade F# 4,7 ' den önceki her giriş için `yield` deyim gerektirir:</span><span class="sxs-lookup"><span data-stu-id="639c1-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

```fsharp
let s = seq { 1; 2; 3; 4; 5 }

let daysOfWeek includeWeekend =
    [ 
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then 
            "Saturday"
            "Sunday"
    ] 
```

<span data-ttu-id="639c1-116">Tek bir `yield` anahtar sözcüğünü tanıtdıysanız, diğer tüm öğeler için de `yield` uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="639c1-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="639c1-117">Örtük olarak, bir diziyi düzleştirmek gibi bir işlem yapmak için `yield!` kullanan bir ifadede kullanıldığında, örtülü olarak, etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="639c1-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="639c1-118">Bu durumlarda `yield` bugün kullanmaya devam etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="639c1-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="639c1-119">Joker karakter tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="639c1-119">Wildcard identifiers</span></span>

<span data-ttu-id="639c1-120">Sınıfları F# içeren kodda, kendi kendine tanımlayıcının üye bildirimlerinde her zaman açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="639c1-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="639c1-121">Ancak, kendi kendine tanımlayıcının hiçbir zaman kullanılmayan durumlarda, genellikle bir ad daha az kendi kendine tanımlayıcı belirtmek için çift alt çizgi kullanma kuralına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="639c1-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="639c1-122">Artık tek bir alt çizgi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="639c1-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="639c1-123">Bu, `for` döngüleri için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="639c1-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="639c1-124">Girintileme</span><span class="sxs-lookup"><span data-stu-id="639c1-124">Indentation relaxations</span></span>

<span data-ttu-id="639c1-125">F# 4,7 ' dan önce, birincil Oluşturucu ve statik üye bağımsız değişkenlerinin girintileme gereksinimleri çok fazla girintileme gerektirdi.</span><span class="sxs-lookup"><span data-stu-id="639c1-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="639c1-126">Artık yalnızca tek bir girintileme kapsamı gerektirir:</span><span class="sxs-lookup"><span data-stu-id="639c1-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
