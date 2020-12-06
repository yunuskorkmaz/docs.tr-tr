---
title: F# nedir?
description: 'F # programlama dilinin ne olduğu ve F # programlamanın nasıl olduğu hakkında bilgi edinin. Zengin veri türleri, işlevleri ve nasıl birbirine sığması hakkında bilgi edinin.'
ms.date: 08/03/2018
ms.openlocfilehash: a6bad3e1db63c3fe948b5916925d5eb24a18a41c
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739483"
---
# <a name="what-is-f"></a>F nedir?\#

F #, doğru ve sürdürülebilir kod yazmayı kolaylaştıran işlevsel bir programlama dilidir.

F # programlama öncelikle tür tarafından çıkarılan ve genelleştirilmiş, otomatik olarak oluşturulan türleri ve işlevleri tanımlamayı içerir. Bu, odağın sorun etki alanında kalmasına ve programlama ayrıntıları yerine verilerinin işlenmesine olanak tanır.

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name = $"Hello, {name}! Isn't F# great?"

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn $"{greeting}")

    0
```

F #, aşağıdakiler dahil olmak üzere çeşitli özelliklere sahiptir:

* Hafif sözdizimi
* Varsayılan olarak sabit
* Tür çıkarımı ve otomatik Genelleştirme
* Birinci sınıf işlevler
* Güçlü veri türleri
* Desen eşleştirme
* Zaman uyumsuz programlama

Tüm özellikler kümesi [F # dil başvurusunda](./language-reference/index.md)belgelenmiştir.

## <a name="rich-data-types"></a>Zengin veri türleri

[Kayıtlar](./language-reference/records.md) ve [ayırt edici birleşimler](./language-reference/discriminated-unions.md) gibi veri türleri, karmaşık verileri ve etki alanlarını temsil etmenize olanak tanır.

```fsharp
// Group data with Records
type SuccessfulWithdrawal =
    { Amount: decimal
      Balance: decimal }

type FailedWithdrawal =
    { Amount: decimal
      Balance: decimal
      IsOverdraft: bool }

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F # kayıtları ve ayrılmış birleşimler, varsayılan olarak boş, değişmez ve karşılaştırılabilir değildir. Bu, kullanımı çok kolay hale getirir.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>İşlevler ve model eşleştirme ile uygulanan doğruluk

F # işlevlerinin kolayca bildirilmesini ve güçlü bir yöntem olduğunu. [Desenler eşleştirilirken](./language-reference/pattern-matching.md), doğruluk derleyici tarafından zorlanan davranışı tanımlamanızı sağlar.

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f{s.Amount}"
    | InsufficientFunds f -> printfn "Failed: balance is %f{f.Balance}"
    | CardExpired d -> printfn "Failed: card expired on {d}"
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F # işlevleri de birinci sınıftır, yani parametre olarak geçirilebilir ve diğer işlevlerden geri döndürülebilecek anlamına gelir.

## <a name="functions-to-define-operations-on-objects"></a>Nesneler üzerinde işlem tanımlamak için işlevler

F #, veri ve işlevsellik Blend gerektiğinde yararlı veri türleri olan nesneler için tam desteğe sahiptir. F # işlevleri nesneleri işlemek için kullanılır.

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

Nesne odaklı kod yazmak yerine, F # ' da genellikle nesneleri işlemek için işlevlere başka bir veri türü olarak niteleyen kodu yazarsınız. [Genel arabirimler](./language-reference/interfaces.md), [nesne ifadeleri](./language-reference/object-expressions.md)ve [üyenin](./language-reference/members/index.md) akıllıca kullanımı gibi özellikler daha büyük F # programlarında ortaktır.

## <a name="next-steps"></a>Sonraki adımlar

Daha büyük bir F # özellikleri kümesi hakkında daha fazla bilgi edinmek için [f # turuna](tour.md)göz atın.
