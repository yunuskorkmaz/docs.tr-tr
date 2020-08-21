---
title: Sonuçlar
description: "F # ' Result ' türünün, hataya dayanıklı kod yazmanıza yardımcı olması için nasıl kullanılacağını öğrenin."
ms.date: 08/13/2020
ms.openlocfilehash: d69e6ddc37bcf5cb5fc28644d59a11a822b83faa
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656924"
---
# <a name="results"></a><span data-ttu-id="ef217-103">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="ef217-103">Results</span></span>

<span data-ttu-id="ef217-104">`Result<'T,'TFailure>`Türü, birleştirilebilen hataya dayanıklı kod yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef217-104">The `Result<'T,'TFailure>` type lets you write error-tolerant code that can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef217-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef217-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="ef217-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef217-106">Remarks</span></span>

<span data-ttu-id="ef217-107">[`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html)İçin yerleşik kombinatör modülüne bakın `Result` .</span><span class="sxs-lookup"><span data-stu-id="ef217-107">See the [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) module for the built-in combinators for the `Result`.</span></span> <span data-ttu-id="ef217-108">türüyle.</span><span class="sxs-lookup"><span data-stu-id="ef217-108">type.</span></span>

<span data-ttu-id="ef217-109">Sonuç türünün bir [struct ayrılmış birleşim](discriminated-unions.md#struct-discriminated-unions)olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ef217-109">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions).</span></span> <span data-ttu-id="ef217-110">Yapısal eşitlik semantiği burada geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ef217-110">Structural equality semantics apply here.</span></span>

<span data-ttu-id="ef217-111">`Result`Tür genellikle F # Community Içinde [Railway odaklı programlama](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) olarak adlandırılan monmonotik hata işleme içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef217-111">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="ef217-112">Aşağıdaki önemsiz örnekte bu yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef217-112">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="ef217-113">Görebileceğiniz gibi, tümünün bir döndürmesini zorlarsanız, çeşitli doğrulama işlevlerini birbirine kolayca zincirleyebilirsiniz `Result` .</span><span class="sxs-lookup"><span data-stu-id="ef217-113">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="ef217-114">Bu, bunun gibi işlevleri, sizin için gerekli olduğu kadar birleştirilebilen küçük parçalara bölmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ef217-114">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="ef217-115">Bu Ayrıca, bir doğrulamanın sonunda, daha yüksek bir program doğruluğu uygulayan, bir doğrulama sayısının sonunda [kalıp eşleştirmesinin](pattern-matching.md) kullanımını *zorunlu kılma* değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="ef217-115">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef217-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef217-116">See also</span></span>

- [<span data-ttu-id="ef217-117">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="ef217-117">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="ef217-118">Model eşleştirme</span><span class="sxs-lookup"><span data-stu-id="ef217-118">Pattern Matching</span></span>](pattern-matching.md)
