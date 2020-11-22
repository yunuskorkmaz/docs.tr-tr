---
title: Dilimler
description: 'Mevcut F # veri türleri için dilimleri kullanmayı ve diğer veri türleri için kendi dilimlerinizi nasıl tanımlayacağınızı öğrenin.'
ms.date: 11/20/2020
ms.openlocfilehash: 9c072648ed46ae29871f2be5cc64b493f6a9b857
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098963"
---
# <a name="slices"></a>Dilimler

Bu makalede, var olan F # türlerinden dilimlerin nasıl yapılacağı ve kendi dilimlerinizi nasıl tanımlayabileceğiniz açıklanır.

F # ' da, dilim herhangi bir veri türünün alt kümesidir.  Dilimler, [Dizin oluşturuculardan](./members/indexed-properties.md)benzerdir, ancak temel alınan veri yapısından tek bir değer vermek yerine birden çok tane oluşur. Dilimler, `..` bir veri türünde belirtilen dizinlerin aralığını seçmek için işleç sözdizimini kullanır. Daha fazla bilgi için bkz. [döngü ifadesi başvuru makalesi](./loops-for-in-expression.md).

F # Şu anda Dilimleme dizeleri, listeler, diziler ve çok boyutlu (2B, 3B, 4D) diziler için iç destek içerir. Dilimleme en yaygın olarak F # dizileri ve listeleriyle kullanılır. `GetSlice`Tür tanımınızda veya kapsam içi bir [tür uzantısında](type-extensions.md)yöntemi kullanarak özel veri türlerinizi Dilimleme ekleyebilirsiniz.

## <a name="slicing-f-lists-and-arrays"></a>F # listelerini ve dizilerini Dilimleme

Dilimlenmiş en yaygın veri türleri, F # listeleri ve dizilerdir.  Aşağıdaki örnek, listelerin nasıl dilimleyeceğinizi göstermektedir:

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

F #, F # Çekirdek kitaplığındaki çok boyutlu dizileri destekler. Tek boyutlu diziler gibi çok boyutlu dizilerin dilimleri de yararlı olabilir. Bununla birlikte, belirli satır ve sütun dilimlerini alabilmeniz için ek boyutların giriş, biraz farklı bir sözdizimi alır.

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

## <a name="defining-slices-for-other-data-structures"></a>Diğer veri yapıları için dilimleri tanımlama

F # Çekirdek Kitaplığı, sınırlı bir tür kümesi için dilimleri tanımlar. Daha fazla veri türü için dilimleri tanımlamak isterseniz, tür tanımının kendisinde veya bir tür uzantısında bunu yapabilirsiniz.

Örneğin, <xref:System.ArraySegment%601> uygun veri işlemeye izin vermek için sınıfı için dilimleri nasıl tanımlayacağınızı aşağıda bulabilirsiniz:

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

Ve türlerini kullanan başka bir örnek <xref:System.Span%601> <xref:System.ReadOnlySpan%601> :

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
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
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a>Yerleşik F # dilimleri uçtan uca

F # içindeki tüm iç dilimler son kapsamlı; diğer bir deyişle, üst sınır dilimde yer alır. Başlangıç dizini ve bitiş dizinini içeren belirli bir dilim için `x` `y` , sonuçta elde edilen dilim, son *yth* değeri içerecektir.

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a>Yerleşik F # boş dilimler

F # listeleri, diziler, sıralar, dizeler, çok boyutlu (2B, 3B, 4D) diziler, sözdizimi mevcut olmayan bir dilim üretemedi boş bir dilim üretir.

Aşağıdaki örneği inceleyin:

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

> [!IMPORTANT]
> C# geliştiricileri, bunları boş bir dilim oluşturmak yerine bir özel durum oluşturması için bekleyebilir. Bu, boş koleksiyonların F # ' ta bir olgusuna göre belirtilmiş bir tasarım karardır. Boş bir F # listesi, başka bir F # listesiyle birleştirilebilir, var olan bir dizeye boş bir dize eklenebilir ve bu şekilde devam eder. Parametre olarak geçirilen değerlere bağlı olarak dilimleri almak ve boş bir koleksiyon, F # kodunun kompozisyonu ile uyumlu hale getirerek sınır dışı > dayanıklı olması çok yaygın olabilir.

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a>3B ve 4D dizileri için sabit Dizin dilimleri

F # 3D ve 4D dizileri için, belirli bir dizini "düzeltir" ve diğer boyutları, bu dizinle sabitleyecek şekilde dilimleyin.

Bunu göstermek için aşağıdaki 3B diziyi göz önünde bulundurun:

*z = 0*

| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*

| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

Dilimi diziden ayıklamak istiyorsanız `[| 4; 5 |]` , sabit Dizin dilimi kullanın.

```fsharp
let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

Son satır `y` `z` 3B dizisinin ve dizinlerini düzeltir ve `x` matriste karşılık gelen değerleri geri alır.

## <a name="see-also"></a>Ayrıca bkz.

- [Dizinli Özellikler](./members/indexed-properties.md)
