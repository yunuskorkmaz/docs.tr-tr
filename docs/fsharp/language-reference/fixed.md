---
title: "Sabit anahtar sözcüğü (F #)"
description: "'Sabitleyebilir nasıl' ile F # koleksiyon önlemek için bir yerel yığına 'anahtar sözcüğü sabit' öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5795ce1f-11bf-4798-9f1f-6e44ffa1477e
ms.openlocfilehash: 1605603bc35941e21c798600140036fb678869b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="the-fixed-keyword"></a>Sabit anahtar sözcüğü

F # 4.1 tanıtır `fixed` anahtar sözcüğü "toplanan veya çöp toplama sırasında taşınmış önlemek için bir yerel yığına sabitlemek" sağlar.  Alt düzey programlama senaryolar için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Açıklamalar

Bu işaretçi ayıklanması ve toplanan veya çöp toplama sırasında taşınmış engelleyen bir adı bağlama izin ifadenin sözdizimi genişletir.  

Bir ifade işaretçi aracılığıyla sabit `fixed` anahtar sözcüğü bir tanımlayıcıya bağlı `use` anahtar sözcüğü.  Bu semantiği kaynak yönetimi benzer `use` anahtar sözcüğü.  İşaretçinin kapsamında olduğunu ve kapsamının dışına olduktan sonra artık sabittir düzeltilmiştir.  `fixed`bağlamı dışında kullanılamaz bir `use` bağlama.  İşaretçinin bir adla bağlamak gerekir `use`.

Kullanımı `fixed` bir ifadede bir işlev veya yöntem içinde gerçekleşmelidir.  Bir komut dosyası düzeyi veya modül düzeyi kapsamda kullanılamaz.

Tüm işaretçi kodu gibi bu güvensiz bir özelliktir ve kullanıldığında bir uyarı yayma.

## <a name="example"></a>Örnek

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>Ayrıca Bkz.

[NativePtr modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
