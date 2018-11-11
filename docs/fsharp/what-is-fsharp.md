---
title: F# nedir
description: F# programlama gibi nedir ve hangi F# programlama dili hakkında bilgi edinin. Zengin veri türleri, İşlevler ve bunlar birbirine nasıl uyduğunu hakkında bilgi edinin.
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863302"
---
# <a name="what-is-f"></a>F# nedir #

F#, doğru ve sürdürülebilir kod yazmak kolay bir işlevsel programlama dilidir.

F# programlama, türler ve tür çıkarımı yapılan ve otomatik olarak genelleştirilmiş işlevleri tanımlama öncelikle içerir. Bu, odağınızı sorun etki alanı ve programlama ayrıntılarını yerine verilerini düzenleme kalmasına izin verir.

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

F# dahil olmak üzere çok sayıda özelliğe sahiptir:

* Basit sözdizimi
* Varsayılan olarak sabit
* Tür çıkarımı ve otomatik Genelleştirme
* Birinci sınıf İşlevler
* Güçlü veri türleri
* Desen eşleştirme
* Zaman uyumsuz programlama

Tam bir özellikler kümesi belgelenir [F# dili başvurusu](language-reference/index.md).

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

F# kayıt ve ayrılmış birleşimler, null olmayan, sabit ve kullanımı çok kolay hale getirme varsayılan olarak karşılaştırılabilir.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>İşlevler ve desen eşleştirme ile zorlanan doğruluğu

F# işlevleri bildirmek kolay ve güçlü uygulamada. İle birlikte kullanıldığında [desen eşleştirme](language-reference/pattern-matching.md), bunlar, doğruluk, derleyici tarafından zorlanır davranışı tanımlamanızı sağlar.

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

F# işlevleri de birinci parametre olarak geçirilen edilebilmeleri ve diğer işlevlerden döndürülebilir anlamına gelir.

## <a name="functions-to-define-operations-on-objects"></a>Nesneler üzerinde işlemleri tanımlamak için işlevleri

F# yararlı veri türleri, verilere ve işlevlere blend gerektiğinde olan nesneleri için tam destek sunar. F# işlevleri nesneleri işlemek için kullanılır.

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

Nesne F#'ta odaklı, kod yazmak yerine, davranır işlemek için başka veri türü işlevler için nesneleri, kod genellikle yazacaksınız. Gibi özellikleri [genel arabirimler](language-reference/interfaces.md), [nesne ifadeleri](language-reference/object-expressions.md)ve kullanmalıdır [üyeleri](language-reference/members/index.md) büyük F# programlarında ortaktır.

## <a name="next-steps"></a>Sonraki adımlar

Daha büyük bir F# özellikleri hakkında daha fazla bilgi edinmek için kullanıma [F# Turu](tour.md).