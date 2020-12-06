---
title: Sonuçlar
description: "F # ' Result ' türünün, hataya dayanıklı kod yazmanıza yardımcı olması için nasıl kullanılacağını öğrenin."
ms.date: 08/13/2020
ms.openlocfilehash: 53b1db0c9224ae032d58c06cd3c58e3dbed03f7b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740230"
---
# <a name="results"></a>Sonuçlar

`Result<'T,'TFailure>`Türü, birleştirilebilen hataya dayanıklı kod yazmanızı sağlar.

## <a name="syntax"></a>Syntax

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Açıklamalar

[`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html)İçin yerleşik kombinatör modülüne bakın `Result` . türüyle.

Sonuç türünün bir [struct ayrılmış birleşim](discriminated-unions.md#struct-discriminated-unions)olduğunu unutmayın. Yapısal eşitlik semantiği burada geçerlidir.

`Result`Tür genellikle F # Community Içinde [Railway odaklı programlama](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) olarak adlandırılan monmonotik hata işleme içinde kullanılır.  Aşağıdaki önemsiz örnekte bu yaklaşım gösterilmektedir.

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
    | Ok req -> printfn $"My request was valid! Name: {req.Name} Email {req.Email}"  
    | Error e -> printfn $"Error: {e}"
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn $"My request was valid! Name: {req.Name} Email {req.Email}"  
    | Error e -> printfn $"Error: {e}"
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

Görebileceğiniz gibi, tümünün bir döndürmesini zorlarsanız, çeşitli doğrulama işlevlerini birbirine kolayca zincirleyebilirsiniz `Result` .  Bu, bunun gibi işlevleri, sizin için gerekli olduğu kadar birleştirilebilen küçük parçalara bölmenize olanak tanır.  Bu Ayrıca, bir doğrulamanın sonunda, daha yüksek bir program doğruluğu uygulayan, bir doğrulama sayısının sonunda [kalıp eşleştirmesinin](pattern-matching.md) kullanımını *zorunlu kılma* değeri de vardır.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrılmış Birleşimler](discriminated-unions.md)
- [Desen Eşleştirme](pattern-matching.md)
