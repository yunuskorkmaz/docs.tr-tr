---
title: Dilimler (F#)
description: Mevcut F# veri türleri için dilimleri kullanma ve diğer veri türleri için kendi dilimlerinizi tanımlama hakkında bilgi edinin.
ms.date: 01/22/2019
ms.openlocfilehash: 3067982c2b4249312c7e9365bbfb994be840911d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627137"
---
# <a name="slices"></a>Dilimler

' F#De, bir dilim veri türünün bir alt kümesidir. Veri türünün bir dilimini alabilmesi için, veri türü kapsam içinde olan bir `GetSlice` Yöntem ya da bir [tür uzantısı](type-extensions.md) içinde tanımlanmalıdır. Bu makalede, mevcut F# türlerden dilimlerin nasıl alınacağını ve kendinizinkini nasıl tanımlayabileceğiniz açıklanır.

Dilimler, [Dizin oluşturuculardan](./members/indexed-properties.md)benzerdir, ancak temel alınan veri yapısından tek bir değer vermek yerine birden çok tane oluşur.

F#Şu anda, Dilimleme dizeleri, listeler, diziler ve 2B diziler için iç destek içerir.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>F# Listelerle ve dizilerle temel Dilimleme

Dilimlenmiş en yaygın veri türleri F# listeler ve dizilerdir. Aşağıdaki örnek, listenin nasıl yapılacağını gösterir:

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

Dizileri dilimleme, yalnızca Dilimleme listelerine benzer:

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

## <a name="slicing-multidimensional-arrays"></a>Çok boyutlu dizileri Dilimleme

F#F# çekirdek kitaplıkta çok boyutlu dizileri destekler. Tek boyutlu diziler gibi çok boyutlu dizilerin dilimleri de yararlı olabilir. Bununla birlikte, belirli satır ve sütun dilimlerini alabilmeniz için ek boyutların giriş, biraz farklı bir sözdizimi alır.

Aşağıdaki örneklerde bir 2B dizisinin nasıl dilimlenme gösterilmektedir:

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

F# Çekirdek kitaplık 3B diziler için tanımlamaz `GetSlice`. Daha fazla boyut için bu veya diğer dizileri dilimlemek isterseniz, `GetSlice` üyeyi kendiniz tanımlamanız gerekir.

## <a name="defining-slices-for-other-data-structures"></a>Diğer veri yapıları için dilimleri tanımlama

Çekirdek F# kitaplık, sınırlı bir tür kümesi için dilimleri tanımlar. Daha fazla veri türü için dilimleri tanımlamak isterseniz, tür tanımının kendisinde veya bir tür uzantısında bunu yapabilirsiniz.

Örneğin, uygun veri işlemeye izin vermek için <xref:System.ArraySegment%601> sınıfı için dilimleri nasıl tanımlayacağınızı aşağıda bulabilirsiniz:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Gerekirse kutulamayı önlemek için satır içi kullanın

Aslında bir struct olan bir tür için dilim tanımlıyorsanız, `inline` `GetSlice` üye yapmanızı öneririz. F# Derleyici, Dilimleme sonucu olarak herhangi bir yığın ayırmasını önleyerek isteğe bağlı bağımsız değişkenleri en iyi duruma getirir. Bu, yığın üzerinde ayrılabilen gibi Dilimleme yapıları <xref:System.Span%601> için kritik öneme sahiptir.

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

- [Dizinli Özellikler](./members/indexed-properties.md)
