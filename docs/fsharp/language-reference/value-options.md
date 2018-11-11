---
title: Değer seçenekleri (F#)
description: Seçenek türü bir yapı sürümü F# değer seçeneği türü hakkında bilgi edinin.
ms.date: 06/16/2018
ms.openlocfilehash: 978bd1713c16f7c050ccb097cb134973d10ef6f5
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50185842"
---
# <a name="value-options"></a><span data-ttu-id="45688-103">Değer seçenekleri</span><span class="sxs-lookup"><span data-stu-id="45688-103">Value Options</span></span>

<span data-ttu-id="45688-104">Aşağıdaki iki koşul tuttuğunuzda değeri seçenek türünün F# kullanılır:</span><span class="sxs-lookup"><span data-stu-id="45688-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="45688-105">Bir senaryo için uygun olan bir [F# seçeneği](options.md).</span><span class="sxs-lookup"><span data-stu-id="45688-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="45688-106">Bir yapı kullanarak sizin senaryonuzda bu performans artar.</span><span class="sxs-lookup"><span data-stu-id="45688-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="45688-107">Tüm performans açısından duyarlı senaryoları "yapılar kullanarak çözülen".</span><span class="sxs-lookup"><span data-stu-id="45688-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="45688-108">Bunları başvuru türleri yerine kullanırken kopyalama ek maliyeti dikkate almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="45688-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="45688-109">Ancak, çünkü yapılar bazen daha iyi bir program ömrü boyunca genel performansı sağlayabilir büyük F# programları genellikle etkin yolları akış birçok isteğe bağlı tür örneği.</span><span class="sxs-lookup"><span data-stu-id="45688-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, because structs can sometimes yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="45688-110">Tanım</span><span class="sxs-lookup"><span data-stu-id="45688-110">Definition</span></span>

<span data-ttu-id="45688-111">Değer seçeneği olarak tanımlanmış olan bir [ayırt edici birleşim](discriminated-unions.md#struct-discriminated-unions) olan başvuru seçeneği türüne benzerdir.</span><span class="sxs-lookup"><span data-stu-id="45688-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="45688-112">Tanımı şöyle düşünülebilir:</span><span class="sxs-lookup"><span data-stu-id="45688-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="45688-113">Değer seçeneği yapısal eşitlik ve karşılaştırma için uygundur.</span><span class="sxs-lookup"><span data-stu-id="45688-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="45688-114">İkisi arasındaki temel fark, derlenmiş ad, tür adı ve büyük/küçük harf adları, bir değer türü olduğunu belirtmek ' dir.</span><span class="sxs-lookup"><span data-stu-id="45688-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="45688-115">Değer seçeneklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="45688-115">Using Value Options</span></span>

<span data-ttu-id="45688-116">Değer seçenekleri gibi kullanılır [seçenekleri](options.md).</span><span class="sxs-lookup"><span data-stu-id="45688-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="45688-117">`ValueSome` bir değerin mevcut olduğunu belirtmek için kullanılır ve `ValueNone` bir değer mevcut olmadığında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="45688-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="45688-118">Olduğu gibi [seçenekleri](options.md), döndüren bir işlev için adlandırma kuralı `ValueOption` ile ön ek için `try`.</span><span class="sxs-lookup"><span data-stu-id="45688-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="45688-119">Değer seçeneği özellikleri ve yöntemleri</span><span class="sxs-lookup"><span data-stu-id="45688-119">Value Option properties and methods</span></span>

<span data-ttu-id="45688-120">Şu anda bir özellik için değer seçenekleri mevcuttur: `Value`.</span><span class="sxs-lookup"><span data-stu-id="45688-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="45688-121">Bir <xref:System.InvalidOperationException> hiçbir değer yoksa, bu özelliğin çağırılır olması durumunda tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="45688-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="45688-122">Değer seçeneği işlevleri</span><span class="sxs-lookup"><span data-stu-id="45688-122">Value Option functions</span></span>

<span data-ttu-id="45688-123">Şu anda bir modül bağlı işlev değer seçenekleri için olan `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="45688-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

<span data-ttu-id="45688-124">Olduğu gibi `defaultArg` işlevi `defaultValueArg` belirli değer seçeneği temel değerini döndürür var; Aksi takdirde, varsayılan değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="45688-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="45688-125">Şu anda hiç bir modül bağlı işlevi değer seçenekleri için vardır.</span><span class="sxs-lookup"><span data-stu-id="45688-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="45688-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45688-126">See also</span></span>

- [<span data-ttu-id="45688-127">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="45688-127">Options</span></span>](options.md)
