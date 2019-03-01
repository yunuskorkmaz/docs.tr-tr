---
title: Dilim (F#)
description: Varolan dilimleri kullanma hakkında bilgi edinin F# veri türleri ve diğer veri türleri için kendi dilim tanımlama.
ms.date: 01/22/2019
ms.openlocfilehash: 60b57d4eea40bb26dc43d8255dd933b63ac6303c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970121"
---
# <a name="slices"></a><span data-ttu-id="9f5cd-103">Dilimler</span><span class="sxs-lookup"><span data-stu-id="9f5cd-103">Slices</span></span>

<span data-ttu-id="9f5cd-104">İçinde F#, bir dilim bir veri türü bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="9f5cd-105">Bir veri türünden bir dilim yararlanabilmeniz için veri türü ya da tanımlamanız gerekir bir `GetSlice` yöntemi veya bir [türü uzantısı](type-extensions.md) diğer bir deyişle kapsamda.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="9f5cd-106">Bu makalede, mevcut dilimleri gerçekleştirilecek açıklanmaktadır F# türlerini ve nasıl kendi ölçümünüzü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="9f5cd-107">Dilimler benzer [dizin oluşturucular](members/indexed-properties.md), ancak temel alınan veri yapısından tek bir değer sonuçlanmıyor yerine, bunlar birden fazla yield.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-107">Slices are similar to [indexers](members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="9f5cd-108">F#şu anda dizeleri, listeler, diziler ve 2B bir dizi dilimleme iç desteği yok.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="9f5cd-109">İle temel dilimleme F# listeler ve diziler</span><span class="sxs-lookup"><span data-stu-id="9f5cd-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="9f5cd-110">Dilimlenmiş en yaygın veri türleridir F# listeler ve diziler.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="9f5cd-111">Aşağıdaki örnek, bu listeleri ile bunu nasıl yapacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f5cd-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="9f5cd-112">Dizi dilimleme listeleri yalnızca dilimleme gibi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9f5cd-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="9f5cd-113">Dilimleme çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="9f5cd-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="9f5cd-114">F#çok boyutlu dizilerde destekler F# çekirdek kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="9f5cd-115">Tek boyutlu dizilerle gibi çok boyutlu diziler dilimleri da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="9f5cd-116">Ancak, belirli satırları ve sütunları dilimleri yararlanabilmeniz ek boyutlar sunulmasıyla biraz farklı bir sözdizimi zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="9f5cd-117">Aşağıdaki örnekler, 2B bir dizi dilimleme göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9f5cd-117">The following examples demonstrate how to slice a 2D array:</span></span>

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
printfn "%A" twobyTwo
```

<span data-ttu-id="9f5cd-118">F# Çekirdek kitaplığı tanımlamıyor `GetSlice`3B diziler için.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="9f5cd-119">Bu veya daha fazla boyutlarının diğer diziler dilim istiyorsanız tanımlamalıdır `GetSlice` üye kendiniz.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="9f5cd-120">Diğer veri yapılarını dilimleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="9f5cd-120">Defining slices for other data structures</span></span>

<span data-ttu-id="9f5cd-121">F# Çekirdek kitaplığı dilimler sınırlı sayıda türleri için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="9f5cd-122">Daha fazla veri türleri için dilim tanımlamak istiyorsanız, tür tanımını kendisi veya bir tür uzantısında bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="9f5cd-123">Örneğin, işte dilimleri nasıl tanımlayabilir <xref:System.ArraySegment%601> sınıfı için uygun veri işlemesine izin vermek için:</span><span class="sxs-lookup"><span data-stu-id="9f5cd-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="9f5cd-124">Satır içi kullanım gerekli değilse, kutulama önlemek için kullanın</span><span class="sxs-lookup"><span data-stu-id="9f5cd-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="9f5cd-125">Aslında bir yapı türü dilimleri tanımlıyorsanız, öneririz, `inline` `GetSlice` üyesi.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="9f5cd-126">F# Derleyici dilimleme sonucunda herhangi bir yığın ayırma önleme isteğe bağlı bağımsız değişkenler yerine iyileştirir.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="9f5cd-127">Bu yapılar gibi dilimleme için kritik öneme <xref:System.Span%601> yığınında ayrılamaz.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9f5cd-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f5cd-128">See also</span></span>

- [<span data-ttu-id="9f5cd-129">Dizini oluşturulan özellikler</span><span class="sxs-lookup"><span data-stu-id="9f5cd-129">Indexed properties</span></span>](members/indexed-properties.md)
