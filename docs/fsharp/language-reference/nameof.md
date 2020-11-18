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
# <a name="nameof"></a>NameOf

`nameof`İfade, kaynaktaki neredeyse tüm F # yapısı için kaynaktaki adla eşleşen bir dize sabiti oluşturur.

## <a name="syntax"></a>Syntax

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a>Açıklamalar

`nameof` kendisine geçirilen simgeyi çözümleyerek ve kaynak kodunuzda bildirildiği için bu sembolün adını üreten işe yarar. Bu, günlüğe kaydetme gibi çeşitli senaryolarda faydalıdır ve günlüğe kaydetme işleminin kaynak kodundaki değişikliklere karşı korunmasını sağlar.

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

Son satır bir özel durum oluşturur ve `"month"` hata iletisinde gösterilir.

Neredeyse her F # yapısının adını alabilirsiniz:

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

`nameof` Birinci sınıf bir işlev değildir ve bu şekilde kullanılamaz. Bu, kısmen uygulanamadığından ve değerler F # ardışık düzen işleçleri yoluyla buna çıkarılamıyor.

## <a name="nameof-on-operators"></a>Of işleçleri için NameOf

F # içindeki işleçler iki şekilde, bir operatör metninin kendisi olarak veya derlenen formu temsil eden bir sembol ile kullanılabilir. `nameof` bir işleçte, kaynak içinde bildirildiği gibi işlecin adını üretir. Derlenen adı almak için, kaynakta derlenen adı kullanın:

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a>Genel türlerde NameOf

Genel tür parametresinin adını da alabilirsiniz, ancak sözdizimi farklıdır:

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

`nameof<'TGeneric>` , bir çağrı sitesinde değiştirilen türün adı değil, sembolün adını kaynak bölümünde tanımlanan şekilde alır.

Sözdiziminin farklı olmasının nedeni, ve gibi diğer F # içsel işleçlerle hizalanmasıdır `typeof<>` `typedefof<>` . Bu, genel türler üzerinde ve kaynak üzerinde başka her şey üzerinde işlem yapan işleçlere göre F # tutarlılığını sağlar.

## <a name="nameof-in-pattern-matching"></a>Model eşleştirme içindeki NameOf

Bu [ `nameof` model](pattern-matching.md#nameof-pattern) , `nameof` şöyle bir model eşleşme ifadesinde kullanmanıza olanak sağlar:

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
