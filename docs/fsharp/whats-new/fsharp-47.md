---
title: F# 4.7 'deki yenilikler - F# Kılavuzu
description: F# 4.7'de bulunan yeni özelliklere genel bir bakış alın.
ms.date: 11/27/2019
ms.openlocfilehash: 7a6e744a398719bcb55d168dd700459e0b122dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185870"
---
# <a name="whats-new-in-f-47"></a><span data-ttu-id="6b483-103">F# 4.7'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="6b483-103">What's new in F# 4.7</span></span>

<span data-ttu-id="6b483-104">F# 4.7, F# diline birden fazla iyileştirme ekler.</span><span class="sxs-lookup"><span data-stu-id="6b483-104">F# 4.7 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="6b483-105">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="6b483-105">Get started</span></span>

<span data-ttu-id="6b483-106">F# 4.7 tüm .NET Core dağıtımlarında ve Visual Studio araçlamalarında mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="6b483-106">F# 4.7 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="6b483-107">Daha fazla bilgi edinmek için [F# ile başlayın.](../get-started/index.md)</span><span class="sxs-lookup"><span data-stu-id="6b483-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="language-version"></a><span data-ttu-id="6b483-108">Dil sürümü</span><span class="sxs-lookup"><span data-stu-id="6b483-108">Language version</span></span>

<span data-ttu-id="6b483-109">F# 4.7 derleyicisi, etkili dil sürümünüzü proje dosyanızdaki bir özellik üzerinden ayarlama olanağını sunar:</span><span class="sxs-lookup"><span data-stu-id="6b483-109">The F# 4.7 compiler introduces the ability to set your effective language version via a property in your project file:</span></span>

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="6b483-110">Değerleri `4.6`, , , `4.7` `latest`ve `preview`.</span><span class="sxs-lookup"><span data-stu-id="6b483-110">You can set it to the values `4.6`, `4.7`, `latest`, and `preview`.</span></span> <span data-ttu-id="6b483-111">Varsayılan değer: `latest`.</span><span class="sxs-lookup"><span data-stu-id="6b483-111">The default is `latest`.</span></span>

<span data-ttu-id="6b483-112">Eğer `preview`ayarlarsanız, derleyiciniz derleyicinizde uygulanan tüm F# önizleme özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="6b483-112">If you set it to `preview`, your compiler will activate all F# preview features that are implemented in your compiler.</span></span>

## <a name="implicit-yields"></a><span data-ttu-id="6b483-113">Örtük verimler</span><span class="sxs-lookup"><span data-stu-id="6b483-113">Implicit yields</span></span>

<span data-ttu-id="6b483-114">Artık anahtar kelimeyi, `yield` türün çıkarılabildiği dizilerde, listelerde, dizilerde veya hesaplama ifadelerinde uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6b483-114">You no longer need to apply the `yield` keyword in arrays, lists, sequences, or computation expressions where the type can be inferred.</span></span> <span data-ttu-id="6b483-115">Aşağıdaki örnekte, her iki `yield` ifade f# 4.7 önce her giriş için deyimi gerekli:</span><span class="sxs-lookup"><span data-stu-id="6b483-115">In the following example, both expressions required the `yield` statement for each entry prior to F# 4.7:</span></span>

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

<span data-ttu-id="6b483-116">Tek `yield` bir anahtar kelime tanıtıyorsanız, `yield` diğer tüm öğede de uygulanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b483-116">If you introduce a single `yield` keyword, every other item must also have `yield` applied to it.</span></span>

<span data-ttu-id="6b483-117">Örtük verimler, bir diziyi düzleştirmek `yield!` gibi bir şey yapmak için de kullanan bir ifadede kullanıldığında etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="6b483-117">Implicit yields are not activated when used in an expression that also uses `yield!` to do something like flatten a sequence.</span></span> <span data-ttu-id="6b483-118">Bu gibi durumlarda `yield` bugün kullanmaya devam etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6b483-118">You must continue to use `yield` today in these cases.</span></span>

## <a name="wildcard-identifiers"></a><span data-ttu-id="6b483-119">Joker karakter tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="6b483-119">Wildcard identifiers</span></span>

<span data-ttu-id="6b483-120">Sınıfları içeren F# kodunda, öz tanımlayıcının üye bildirimlerinde her zaman açık olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b483-120">In F# code involving classes, the self-identifier needs to always be explicit in member declarations.</span></span> <span data-ttu-id="6b483-121">Ancak kendini tanımlayıcının hiç kullanılmadığı durumlarda, isimsiz bir öz tanımlayıcıyı belirtmek için bir çift alt çizgi kullanmak geleneksel olarak bir gelenektir.</span><span class="sxs-lookup"><span data-stu-id="6b483-121">But in cases where the self-identifier is never used, it has traditionally been convention to use a double-underscore to indicate a nameless self-identifiers.</span></span> <span data-ttu-id="6b483-122">Artık tek bir alt alt alt puan kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6b483-122">You can now use a single underscore:</span></span>

```fsharp
type C() =
    member _.M() = ()
```

<span data-ttu-id="6b483-123">Bu döngüler `for` için de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="6b483-123">This also applies for `for` loops:</span></span>

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a><span data-ttu-id="6b483-124">Girintisi gevşemeleri</span><span class="sxs-lookup"><span data-stu-id="6b483-124">Indentation relaxations</span></span>

<span data-ttu-id="6b483-125">F# 4.7'den önce, birincil oluşturucu ve statik üye bağımsız değişkenler için girinti gereksinimleri aşırı girinti gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="6b483-125">Prior to F# 4.7, the indentation requirements for primary constructor and static member arguments required excessive indentation.</span></span> <span data-ttu-id="6b483-126">Artık yalnızca tek bir girintin kapsamı gerektirir:</span><span class="sxs-lookup"><span data-stu-id="6b483-126">They now only require a single indentation scope:</span></span>

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
