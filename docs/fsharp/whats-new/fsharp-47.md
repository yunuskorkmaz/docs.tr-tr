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
# <a name="whats-new-in-f-47"></a>F# 4.7'deki yenilikler

F# 4.7, F# diline birden fazla iyileştirme ekler.

## <a name="get-started"></a>Kullanmaya başlayın

F# 4.7 tüm .NET Core dağıtımlarında ve Visual Studio araçlamalarında mevcuttur. Daha fazla bilgi edinmek için [F# ile başlayın.](../get-started/index.md)

## <a name="language-version"></a>Dil sürümü

F# 4.7 derleyicisi, etkili dil sürümünüzü proje dosyanızdaki bir özellik üzerinden ayarlama olanağını sunar:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Değerleri `4.6`, , , `4.7` `latest`ve `preview`. Varsayılan değer: `latest`.

Eğer `preview`ayarlarsanız, derleyiciniz derleyicinizde uygulanan tüm F# önizleme özelliklerini etkinleştirir.

## <a name="implicit-yields"></a>Örtük verimler

Artık anahtar kelimeyi, `yield` türün çıkarılabildiği dizilerde, listelerde, dizilerde veya hesaplama ifadelerinde uygulamanız gerekmez. Aşağıdaki örnekte, her iki `yield` ifade f# 4.7 önce her giriş için deyimi gerekli:

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

Tek `yield` bir anahtar kelime tanıtıyorsanız, `yield` diğer tüm öğede de uygulanmış olması gerekir.

Örtük verimler, bir diziyi düzleştirmek `yield!` gibi bir şey yapmak için de kullanan bir ifadede kullanıldığında etkinleştirilmez. Bu gibi durumlarda `yield` bugün kullanmaya devam etmelisiniz.

## <a name="wildcard-identifiers"></a>Joker karakter tanımlayıcıları

Sınıfları içeren F# kodunda, öz tanımlayıcının üye bildirimlerinde her zaman açık olması gerekir. Ancak kendini tanımlayıcının hiç kullanılmadığı durumlarda, isimsiz bir öz tanımlayıcıyı belirtmek için bir çift alt çizgi kullanmak geleneksel olarak bir gelenektir. Artık tek bir alt alt alt puan kullanabilirsiniz:

```fsharp
type C() =
    member _.M() = ()
```

Bu döngüler `for` için de geçerlidir:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Girintisi gevşemeleri

F# 4.7'den önce, birincil oluşturucu ve statik üye bağımsız değişkenler için girinti gereksinimleri aşırı girinti gerektiriyor. Artık yalnızca tek bir girintin kapsamı gerektirir:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
