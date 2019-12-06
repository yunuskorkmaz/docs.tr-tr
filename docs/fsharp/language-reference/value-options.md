---
title: Değer Seçenekleri
description: Seçenek türünün bir F# struct sürümü olan değer seçenek türü hakkında bilgi edinin.
ms.date: 12/04/2019
ms.openlocfilehash: 0e9882ab4acdf2757705ef6022516d3572d87ef2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837122"
---
# <a name="value-options"></a>Değer Seçenekleri

' Deki F# değer seçenek türü, aşağıdaki iki koşul ayrı olduğunda kullanılır:

1. Bir senaryo, bir [ F# seçenek](options.md)için uygundur.
2. Yapı kullanımı, senaryonuza bir performans avantajı sağlar.

Tüm performans duyarlı senaryolar yapılar kullanılarak "çözülür". Başvuru türleri yerine bunları kullanırken, kopyalamanın ek maliyetini göz önünde bulundurmanız gerekir. Ancak, büyük F# programlar genellikle dinamik yollardan akan birçok isteğe bağlı türü oluşturur ve bu gibi durumlarda, yapılar genellikle programın kullanım ömrü boyunca daha iyi genel performans elde edebilir.

## <a name="definition"></a>Tanım

Değer seçeneği, başvuru seçenek türüne benzer bir [struct ayrılmış birleşim](discriminated-unions.md#struct-discriminated-unions) olarak tanımlanır. Tanımı şu şekilde düşünülebilir:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

Değer seçeneği yapısal eşitlik ve karşılaştırmaya uyar. Ana fark, derlenmiş ad, tür adı ve büyük/küçük harf adlarının tümü bir değer türü olduğunu gösterir.

## <a name="using-value-options"></a>Değer seçeneklerini kullanma

Değer seçenekleri tıpkı [Seçenekler](options.md)gibi kullanılır. `ValueSome`, bir değerin mevcut olduğunu göstermek için kullanılır ve bir değer mevcut olmadığında `ValueNone` kullanılır:

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

[Seçeneklerde](options.md)olduğu gibi, `ValueOption` döndüren bir işlevin adlandırma kuralı, `try`önek olarak önektir.

## <a name="value-option-properties-and-methods"></a>Değer seçeneği özellikleri ve yöntemleri

Şu anda değer seçenekleri için bir özellik var: `Value`. Bu özellik çağrıldığında hiçbir değer yoksa <xref:System.InvalidOperationException> tetiklenir.

## <a name="value-option-functions"></a>Değer seçeneği işlevleri

FSharp. Core 'daki `ValueOption` modülü, `Option` modülüne denk işlevsellik içerir. Adında birkaç fark vardır, örneğin `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

Bu, `Option` modülündeki `defaultArg` gibi davranır, ancak bunun yerine bir değer seçeneği üzerinde çalışır.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler](options.md)
