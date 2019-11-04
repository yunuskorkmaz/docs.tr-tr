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
# <a name="value-options"></a><span data-ttu-id="40e21-103">Değer Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="40e21-103">Value Options</span></span>

<span data-ttu-id="40e21-104">' Deki F# değer seçenek türü, aşağıdaki iki koşul ayrı olduğunda kullanılır:</span><span class="sxs-lookup"><span data-stu-id="40e21-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="40e21-105">Bir senaryo, bir [ F# seçenek](options.md)için uygundur.</span><span class="sxs-lookup"><span data-stu-id="40e21-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="40e21-106">Yapı kullanımı, senaryonuza bir performans avantajı sağlar.</span><span class="sxs-lookup"><span data-stu-id="40e21-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="40e21-107">Tüm performans duyarlı senaryolar yapılar kullanılarak "çözülür".</span><span class="sxs-lookup"><span data-stu-id="40e21-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="40e21-108">Başvuru türleri yerine bunları kullanırken, kopyalamanın ek maliyetini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40e21-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="40e21-109">Ancak, büyük F# programlar genellikle dinamik yollardan akan birçok isteğe bağlı türü oluşturur ve bu gibi durumlarda, yapılar genellikle programın kullanım ömrü boyunca daha iyi genel performans elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="40e21-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="40e21-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="40e21-110">Definition</span></span>

<span data-ttu-id="40e21-111">Değer seçeneği, başvuru seçenek türüne benzer bir [struct ayrılmış birleşim](discriminated-unions.md#struct-discriminated-unions) olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="40e21-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="40e21-112">Tanımı şu şekilde düşünülebilir:</span><span class="sxs-lookup"><span data-stu-id="40e21-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="40e21-113">Değer seçeneği yapısal eşitlik ve karşılaştırmaya uyar.</span><span class="sxs-lookup"><span data-stu-id="40e21-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="40e21-114">Ana fark, derlenmiş ad, tür adı ve büyük/küçük harf adlarının tümü bir değer türü olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="40e21-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="40e21-115">Değer seçeneklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="40e21-115">Using Value Options</span></span>

<span data-ttu-id="40e21-116">Değer seçenekleri tıpkı [Seçenekler](options.md)gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40e21-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="40e21-117">`ValueSome`, bir değerin mevcut olduğunu göstermek için kullanılır ve bir değer mevcut olmadığında `ValueNone` kullanılır:</span><span class="sxs-lookup"><span data-stu-id="40e21-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="40e21-118">[Seçeneklerde](options.md)olduğu gibi, `ValueOption` döndüren bir işlevin adlandırma kuralı, `try`önek olarak önektir.</span><span class="sxs-lookup"><span data-stu-id="40e21-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="40e21-119">Değer seçeneği özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="40e21-119">Value Option properties and methods</span></span>

<span data-ttu-id="40e21-120">Şu anda değer seçenekleri için bir özellik var: `Value`.</span><span class="sxs-lookup"><span data-stu-id="40e21-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="40e21-121">Bu özellik çağrıldığında hiçbir değer yoksa <xref:System.InvalidOperationException> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="40e21-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="40e21-122">Değer seçeneği işlevleri</span><span class="sxs-lookup"><span data-stu-id="40e21-122">Value Option functions</span></span>

<span data-ttu-id="40e21-123">Şu anda değer seçenekleri için bir modüle bağlı işlev var, `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="40e21-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="40e21-124">`defaultArg` işlevinde olduğu gibi `defaultValueArg`, varsa verilen değer seçeneğinin temel alınan değerini döndürür; Aksi halde, belirtilen varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="40e21-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="40e21-125">Şu anda değer seçenekleri için modüle özgü başka işlevler yoktur.</span><span class="sxs-lookup"><span data-stu-id="40e21-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="40e21-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40e21-126">See also</span></span>

- [<span data-ttu-id="40e21-127">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="40e21-127">Options</span></span>](options.md)
