---
title: Dilimler (F#)
description: Mevcut F# veri türleri için dilimleri kullanma ve diğer veri türleri için kendi dilimlerinizi tanımlama hakkında bilgi edinin.
ms.date: 01/22/2019
ms.openlocfilehash: cbff1b055ea99ef708f9db191be49275e630ee90
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798911"
---
# <a name="slices"></a><span data-ttu-id="9b50d-103">Dilimler</span><span class="sxs-lookup"><span data-stu-id="9b50d-103">Slices</span></span>

<span data-ttu-id="9b50d-104">' F#De, bir dilim veri türünün bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="9b50d-105">Veri türünün bir dilimini alabilmesi için, veri türü bir `GetSlice` yöntemi ya da kapsam içinde olan bir [tür uzantısı](type-extensions.md) içinde tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b50d-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="9b50d-106">Bu makalede, mevcut F# türlerden dilimlerin nasıl alınacağını ve kendinizinkini nasıl tanımlayabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="9b50d-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="9b50d-107">Dilimler, [Dizin oluşturuculardan](./members/indexed-properties.md)benzerdir, ancak temel alınan veri yapısından tek bir değer vermek yerine birden çok tane oluşur.</span><span class="sxs-lookup"><span data-stu-id="9b50d-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="9b50d-108">F#Şu anda, Dilimleme dizeleri, listeler, diziler ve 2B diziler için iç destek içerir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="9b50d-109">F# Listelerle ve dizilerle temel Dilimleme</span><span class="sxs-lookup"><span data-stu-id="9b50d-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="9b50d-110">Dilimlenmiş en yaygın veri türleri F# listeler ve dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="9b50d-111">Aşağıdaki örnek, listenin nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9b50d-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="9b50d-112">Dizileri dilimleme, yalnızca Dilimleme listelerine benzer:</span><span class="sxs-lookup"><span data-stu-id="9b50d-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="9b50d-113">Çok boyutlu dizileri Dilimleme</span><span class="sxs-lookup"><span data-stu-id="9b50d-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="9b50d-114">F#F# çekirdek kitaplıkta çok boyutlu dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="9b50d-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="9b50d-115">Tek boyutlu diziler gibi çok boyutlu dizilerin dilimleri de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="9b50d-116">Bununla birlikte, belirli satır ve sütun dilimlerini alabilmeniz için ek boyutların giriş, biraz farklı bir sözdizimi alır.</span><span class="sxs-lookup"><span data-stu-id="9b50d-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="9b50d-117">Aşağıdaki örneklerde bir 2B dizisinin nasıl dilimlenme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9b50d-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="9b50d-118">Çekirdek F# kitaplık, 3B diziler için`GetSlice`tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9b50d-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="9b50d-119">Daha fazla boyut için bu veya diğer dizileri dilimlemek istiyorsanız `GetSlice` üyesini kendiniz tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="9b50d-120">Diğer veri yapıları için dilimleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="9b50d-120">Defining slices for other data structures</span></span>

<span data-ttu-id="9b50d-121">Çekirdek F# kitaplık, sınırlı bir tür kümesi için dilimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9b50d-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="9b50d-122">Daha fazla veri türü için dilimleri tanımlamak isterseniz, tür tanımının kendisinde veya bir tür uzantısında bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b50d-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="9b50d-123">Örneğin, uygun veri işlemeye izin vermek için <xref:System.ArraySegment%601> sınıfı için dilimleri nasıl tanımlayacağınızı aşağıda bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9b50d-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="9b50d-124">Gerekirse kutulamayı önlemek için satır içi kullanın</span><span class="sxs-lookup"><span data-stu-id="9b50d-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="9b50d-125">Aslında bir struct olan bir tür için dilim tanımlıyorsanız `GetSlice` üyesini `inline` öneririz.</span><span class="sxs-lookup"><span data-stu-id="9b50d-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="9b50d-126">F# Derleyici, Dilimleme sonucu olarak herhangi bir yığın ayırmasını önleyerek isteğe bağlı bağımsız değişkenleri en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="9b50d-127">Bu, yığında ayrılabilen <xref:System.Span%601> gibi Dilimleme yapıları için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9b50d-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9b50d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b50d-128">See also</span></span>

- [<span data-ttu-id="9b50d-129">Dizinli Özellikler</span><span class="sxs-lookup"><span data-stu-id="9b50d-129">Indexed properties</span></span>](./members/indexed-properties.md)
