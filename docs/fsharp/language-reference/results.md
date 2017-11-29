---
title: "Sonuçlar (F #)"
description: "F # 'Neden' türü, hataya dayanıklı kod yazmanıza yardımcı olmak için nasıl kullanılacağını öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a15b5cf1-9055-4481-918c-4c8a051b5829
ms.openlocfilehash: 26478ccfbf88d43c0b194e77d9aacc313515283f
ms.sourcegitcommit: 8d14e8c1b15009330c9880f8523686158924e1a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2017
---
# <a name="results"></a><span data-ttu-id="914f2-104">Sonuçları</span><span class="sxs-lookup"><span data-stu-id="914f2-104">Results</span></span>

<span data-ttu-id="914f2-105">F # 4.1 ile başlayarak, var olan bir `Result<'T,'TFailure>` birleştirilebilen hataya dayanıklı kod yazmak için kullanabileceğiniz türü.</span><span class="sxs-lookup"><span data-stu-id="914f2-105">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="914f2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="914f2-106">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="914f2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="914f2-107">Remarks</span></span>

<span data-ttu-id="914f2-108">Sonuç türü olduğuna dikkat edin bir [yapısı ayrılmış birleşim](discriminated-unions.md#struct-discriminated-unions), F # 4.1 içinde sunulan başka bir özellik değil.</span><span class="sxs-lookup"><span data-stu-id="914f2-108">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="914f2-109">Yapısal eşitlik semantiği burada geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="914f2-109">Structural equality semantics apply here.</span></span>

<span data-ttu-id="914f2-110">`Result` Türü genellikle kullanılıyor birli hata hangi sıklıkta olarak adlandırılır işleme, [tren odaklı programlama](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) F # topluluk içinde.</span><span class="sxs-lookup"><span data-stu-id="914f2-110">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="914f2-111">Bu yaklaşım aşağıdaki Önemsiz örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="914f2-111">The following trivial example demonstrates this approach.</span></span>

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
    | String.Empty -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | String.Empty -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> OK req

let validateRequest reqResult =
    reqResult 
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() = 
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (OK req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req1.Name req1.Email
    | Error e -> printfn "Error: %s" e
    // Prints " "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (OK req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req1.Name req1.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="914f2-112">Gördüğünüz gibi çeşitli doğrulama işlevleri tümünü döndürülecek zorlarsanız zincir oldukça kolay hale gelir bir `Result`.</span><span class="sxs-lookup"><span data-stu-id="914f2-112">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="914f2-113">Böyle bir işlevsellik olması gerektiği gibi birleştirilebilir küçük parçalara bölmeniz bu sağlar.</span><span class="sxs-lookup"><span data-stu-id="914f2-113">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="914f2-114">Bu aynı zamanda eklenen değerine sahip *zorlamayı* kullanımını [desen eşleştirme](pattern-matching.md) hepsini doğrulama sonunda tasarrufludur zorlar daha yüksek bir program doğruluk derecesi.</span><span class="sxs-lookup"><span data-stu-id="914f2-114">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="914f2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="914f2-115">See Also</span></span>

[<span data-ttu-id="914f2-116">Ayrılmış birleşimler</span><span class="sxs-lookup"><span data-stu-id="914f2-116">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="914f2-117">Desen eşleştirme</span><span class="sxs-lookup"><span data-stu-id="914f2-117">Pattern Matching</span></span>](pattern-matching.md)
