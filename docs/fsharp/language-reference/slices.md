---
title: Dilimler
description: Mevcut F# veri türleri için dilimleri kullanmayı ve diğer veri türleri için kendi dilimlerinizi nasıl tanımlayacağınızı öğrenin.
ms.date: 12/23/2019
ms.openlocfilehash: 928005f2c63ffe099bb64e11ed29bb625e0a54c6
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980385"
---
# <a name="slices"></a><span data-ttu-id="fec98-103">Dilimler</span><span class="sxs-lookup"><span data-stu-id="fec98-103">Slices</span></span>

<span data-ttu-id="fec98-104">' F#De, bir dilim, tanımında veya kapsam içi [tür uzantısında](type-extensions.md)`GetSlice` yöntemi olan herhangi bir veri türünün alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="fec98-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="fec98-105">En yaygın olarak F# diziler ve listelerle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fec98-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="fec98-106">Bu makalede, mevcut F# türlerden dilimlerin nasıl yapılacağı ve kendi dilimlerinizi nasıl tanımlayabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fec98-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="fec98-107">Dilimler, [Dizin oluşturuculardan](./members/indexed-properties.md)benzerdir, ancak temel alınan veri yapısından tek bir değer vermek yerine birden çok tane oluşur.</span><span class="sxs-lookup"><span data-stu-id="fec98-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="fec98-108">F#Şu anda, Dilimleme dizeleri, listeler, diziler ve 2B diziler için iç destek içerir.</span><span class="sxs-lookup"><span data-stu-id="fec98-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="fec98-109">F# Listelerle ve dizilerle temel Dilimleme</span><span class="sxs-lookup"><span data-stu-id="fec98-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="fec98-110">Dilimlenmiş en yaygın veri türleri F# listeler ve dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="fec98-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="fec98-111">Aşağıdaki örnek, listenin nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fec98-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="fec98-112">Dizileri dilimleme, yalnızca Dilimleme listelerine benzer:</span><span class="sxs-lookup"><span data-stu-id="fec98-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="fec98-113">Çok boyutlu dizileri Dilimleme</span><span class="sxs-lookup"><span data-stu-id="fec98-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="fec98-114">F#F# çekirdek kitaplıkta çok boyutlu dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="fec98-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="fec98-115">Tek boyutlu diziler gibi çok boyutlu dizilerin dilimleri de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fec98-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="fec98-116">Bununla birlikte, belirli satır ve sütun dilimlerini alabilmeniz için ek boyutların giriş, biraz farklı bir sözdizimi alır.</span><span class="sxs-lookup"><span data-stu-id="fec98-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="fec98-117">Aşağıdaki örneklerde bir 2B dizisinin nasıl dilimlenme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="fec98-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="fec98-118">F# Çekirdek kitaplık Şu anda 3B diziler için `GetSlice` tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="fec98-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="fec98-119">3B dizilerini veya daha fazla boyutun diğer dizilerini dilimlemek isterseniz, `GetSlice` üyesini kendiniz tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="fec98-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="fec98-120">Diğer veri yapıları için dilimleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="fec98-120">Defining slices for other data structures</span></span>

<span data-ttu-id="fec98-121">Çekirdek F# kitaplık, sınırlı bir tür kümesi için dilimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fec98-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="fec98-122">Daha fazla veri türü için dilimleri tanımlamak isterseniz, tür tanımının kendisinde veya bir tür uzantısında bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fec98-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="fec98-123">Örneğin, uygun veri işlemeye izin vermek için <xref:System.ArraySegment%601> sınıfı için dilimleri nasıl tanımlayacağınızı aşağıda bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fec98-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="fec98-124">Gerekirse kutulamayı önlemek için satır içi kullanın</span><span class="sxs-lookup"><span data-stu-id="fec98-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="fec98-125">Aslında bir struct olan bir tür için dilim tanımlıyorsanız `GetSlice` üyesini `inline` öneririz.</span><span class="sxs-lookup"><span data-stu-id="fec98-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="fec98-126">F# Derleyici, Dilimleme sonucu olarak herhangi bir yığın ayırmasını önleyerek isteğe bağlı bağımsız değişkenleri en iyi duruma getirir.</span><span class="sxs-lookup"><span data-stu-id="fec98-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="fec98-127">Bu, yığında ayrılabilen <xref:System.Span%601> gibi Dilimleme yapıları için kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fec98-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
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
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="fec98-128">Yerleşik F# dilimler son kapsamlı</span><span class="sxs-lookup"><span data-stu-id="fec98-128">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="fec98-129">İçindeki F# tüm iç dilimler uçtan uca; diğer bir deyişle, üst sınır dilimde yer alır.</span><span class="sxs-lookup"><span data-stu-id="fec98-129">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="fec98-130">Dizin `x` başlayan ve Dizin `y`biten belirli bir dilim için, sonuçta elde edilen dilim *Bu değeri içerir* .</span><span class="sxs-lookup"><span data-stu-id="fec98-130">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="fec98-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fec98-131">See also</span></span>

- [<span data-ttu-id="fec98-132">Dizinli Özellikler</span><span class="sxs-lookup"><span data-stu-id="fec98-132">Indexed properties</span></span>](./members/indexed-properties.md)
