---
title: NameOf
description: Kaynak kodunuzda herhangi bir simgenin adını üretmeniz için bir meta programlama özelliği olan NameOf işleci hakkında bilgi edinin.
ms.date: 11/12/2020
ms.openlocfilehash: 9947d7172d1b73db5c181297ec8b1131382e1f5e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688616"
---
# <a name="nameof"></a><span data-ttu-id="30513-103">NameOf</span><span class="sxs-lookup"><span data-stu-id="30513-103">Nameof</span></span>

<span data-ttu-id="30513-104">`nameof`İfade, kaynaktaki neredeyse tüm F # yapısı için kaynaktaki adla eşleşen bir dize sabiti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30513-104">The `nameof` expression produces a string constant that matches the name in source for nearly any F# construct in source.</span></span>

## <a name="syntax"></a><span data-ttu-id="30513-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="30513-105">Syntax</span></span>

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a><span data-ttu-id="30513-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30513-106">Remarks</span></span>

<span data-ttu-id="30513-107">`nameof` kendisine geçirilen simgeyi çözümleyerek ve kaynak kodunuzda bildirildiği için bu sembolün adını üreten işe yarar.</span><span class="sxs-lookup"><span data-stu-id="30513-107">`nameof` works by resolving the symbol passed to it and produces the name of that symbol as it is declared in your source code.</span></span> <span data-ttu-id="30513-108">Bu, günlüğe kaydetme gibi çeşitli senaryolarda faydalıdır ve günlüğe kaydetme işleminin kaynak kodundaki değişikliklere karşı korunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="30513-108">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) ($"Value passed in was %d{month}.")

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="30513-109">Son satır bir özel durum oluşturur ve `"month"` hata iletisinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="30513-109">The last line will throw an exception and `"month"` will be shown in the error message.</span></span>

<span data-ttu-id="30513-110">Neredeyse her F # yapısının adını alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30513-110">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

<span data-ttu-id="30513-111">`nameof` Birinci sınıf bir işlev değildir ve bu şekilde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30513-111">`nameof` is not a first-class function and cannot be used as such.</span></span> <span data-ttu-id="30513-112">Bu, kısmen uygulanamadığından ve değerler F # ardışık düzen işleçleri yoluyla buna çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="30513-112">That means it cannot be partially applied and values cannot be piped into it via F# pipeline operators.</span></span>

## <a name="nameof-on-operators"></a><span data-ttu-id="30513-113">Of işleçleri için NameOf</span><span class="sxs-lookup"><span data-stu-id="30513-113">Nameof on operators</span></span>

<span data-ttu-id="30513-114">F # içindeki işleçler iki şekilde, bir operatör metninin kendisi olarak veya derlenen formu temsil eden bir sembol ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30513-114">Operators in F# can be used in two ways, as an operator text itself, or a symbol representing the compiled form.</span></span> <span data-ttu-id="30513-115">`nameof` bir işleçte, kaynak içinde bildirildiği gibi işlecin adını üretir.</span><span class="sxs-lookup"><span data-stu-id="30513-115">`nameof` on an operator will produce the name of the operator as it is declared in source.</span></span> <span data-ttu-id="30513-116">Derlenen adı almak için, kaynakta derlenen adı kullanın:</span><span class="sxs-lookup"><span data-stu-id="30513-116">To get the compiled name, use the compiled name in source:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a><span data-ttu-id="30513-117">Genel türlerde NameOf</span><span class="sxs-lookup"><span data-stu-id="30513-117">Nameof on generics</span></span>

<span data-ttu-id="30513-118">Genel tür parametresinin adını da alabilirsiniz, ancak sözdizimi farklıdır:</span><span class="sxs-lookup"><span data-stu-id="30513-118">You can also take a name of a generic type parameter, but the syntax is different:</span></span>

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

<span data-ttu-id="30513-119">`nameof<'TGeneric>` , bir çağrı sitesinde değiştirilen türün adı değil, sembolün adını kaynak bölümünde tanımlanan şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="30513-119">`nameof<'TGeneric>` will take the name of the symbol as defined in source, not the name of the type substituted at a call site.</span></span>

<span data-ttu-id="30513-120">Sözdiziminin farklı olmasının nedeni, ve gibi diğer F # içsel işleçlerle hizalanmasıdır `typeof<>` `typedefof<>` .</span><span class="sxs-lookup"><span data-stu-id="30513-120">The reason why the syntax is different is to align with other F# intrinsic operators like `typeof<>` and `typedefof<>`.</span></span> <span data-ttu-id="30513-121">Bu, genel türler üzerinde ve kaynak üzerinde başka her şey üzerinde işlem yapan işleçlere göre F # tutarlılığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="30513-121">This makes F# consistent with respect to operators that act on generic types and anything else in source.</span></span>

## <a name="nameof-in-pattern-matching"></a><span data-ttu-id="30513-122">Model eşleştirme içindeki NameOf</span><span class="sxs-lookup"><span data-stu-id="30513-122">Nameof in pattern matching</span></span>

<span data-ttu-id="30513-123">Bu [ `nameof` model](pattern-matching.md#nameof-pattern) , `nameof` şöyle bir model eşleşme ifadesinde kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="30513-123">The [`nameof` pattern](pattern-matching.md#nameof-pattern) lets you use `nameof` in a pattern match expression like so:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
