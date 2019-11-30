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
# <a name="whats-new-in-f-47"></a>F# 4,7 sürümündeki yenilikler

F#4,7, F# dile birden çok geliştirme ekler.

## <a name="get-started"></a>Kullanmaya başlayın

F#4,7 tüm .NET Core dağıtımları ve Visual Studio Araçları 'nda kullanılabilir. Daha fazla bilgi edinmek için [ile F# çalışmaya](../get-started/index.md) başlayın.

## <a name="language-version"></a>Dil sürümü

4,7 F# derleyicisi, etkin dil sürümünüzü proje dosyanızdaki bir özellik aracılığıyla ayarlamanıza olanak sağlar:

```xml
<PropertyGroup>
    <LangVersion>preview</LangVersion>
</PropertyGroup>
```

`4.6`, `4.7`, `latest`ve `preview`değerlerine ayarlayabilirsiniz. Varsayılan, `latest` değeridir.

`preview`olarak ayarlarsanız, derleyici, derleyicide uygulanan tüm F# Önizleme özelliklerini etkinleştireceğinize sahip olur.

## <a name="implicit-yields"></a>Örtük olarak verir

Artık türün çıkarsanbileceği diziler, listeler, diziler veya hesaplama ifadelerinde `yield` anahtar sözcüğünü uygulamanız gerekmez. Aşağıdaki örnekte her iki ifade F# 4,7 ' den önceki her giriş için `yield` deyim gerektirir:

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

Tek bir `yield` anahtar sözcüğünü tanıtdıysanız, diğer tüm öğeler için de `yield` uygulanmış olması gerekir.

Örtük olarak, bir diziyi düzleştirmek gibi bir işlem yapmak için `yield!` kullanan bir ifadede kullanıldığında, örtülü olarak, etkin değildir. Bu durumlarda `yield` bugün kullanmaya devam etmeniz gerekir.

## <a name="wildcard-identifiers"></a>Joker karakter tanımlayıcıları

Sınıfları F# içeren kodda, kendi kendine tanımlayıcının üye bildirimlerinde her zaman açık olması gerekir. Ancak, kendi kendine tanımlayıcının hiçbir zaman kullanılmayan durumlarda, genellikle bir ad daha az kendi kendine tanımlayıcı belirtmek için çift alt çizgi kullanma kuralına sahiptir. Artık tek bir alt çizgi kullanabilirsiniz:

```fsharp
type C() =
    member _.M() = ()
```

Bu, `for` döngüleri için de geçerlidir:

```fsharp
for _ in 1..10 do printfn "Hello!"
```

## <a name="indentation-relaxations"></a>Girintileme

F# 4,7 ' dan önce, birincil Oluşturucu ve statik üye bağımsız değişkenlerinin girintileme gereksinimleri çok fazla girintileme gerektirdi. Artık yalnızca tek bir girintileme kapsamı gerektirir:

```fsharp
type OffsideCheck(a:int,
    b:int, c:int,
    d:int) = class end

type C() =
    static member M(a:int,
        b:int, c:int,
        d:int) = 1
```
