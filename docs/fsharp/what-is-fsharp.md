---
title: NedirF#
description: Hakkında bilgi edinin F# programlama dilinde olduğu ve neler F# programlama benzer. Zengin veri türleri, İşlevler ve bunlar birbirine nasıl uyduğunu hakkında bilgi edinin.
ms.date: 08/03/2018
ms.openlocfilehash: ea82147e4e6d3c980fb224eeafd805c7ed53f8f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756344"
---
# <a name="what-is-f"></a>F nedir\#

F#doğru ve sürdürülebilir kod yazmayı kolaylaştıran bir işlevsel programlama dilidir.

F#öncelikle programlama, türler ve tür çıkarımı yapılan ve otomatik olarak genelleştirilmiş işlevleri tanımlama içerir. Bu, odağınızı sorun etki alanı ve programlama ayrıntılarını yerine verilerini düzenleme kalmasına izin verir.

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

F#dahil olmak üzere çok sayıda özelliğe sahiptir:

* Basit sözdizimi
* Varsayılan olarak sabit
* Tür çıkarımı ve otomatik Genelleştirme
* Birinci sınıf İşlevler
* Güçlü veri türleri
* Desen eşleştirme
* Zaman uyumsuz programlama

Tam bir özellikler kümesi belgelenir [ F# dil başvurusu](language-reference/index.md).

## <a name="rich-data-types"></a>Zengin veri türleri

Veri türleri gibi [kayıtları](language-reference/records.md) ve [ayırt edici birleşimler](language-reference/discriminated-unions.md) , karmaşık verileri ve etki alanları temsil eden olanak tanır.

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F#kayıtlar ve ayrılmış birleşimler, null olmayan, sabit ve kullanımı çok kolay hale getirme varsayılan olarak karşılaştırılabilir.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>İşlevler ve desen eşleştirme ile zorlanan doğruluğu

F#bildirmek kolay ve güçlü uygulamada işlevlerdir. İle birlikte kullanıldığında [desen eşleştirme](language-reference/pattern-matching.md), bunlar, doğruluk, derleyici tarafından zorlanır davranışı tanımlamanızı sağlar.

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F#İşlevler ayrıca birinci parametre olarak geçirilen edilebilmeleri ve diğer işlevlerden döndürülebilir anlamına gelir.

## <a name="functions-to-define-operations-on-objects"></a>Nesneler üzerinde işlemleri tanımlamak için işlevleri

F#blend veri ve işlevsellik gerektiğinde yararlı veri türleri olan nesneleri için tam destek sunar. F#işlevleri, nesneleri işlemek için kullanılır.

```fsharp
type Set<[<EqualityConditionOn>] ‘T when ‘T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

Nesne yönelimli, içinde bir kod yazmak yerine F#, işler kod nesneleri değiştirmek için başka veri türü işlevler için genellikle yazacaksınız. Gibi özellikleri [genel arabirimler](language-reference/interfaces.md), [nesne ifadeleri](language-reference/object-expressions.md)ve kullanmalıdır [üyeleri](language-reference/members/index.md) içinde ortak olan daha büyük F# programlar.

## <a name="next-steps"></a>Sonraki adımlar

Daha büyük bir hakkında daha fazla bilgi edinmek için F# özellikleri kullanıma [ F# Turu](tour.md).