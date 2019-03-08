---
title: Dilim (F#)
description: Varolan dilimleri kullanma hakkında bilgi edinin F# veri türleri ve diğer veri türleri için kendi dilim tanımlama.
ms.date: 01/22/2019
ms.openlocfilehash: 1d8bb029ad18c8853ab58888959967ed279fb368
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675283"
---
# <a name="slices"></a>Dilimler

İçinde F#, bir dilim bir veri türü bir alt kümesidir. Bir veri türünden bir dilim yararlanabilmeniz için veri türü ya da tanımlamanız gerekir bir `GetSlice` yöntemi veya bir [türü uzantısı](type-extensions.md) diğer bir deyişle kapsamda. Bu makalede, mevcut dilimleri gerçekleştirilecek açıklanmaktadır F# türlerini ve nasıl kendi ölçümünüzü tanımlayın.

Dilimler benzer [dizin oluşturucular](members/indexed-properties.md), ancak temel alınan veri yapısından tek bir değer sonuçlanmıyor yerine, bunlar birden fazla yield.

F#şu anda dizeleri, listeler, diziler ve 2B bir dizi dilimleme iç desteği yok.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>İle temel dilimleme F# listeler ve diziler

Dilimlenmiş en yaygın veri türleridir F# listeler ve diziler. Aşağıdaki örnek, bu listeleri ile bunu nasıl yapacağınızı gösterir:

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

Dizi dilimleme listeleri yalnızca dilimleme gibi verilmiştir:

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a>Dilimleme çok boyutlu diziler

F#çok boyutlu dizilerde destekler F# çekirdek kitaplığı. Tek boyutlu dizilerle gibi çok boyutlu diziler dilimleri da yararlı olabilir. Ancak, belirli satırları ve sütunları dilimleri yararlanabilmeniz ek boyutlar sunulmasıyla biraz farklı bir sözdizimi zorunlu kılar.

Aşağıdaki örnekler, 2B bir dizi dilimleme göstermektedir:

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

F# Çekirdek kitaplığı tanımlamıyor `GetSlice`3B diziler için. Bu veya daha fazla boyutlarının diğer diziler dilim istiyorsanız tanımlamalıdır `GetSlice` üye kendiniz.

## <a name="defining-slices-for-other-data-structures"></a>Diğer veri yapılarını dilimleri tanımlama

F# Çekirdek kitaplığı dilimler sınırlı sayıda türleri için tanımlar. Daha fazla veri türleri için dilim tanımlamak istiyorsanız, tür tanımını kendisi veya bir tür uzantısında bunu yapabilirsiniz.

Örneğin, işte dilimleri nasıl tanımlayabilir <xref:System.ArraySegment%601> sınıfı için uygun veri işlemesine izin vermek için:

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Satır içi kullanım gerekli değilse, kutulama önlemek için kullanın

Aslında bir yapı türü dilimleri tanımlıyorsanız, öneririz, `inline` `GetSlice` üyesi. F# Derleyici dilimleme sonucunda herhangi bir yığın ayırma önleme isteğe bağlı bağımsız değişkenler yerine iyileştirir. Bu yapılar gibi dilimleme için kritik öneme <xref:System.Span%601> yığınında ayrılamaz.

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a>Ayrıca bkz.

- [Dizini oluşturulan özellikler](members/indexed-properties.md)
