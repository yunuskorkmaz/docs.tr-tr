---
title: Sonuçlar
description: Nasıl kullanacağınızı öğrenin F# hataya dayanıklı kod yazmanıza yardımcı olmak için 'Result' yazın.
ms.date: 04/24/2017
ms.openlocfilehash: 36f60df8a2991c1d318e4921af6c9e89a0156918
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645316"
---
# <a name="results"></a>Sonuçlar

İle başlayarak F# 4.1, var olan bir `Result<'T,'TFailure>` kullanılıp kullanılamayacağı hataya dayanıklı kod yazmak için kullanabileceğiniz türü.

## <a name="syntax"></a>Sözdizimi

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

Sonuç türü olduğuna dikkat edin bir [ayırt edici birleşim](discriminated-unions.md#struct-discriminated-unions), hangi içinde başka bir özellik sunulmuştur F# 4.1.  Yapısal eşitlik semantiği burada geçerli olur.

`Result` Türü genellikle birli hata genellikle olarak adlandırılan işleme, kullanılan [demiryolu yönelimli programlama](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) içinde F# topluluğu.  Aşağıdaki basit örnekte, bu yaklaşım gösterilmektedir.

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

Gördüğünüz gibi çeşitli doğrulama işlevleri tümünü döndürülecek zorlarsanız zincir oldukça kolay bir `Result`.  Böyle bir işlevsellik olması gerektiği gibi birleştirilebilir küçük parçalara bölmeniz olanak sağlar.  Bu da eklenen değerine sahip *zorlamayı* kullanımını [desen eşleştirme](pattern-matching.md) doğrulama turu sonunda, hangi sırayla zorlar daha yüksek bir program doğruluk derecesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrılmış Birleşimler](discriminated-unions.md)
- [Desen Eşleştirme](pattern-matching.md)
