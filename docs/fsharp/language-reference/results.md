---
title: Sonuçlar
description: Hataya dayanıklı kod yazmanıza yardımcı F# olması için ' Result ' türünü nasıl kullanacağınızı öğrenin.
ms.date: 04/24/2017
ms.openlocfilehash: 187aa26ccbaac7e0ec998756377bb7b0489eb1ab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424845"
---
# <a name="results"></a><span data-ttu-id="6bce9-103">Sonuçlar</span><span class="sxs-lookup"><span data-stu-id="6bce9-103">Results</span></span>

<span data-ttu-id="6bce9-104">4,1 ' F# den başlayarak, birleştirilebilen hata toleranslı kod yazmak için kullanabileceğiniz `Result<'T,'TFailure>` bir tür vardır.</span><span class="sxs-lookup"><span data-stu-id="6bce9-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bce9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bce9-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="6bce9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bce9-106">Remarks</span></span>

<span data-ttu-id="6bce9-107">Sonuç türünün, 4,1 ' de F# tanıtılan bir [Yapı ayrılmış birleşimi](discriminated-unions.md#struct-discriminated-unions)olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6bce9-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="6bce9-108">Yapısal eşitlik semantiği burada geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6bce9-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="6bce9-109">`Result` türü genellikle F# topluluk Içinde [Railway odaklı programlama](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) olarak adlandırılan monadıc hata işleme içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6bce9-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="6bce9-110">Aşağıdaki önemsiz örnekte bu yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bce9-110">The following trivial example demonstrates this approach.</span></span>

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

<span data-ttu-id="6bce9-111">Görebileceğiniz gibi, tümünün bir `Result`döndürmesini zorlarsanız, çeşitli doğrulama işlevlerini birbirine kolayca zincirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bce9-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="6bce9-112">Bu, bunun gibi işlevleri, sizin için gerekli olduğu kadar birleştirilebilen küçük parçalara bölmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6bce9-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="6bce9-113">Bu Ayrıca, bir doğrulamanın sonunda, daha yüksek bir program doğruluğu uygulayan, bir doğrulama sayısının sonunda [kalıp eşleştirmesinin](pattern-matching.md) kullanımını *zorunlu kılma* değeri de vardır.</span><span class="sxs-lookup"><span data-stu-id="6bce9-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bce9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bce9-114">See also</span></span>

- [<span data-ttu-id="6bce9-115">Ayrılmış Birleşimler</span><span class="sxs-lookup"><span data-stu-id="6bce9-115">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="6bce9-116">Desen Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="6bce9-116">Pattern Matching</span></span>](pattern-matching.md)
