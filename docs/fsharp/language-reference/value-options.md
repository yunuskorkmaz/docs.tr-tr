---
title: Değer Seçenekleri
description: Seçenek türünün bir F# struct sürümü olan değer seçenek türü hakkında bilgi edinin.
ms.date: 02/06/2019
ms.openlocfilehash: 4dc3f7217943345b7aaf1165fd648ab2e01bd727
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424015"
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

Şu anda değer seçenekleri için bir modüle bağlı işlev var, `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

`defaultArg` işlevinde olduğu gibi `defaultValueArg`, varsa verilen değer seçeneğinin temel alınan değerini döndürür; Aksi halde, belirtilen varsayılan değeri döndürür.

Şu anda değer seçenekleri için modüle özgü başka işlevler yoktur.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler](options.md)
