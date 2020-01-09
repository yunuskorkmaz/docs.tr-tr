---
title: Dilimler
description: Mevcut F# veri türleri için dilimleri kullanmayı ve diğer veri türleri için kendi dilimlerinizi nasıl tanımlayacağınızı öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: 3911139c7ce656043817eb23d30f3686555b6efe
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545107"
---
# <a name="slices"></a>Dilimler

' F#De, bir dilim, tanımında veya kapsam içi [tür uzantısında](type-extensions.md)`GetSlice` yöntemi olan herhangi bir veri türünün alt kümesidir. En yaygın olarak F# diziler ve listelerle kullanılır. Bu makalede, mevcut F# türlerden dilimlerin nasıl yapılacağı ve kendi dilimlerinizi nasıl tanımlayabileceğiniz açıklanır.

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

F# Çekirdek kitaplık Şu anda 3B diziler için `GetSlice` tanımlamıyor. 3B dizilerini veya daha fazla boyutun diğer dizilerini dilimlemek isterseniz, `GetSlice` üyesini kendiniz tanımlayın.

## <a name="defining-slices-for-other-data-structures"></a>Diğer veri yapıları için dilimleri tanımlama

Çekirdek F# kitaplık, sınırlı bir tür kümesi için dilimleri tanımlar. Daha fazla veri türü için dilimleri tanımlamak isterseniz, tür tanımının kendisinde veya bir tür uzantısında bunu yapabilirsiniz.

Örneğin, uygun veri işlemeye izin vermek için <xref:System.ArraySegment%601> sınıfı için dilimleri nasıl tanımlayacağınızı aşağıda bulabilirsiniz:

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Gerekirse kutulamayı önlemek için satır içi kullanın

Aslında bir struct olan bir tür için dilim tanımlıyorsanız `GetSlice` üyesini `inline` öneririz. F# Derleyici, Dilimleme sonucu olarak herhangi bir yığın ayırmasını önleyerek isteğe bağlı bağımsız değişkenleri en iyi duruma getirir. Bu, yığında ayrılabilen <xref:System.Span%601> gibi Dilimleme yapıları için kritik öneme sahiptir.

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a>Yerleşik F# dilimler son kapsamlı

İçindeki F# tüm iç dilimler uçtan uca; diğer bir deyişle, üst sınır dilimde yer alır. Dizin `x` başlayan ve Dizin `y`biten belirli bir dilim için, sonuçta elde edilen dilim *Bu değeri içerir* .

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a>Ayrıca bkz.

- [Dizinli Özellikler](./members/indexed-properties.md)
