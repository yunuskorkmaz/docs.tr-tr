---
title: Değer seçenekleri
description: Hakkında bilgi edinin F# seçenek türünün bir yapı sürümü seçeneği değer türü.
ms.date: 02/06/2019
ms.openlocfilehash: e1036c83189c853b3704d94ca245e4818acc98c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982585"
---
# <a name="value-options"></a>Değer seçenekleri

Değer seçenek türünde F# aşağıdaki iki koşul tuttuğunuzda kullanılır:

1. Bir senaryo için uygun olan bir [ F# seçeneği](options.md).
2. Bir yapı kullanarak sizin senaryonuzda bu performans artar.

Tüm performans açısından duyarlı senaryoları "yapılar kullanarak çözülen". Bunları başvuru türleri yerine kullanırken kopyalama ek maliyeti dikkate almanız gerekir. Ancak, büyük F# programlar etkin yolları akış birçok isteğe bağlı türler genellikle örneği ve böyle durumlarda yapılar genellikle bir program ömrü boyunca daha iyi toplam performans sağlayabilir.

## <a name="definition"></a>Tanım

Değer seçeneği olarak tanımlanmış olan bir [ayırt edici birleşim](discriminated-unions.md#struct-discriminated-unions) olan başvuru seçeneği türüne benzerdir. Tanımı şöyle düşünülebilir:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

Değer seçeneği yapısal eşitlik ve karşılaştırma için uygundur. İkisi arasındaki temel fark, derlenmiş ad, tür adı ve büyük/küçük harf adları, bir değer türü olduğunu belirtmek ' dir.

## <a name="using-value-options"></a>Değer seçeneklerini kullanma

Değer seçenekleri gibi kullanılır [seçenekleri](options.md). `ValueSome` bir değerin mevcut olduğunu belirtmek için kullanılır ve `ValueNone` bir değer mevcut olmadığında kullanılır:

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

Olduğu gibi [seçenekleri](options.md), döndüren bir işlev için adlandırma kuralı `ValueOption` ile ön ek için `try`.

## <a name="value-option-properties-and-methods"></a>Değer seçeneği özellikleri ve yöntemleri

Şu anda bir özellik için değer seçenekleri mevcuttur: `Value`. Bir <xref:System.InvalidOperationException> hiçbir değer yoksa, bu özelliğin çağırılır olması durumunda tetiklenir.

## <a name="value-option-functions"></a>Değer seçeneği işlevleri

Şu anda bir modül bağlı işlev değer seçenekleri için olan `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

Olduğu gibi `defaultArg` işlevi `defaultValueArg` belirli değer seçeneği temel değerini döndürür var; Aksi takdirde, varsayılan değeri döndürür.

Şu anda hiç bir modül bağlı işlevi değer seçenekleri için vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler](options.md)
