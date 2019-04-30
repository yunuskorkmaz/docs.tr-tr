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
# <a name="what-is-f"></a><span data-ttu-id="4f2ed-104">F nedir\#</span><span class="sxs-lookup"><span data-stu-id="4f2ed-104">What is F\#</span></span>

<span data-ttu-id="4f2ed-105">F#doğru ve sürdürülebilir kod yazmayı kolaylaştıran bir işlevsel programlama dilidir.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="4f2ed-106">F#öncelikle programlama, türler ve tür çıkarımı yapılan ve otomatik olarak genelleştirilmiş işlevleri tanımlama içerir.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="4f2ed-107">Bu, odağınızı sorun etki alanı ve programlama ayrıntılarını yerine verilerini düzenleme kalmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="4f2ed-108">F#dahil olmak üzere çok sayıda özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4f2ed-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="4f2ed-109">Basit sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f2ed-109">Lightweight syntax</span></span>
* <span data-ttu-id="4f2ed-110">Varsayılan olarak sabit</span><span class="sxs-lookup"><span data-stu-id="4f2ed-110">Immutable by default</span></span>
* <span data-ttu-id="4f2ed-111">Tür çıkarımı ve otomatik Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f2ed-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="4f2ed-112">Birinci sınıf İşlevler</span><span class="sxs-lookup"><span data-stu-id="4f2ed-112">First-class functions</span></span>
* <span data-ttu-id="4f2ed-113">Güçlü veri türleri</span><span class="sxs-lookup"><span data-stu-id="4f2ed-113">Powerful data types</span></span>
* <span data-ttu-id="4f2ed-114">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="4f2ed-114">Pattern matching</span></span>
* <span data-ttu-id="4f2ed-115">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="4f2ed-115">Async programming</span></span>

<span data-ttu-id="4f2ed-116">Tam bir özellikler kümesi belgelenir [ F# dil başvurusu](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="4f2ed-116">A full set of features are documented in the [F# language reference](language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="4f2ed-117">Zengin veri türleri</span><span class="sxs-lookup"><span data-stu-id="4f2ed-117">Rich data types</span></span>

<span data-ttu-id="4f2ed-118">Veri türleri gibi [kayıtları](language-reference/records.md) ve [ayırt edici birleşimler](language-reference/discriminated-unions.md) , karmaşık verileri ve etki alanları temsil eden olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-118">Data types such as [Records](language-reference/records.md) and [Discriminated Unions](language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="4f2ed-119">F#kayıtlar ve ayrılmış birleşimler, null olmayan, sabit ve kullanımı çok kolay hale getirme varsayılan olarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="4f2ed-120">İşlevler ve desen eşleştirme ile zorlanan doğruluğu</span><span class="sxs-lookup"><span data-stu-id="4f2ed-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="4f2ed-121">F#bildirmek kolay ve güçlü uygulamada işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="4f2ed-122">İle birlikte kullanıldığında [desen eşleştirme](language-reference/pattern-matching.md), bunlar, doğruluk, derleyici tarafından zorlanır davranışı tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-122">When combined with [pattern matching](language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="4f2ed-123">F#İşlevler ayrıca birinci parametre olarak geçirilen edilebilmeleri ve diğer işlevlerden döndürülebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="4f2ed-124">Nesneler üzerinde işlemleri tanımlamak için işlevleri</span><span class="sxs-lookup"><span data-stu-id="4f2ed-124">Functions to define operations on objects</span></span>

<span data-ttu-id="4f2ed-125">F#blend veri ve işlevsellik gerektiğinde yararlı veri türleri olan nesneleri için tam destek sunar.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="4f2ed-126">F#işlevleri, nesneleri işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-126">F# functions are used to manipulate objects.</span></span>

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

<span data-ttu-id="4f2ed-127">Nesne yönelimli, içinde bir kod yazmak yerine F#, işler kod nesneleri değiştirmek için başka veri türü işlevler için genellikle yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="4f2ed-128">Gibi özellikleri [genel arabirimler](language-reference/interfaces.md), [nesne ifadeleri](language-reference/object-expressions.md)ve kullanmalıdır [üyeleri](language-reference/members/index.md) içinde ortak olan daha büyük F# programlar.</span><span class="sxs-lookup"><span data-stu-id="4f2ed-128">Features such as [generic interfaces](language-reference/interfaces.md), [object expressions](language-reference/object-expressions.md), and judicious use of [members](language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f2ed-129">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="4f2ed-129">Next steps</span></span>

<span data-ttu-id="4f2ed-130">Daha büyük bir hakkında daha fazla bilgi edinmek için F# özellikleri kullanıma [ F# Turu](tour.md).</span><span class="sxs-lookup"><span data-stu-id="4f2ed-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>