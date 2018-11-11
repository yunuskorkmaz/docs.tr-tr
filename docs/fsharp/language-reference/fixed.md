---
title: Fixed anahtar sözcüğü (F#)
description: "'Sabitleyebilirsiniz nasıl' ile F# koleksiyon önlemek için bir yerel yığına 'anahtar sözcüğü sabit' öğrenin."
ms.date: 04/24/2017
ms.openlocfilehash: 1bf1b2ad67d2dd7f854e569cfca7c06e8aec7f4c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45624515"
---
# <a name="the-fixed-keyword"></a>Fixed anahtar sözcüğü

F# 4.1 tanıtır `fixed` ", toplanan veya çöp toplama sırasında taşınan önlemek için bir yerel yığına sabitlemek" izin veren anahtar sözcüğü.  Bu düşük düzeydeki programlama senaryoları için kullanılır.

## <a name="syntax"></a>Sözdizimi

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Açıklamalar

Bu, bir işaretçi çıkarma ve toplanan veya çöp toplama sırasında taşınan dan engelleyen bir ad bağlama izin vermek için ifadeler sözdizimi genişletir.  

Bir ifade işaretçisinden aracılığıyla sabit `fixed` anahtar sözcüğü bir tanımlayıcıya bağlı `use` anahtar sözcüğü.  Bu semantiği kaynak yönetimi benzerdir `use` anahtar sözcüğü.  İşaretçi sabit kapsamları dahilinde olması ve kapsam dışına olduktan sonra artık sabittir.  `fixed` bağlamı dışında kullanılamaz bir `use` bağlama.  İşaretçiyi bir adla bağlamanız gerekir `use`.

Kullanım `fixed` bir ifadede bir işlev veya yöntem içinde gerçekleşmelidir.  Bir komut dosyası düzeyi veya modül düzeyinde kapsamda kullanılamaz.

Tüm işaretçi kodu gibi bu güvenli olmayan bir özelliktir ve bir uyarı yayar.

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

## <a name="see-also"></a>Ayrıca bkz.

- [NativePtr modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
