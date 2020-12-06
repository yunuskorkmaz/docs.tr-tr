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
# <a name="what-is-f"></a><span data-ttu-id="bb0f4-104">F nedir?\#</span><span class="sxs-lookup"><span data-stu-id="bb0f4-104">What is F\#</span></span>

<span data-ttu-id="bb0f4-105">F #, doğru ve sürdürülebilir kod yazmayı kolaylaştıran işlevsel bir programlama dilidir.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="bb0f4-106">F # programlama öncelikle tür tarafından çıkarılan ve genelleştirilmiş, otomatik olarak oluşturulan türleri ve işlevleri tanımlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="bb0f4-107">Bu, odağın sorun etki alanında kalmasına ve programlama ayrıntıları yerine verilerinin işlenmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="bb0f4-108">F #, aşağıdakiler dahil olmak üzere çeşitli özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="bb0f4-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="bb0f4-109">Hafif sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb0f4-109">Lightweight syntax</span></span>
* <span data-ttu-id="bb0f4-110">Varsayılan olarak sabit</span><span class="sxs-lookup"><span data-stu-id="bb0f4-110">Immutable by default</span></span>
* <span data-ttu-id="bb0f4-111">Tür çıkarımı ve otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="bb0f4-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="bb0f4-112">Birinci sınıf işlevler</span><span class="sxs-lookup"><span data-stu-id="bb0f4-112">First-class functions</span></span>
* <span data-ttu-id="bb0f4-113">Güçlü veri türleri</span><span class="sxs-lookup"><span data-stu-id="bb0f4-113">Powerful data types</span></span>
* <span data-ttu-id="bb0f4-114">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="bb0f4-114">Pattern matching</span></span>
* <span data-ttu-id="bb0f4-115">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="bb0f4-115">Async programming</span></span>

<span data-ttu-id="bb0f4-116">Tüm özellikler kümesi [F # dil başvurusunda](./language-reference/index.md)belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="bb0f4-117">Zengin veri türleri</span><span class="sxs-lookup"><span data-stu-id="bb0f4-117">Rich data types</span></span>

<span data-ttu-id="bb0f4-118">[Kayıtlar](./language-reference/records.md) ve [ayırt edici birleşimler](./language-reference/discriminated-unions.md) gibi veri türleri, karmaşık verileri ve etki alanlarını temsil etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="bb0f4-119">F # kayıtları ve ayrılmış birleşimler, varsayılan olarak boş, değişmez ve karşılaştırılabilir değildir. Bu, kullanımı çok kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="bb0f4-120">İşlevler ve model eşleştirme ile uygulanan doğruluk</span><span class="sxs-lookup"><span data-stu-id="bb0f4-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="bb0f4-121">F # işlevlerinin kolayca bildirilmesini ve güçlü bir yöntem olduğunu.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="bb0f4-122">[Desenler eşleştirilirken](./language-reference/pattern-matching.md), doğruluk derleyici tarafından zorlanan davranışı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="bb0f4-123">F # işlevleri de birinci sınıftır, yani parametre olarak geçirilebilir ve diğer işlevlerden geri döndürülebilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="bb0f4-124">Nesneler üzerinde işlem tanımlamak için işlevler</span><span class="sxs-lookup"><span data-stu-id="bb0f4-124">Functions to define operations on objects</span></span>

<span data-ttu-id="bb0f4-125">F #, veri ve işlevsellik Blend gerektiğinde yararlı veri türleri olan nesneler için tam desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="bb0f4-126">F # işlevleri nesneleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-126">F# functions are used to manipulate objects.</span></span>

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

<span data-ttu-id="bb0f4-127">Nesne odaklı kod yazmak yerine, F # ' da genellikle nesneleri işlemek için işlevlere başka bir veri türü olarak niteleyen kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="bb0f4-128">[Genel arabirimler](./language-reference/interfaces.md), [nesne ifadeleri](./language-reference/object-expressions.md)ve [üyenin](./language-reference/members/index.md) akıllıca kullanımı gibi özellikler daha büyük F # programlarında ortaktır.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="bb0f4-129">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="bb0f4-129">Next steps</span></span>

<span data-ttu-id="bb0f4-130">Daha büyük bir F # özellikleri kümesi hakkında daha fazla bilgi edinmek için [f # turuna](tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="bb0f4-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
