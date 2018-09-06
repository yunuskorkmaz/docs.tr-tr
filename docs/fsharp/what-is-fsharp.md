---
title: 'F # nedir'
description: 'F # programlama gibi nedir ve hangi F # programlama dili hakkında bilgi edinin. Zengin veri türleri, İşlevler ve bunlar birbirine nasıl uyduğunu hakkında bilgi edinin.'
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863302"
---
# <a name="what-is-f"></a><span data-ttu-id="72b45-104">F # nedir</span><span class="sxs-lookup"><span data-stu-id="72b45-104">What is F#</span></span> #

<span data-ttu-id="72b45-105">F #, doğru ve sürdürülebilir kod yazmak kolay bir işlevsel programlama dilidir.</span><span class="sxs-lookup"><span data-stu-id="72b45-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="72b45-106">F # programlama, türler ve tür çıkarımı yapılan ve otomatik olarak genelleştirilmiş işlevleri tanımlama öncelikle içerir.</span><span class="sxs-lookup"><span data-stu-id="72b45-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="72b45-107">Bu, odağınızı sorun etki alanı ve programlama ayrıntılarını yerine verilerini düzenleme kalmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="72b45-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="72b45-108">F # dahil olmak üzere çok sayıda özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="72b45-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="72b45-109">Basit sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72b45-109">Lightweight syntax</span></span>
* <span data-ttu-id="72b45-110">Varsayılan olarak sabit</span><span class="sxs-lookup"><span data-stu-id="72b45-110">Immutable by default</span></span>
* <span data-ttu-id="72b45-111">Tür çıkarımı ve otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="72b45-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="72b45-112">Birinci sınıf İşlevler</span><span class="sxs-lookup"><span data-stu-id="72b45-112">First-class functions</span></span>
* <span data-ttu-id="72b45-113">Güçlü veri türleri</span><span class="sxs-lookup"><span data-stu-id="72b45-113">Powerful data types</span></span>
* <span data-ttu-id="72b45-114">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="72b45-114">Pattern matching</span></span>
* <span data-ttu-id="72b45-115">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="72b45-115">Async programming</span></span>

<span data-ttu-id="72b45-116">Tam bir özellikler kümesi belgelenir [F # dili başvurusu](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="72b45-116">A full set of features are documented in the [F# language reference](language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="72b45-117">Zengin veri türleri</span><span class="sxs-lookup"><span data-stu-id="72b45-117">Rich data types</span></span>

<span data-ttu-id="72b45-118">Veri türleri gibi [kayıtları](language-reference/records.md) ve [ayırt edici birleşimler](language-reference/discriminated-unions.md) , karmaşık verileri ve etki alanları temsil eden olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="72b45-118">Data types such as [Records](language-reference/records.md) and [Discriminated Unions](language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="72b45-119">F # kayıt ve ayrılmış birleşimler, null olmayan, sabit ve kullanımı çok kolay hale getirme varsayılan olarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="72b45-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="72b45-120">İşlevler ve desen eşleştirme ile zorlanan doğruluğu</span><span class="sxs-lookup"><span data-stu-id="72b45-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="72b45-121">F # işlevleri bildirmek kolay ve güçlü uygulamada.</span><span class="sxs-lookup"><span data-stu-id="72b45-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="72b45-122">İle birlikte kullanıldığında [desen eşleştirme](language-reference/pattern-matching.md), bunlar, doğruluk, derleyici tarafından zorlanır davranışı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="72b45-122">When combined with [pattern matching](language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="72b45-123">F # işlevleri de birinci parametre olarak geçirilen edilebilmeleri ve diğer işlevlerden döndürülebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="72b45-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="72b45-124">Nesneler üzerinde işlemleri tanımlamak için işlevleri</span><span class="sxs-lookup"><span data-stu-id="72b45-124">Functions to define operations on objects</span></span>

<span data-ttu-id="72b45-125">F # yararlı veri türleri, verilere ve işlevlere blend gerektiğinde olan nesneleri için tam destek sunar.</span><span class="sxs-lookup"><span data-stu-id="72b45-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="72b45-126">F # işlevleri nesneleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72b45-126">F# functions are used to manipulate objects.</span></span>

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

<span data-ttu-id="72b45-127">Nesne F #'ta odaklı, kod yazmak yerine, davranır işlemek için başka veri türü işlevler için nesneleri, kod genellikle yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="72b45-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="72b45-128">Gibi özellikleri [genel arabirimler](language-reference/interfaces.md), [nesne ifadeleri](language-reference/object-expressions.md)ve kullanmalıdır [üyeleri](language-reference/members/index.md) büyük F # programlarında ortaktır.</span><span class="sxs-lookup"><span data-stu-id="72b45-128">Features such as [generic interfaces](language-reference/interfaces.md), [object expressions](language-reference/object-expressions.md), and judicious use of [members](language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="72b45-129">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="72b45-129">Next steps</span></span>

<span data-ttu-id="72b45-130">Daha büyük bir F # özellikleri hakkında daha fazla bilgi edinmek için kullanıma [F # Turu](tour.md).</span><span class="sxs-lookup"><span data-stu-id="72b45-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>