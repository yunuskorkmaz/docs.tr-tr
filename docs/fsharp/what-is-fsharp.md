---
title: F# nedir?
description: F# Programlama dilinin ne olduğu ve F# programlamanın nasıl olduğu hakkında bilgi edinin. Zengin veri türleri, işlevleri ve nasıl birbirine sığması hakkında bilgi edinin.
ms.date: 08/03/2018
ms.openlocfilehash: 3cba509f59a8e81e1a0264de7451e9d80304d768
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332728"
---
# <a name="what-is-f"></a><span data-ttu-id="066b6-104">F\# nedir?</span><span class="sxs-lookup"><span data-stu-id="066b6-104">What is F\#</span></span>

<span data-ttu-id="066b6-105">F#, doğru ve sürdürülebilir kod yazmayı kolaylaştıran işlevsel bir programlama dilidir.</span><span class="sxs-lookup"><span data-stu-id="066b6-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="066b6-106">F#programlama öncelikle, türü çıkarılan ve otomatik olarak Genelleştirilmiş türleri ve işlevleri tanımlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="066b6-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="066b6-107">Bu, odağın sorun etki alanında kalmasına ve programlama ayrıntıları yerine verilerinin işlenmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="066b6-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="066b6-108">F#Aşağıdakiler dahil olmak üzere çeşitli özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="066b6-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="066b6-109">Hafif sözdizimi</span><span class="sxs-lookup"><span data-stu-id="066b6-109">Lightweight syntax</span></span>
* <span data-ttu-id="066b6-110">Varsayılan olarak sabit</span><span class="sxs-lookup"><span data-stu-id="066b6-110">Immutable by default</span></span>
* <span data-ttu-id="066b6-111">Tür çıkarımı ve otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="066b6-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="066b6-112">Birinci sınıf işlevler</span><span class="sxs-lookup"><span data-stu-id="066b6-112">First-class functions</span></span>
* <span data-ttu-id="066b6-113">Güçlü veri türleri</span><span class="sxs-lookup"><span data-stu-id="066b6-113">Powerful data types</span></span>
* <span data-ttu-id="066b6-114">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="066b6-114">Pattern matching</span></span>
* <span data-ttu-id="066b6-115">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="066b6-115">Async programming</span></span>

<span data-ttu-id="066b6-116">Tam özellikler kümesi, [ F# dil başvurusunda](./language-reference/index.md)belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="066b6-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="066b6-117">Zengin veri türleri</span><span class="sxs-lookup"><span data-stu-id="066b6-117">Rich data types</span></span>

<span data-ttu-id="066b6-118">[Kayıtlar](./language-reference/records.md) ve [ayırt edici birleşimler](./language-reference/discriminated-unions.md) gibi veri türleri, karmaşık verileri ve etki alanlarını temsil etmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="066b6-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="066b6-119">F#kayıtlar ve ayrılmış birleşimler, varsayılan olarak boş, değişmez ve karşılaştırılabilir değildir. Bu, kullanımı çok kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="066b6-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="066b6-120">İşlevler ve model eşleştirme ile uygulanan doğruluk</span><span class="sxs-lookup"><span data-stu-id="066b6-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="066b6-121">F#işlevler, kolayca bildirmek ve güçlü bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="066b6-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="066b6-122">[Desenler eşleştirilirken](./language-reference/pattern-matching.md), doğruluk derleyici tarafından zorlanan davranışı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="066b6-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="066b6-123">F#işlevler ayrıca birinci sınıftır, yani Parametreler olarak geçirilebilir ve diğer işlevlerden geri döndürülebilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="066b6-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="066b6-124">Nesneler üzerinde işlem tanımlamak için işlevler</span><span class="sxs-lookup"><span data-stu-id="066b6-124">Functions to define operations on objects</span></span>

<span data-ttu-id="066b6-125">F#, veri ve işlevsellik Blend gerektiğinde yararlı veri türleri olan nesneler için tam desteğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="066b6-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="066b6-126">F#işlevleri nesneleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="066b6-126">F# functions are used to manipulate objects.</span></span>

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

<span data-ttu-id="066b6-127">İçinde F#nesne odaklı kod yazmak yerine, genellikle nesneleri işlemek için işlevleri farklı bir veri türü olarak karşılayan kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="066b6-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="066b6-128">[Genel arabirimler](./language-reference/interfaces.md), [nesne ifadeleri](./language-reference/object-expressions.md)ve [üyenin](./language-reference/members/index.md) akıllıca kullanımı gibi özellikler daha büyük F# programlarda ortaktır.</span><span class="sxs-lookup"><span data-stu-id="066b6-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="066b6-129">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="066b6-129">Next steps</span></span>

<span data-ttu-id="066b6-130">Daha büyük bir F# özellikler kümesi hakkında daha fazla bilgi edinmek için [ F# tura](tour.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="066b6-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
