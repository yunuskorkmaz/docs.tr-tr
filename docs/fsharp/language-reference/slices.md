---
title: Dilimler
description: 'Mevcut F # veri türleri için dilimleri kullanmayı ve diğer veri türleri için kendi dilimlerinizi nasıl tanımlayacağınızı öğrenin.'
ms.date: 12/23/2019
ms.openlocfilehash: a3920ad9e1b205b506aaee92c4606bcebf94feba
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557085"
---
# <a name="slices"></a><span data-ttu-id="5eb35-103">Dilimler</span><span class="sxs-lookup"><span data-stu-id="5eb35-103">Slices</span></span>

<span data-ttu-id="5eb35-104">F # ' da, dilim, `GetSlice` tanımında veya kapsam içi [tür uzantısında](type-extensions.md)yöntemi olan herhangi bir veri türünün bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="5eb35-105">Bu en yaygın olarak F # dizileri ve listeleri ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5eb35-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="5eb35-106">Bu makalede, var olan F # türlerinden dilimlerin nasıl yapılacağı ve kendi dilimlerinizi nasıl tanımlayabileceğiniz açıklanır.</span><span class="sxs-lookup"><span data-stu-id="5eb35-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="5eb35-107">Dilimler, [Dizin oluşturuculardan](./members/indexed-properties.md)benzerdir, ancak temel alınan veri yapısından tek bir değer vermek yerine birden çok tane oluşur.</span><span class="sxs-lookup"><span data-stu-id="5eb35-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="5eb35-108">F # Şu anda Dilimleme dizeleri, listeler, diziler ve 2B diziler için iç destek içerir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="5eb35-109">F # listeleri ve dizileri ile temel Dilimleme</span><span class="sxs-lookup"><span data-stu-id="5eb35-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="5eb35-110">Dilimlenmiş en yaygın veri türleri, F # listeleri ve dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="5eb35-111">Aşağıdaki örnek, listenin nasıl yapılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5eb35-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="5eb35-112">Dizileri dilimleme, yalnızca Dilimleme listelerine benzer:</span><span class="sxs-lookup"><span data-stu-id="5eb35-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="5eb35-113">Çok boyutlu dizileri Dilimleme</span><span class="sxs-lookup"><span data-stu-id="5eb35-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="5eb35-114">F #, F # Çekirdek kitaplığındaki çok boyutlu dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="5eb35-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="5eb35-115">Tek boyutlu diziler gibi çok boyutlu dizilerin dilimleri de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="5eb35-116">Bununla birlikte, belirli satır ve sütun dilimlerini alabilmeniz için ek boyutların giriş, biraz farklı bir sözdizimi alır.</span><span class="sxs-lookup"><span data-stu-id="5eb35-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="5eb35-117">Aşağıdaki örneklerde bir 2B dizisinin nasıl dilimlenme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5eb35-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="5eb35-118">F # Çekirdek Kitaplığı Şu anda `GetSlice` 3B diziler için tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5eb35-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="5eb35-119">3B dizilerini veya daha fazla boyutun diğer dizilerini dilimlemek isterseniz, `GetSlice` üyeyi kendiniz tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5eb35-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="5eb35-120">Diğer veri yapıları için dilimleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="5eb35-120">Defining slices for other data structures</span></span>

<span data-ttu-id="5eb35-121">F # Çekirdek Kitaplığı, sınırlı bir tür kümesi için dilimleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5eb35-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="5eb35-122">Daha fazla veri türü için dilimleri tanımlamak isterseniz, tür tanımının kendisinde veya bir tür uzantısında bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eb35-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="5eb35-123">Örneğin, <xref:System.ArraySegment%601> uygun veri işlemeye izin vermek için sınıfı için dilimleri nasıl tanımlayacağınızı aşağıda bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5eb35-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="5eb35-124">Ve türlerini kullanan başka bir örnek <xref:System.Span%601> <xref:System.ReadOnlySpan%601> :</span><span class="sxs-lookup"><span data-stu-id="5eb35-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

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

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="5eb35-125">Yerleşik F # dilimleri uçtan uca</span><span class="sxs-lookup"><span data-stu-id="5eb35-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="5eb35-126">F # içindeki tüm iç dilimler son kapsamlı; diğer bir deyişle, üst sınır dilimde yer alır.</span><span class="sxs-lookup"><span data-stu-id="5eb35-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="5eb35-127">Başlangıç dizini ve bitiş dizinini içeren belirli bir dilim için `x` `y` , sonuçta elde edilen dilim, son *yth* değeri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="5eb35-128">Yerleşik F # boş dilimler</span><span class="sxs-lookup"><span data-stu-id="5eb35-128">Built-in F# empty slices</span></span>

<span data-ttu-id="5eb35-129">Sözdizimi mevcut olmayan bir dilim oluşturamazsa, F # listeleri, diziler, sıralar, dizeler, 2B diziler, 3B diziler ve 4D dizileri hepsi boş bir dilim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5eb35-129">F# lists, arrays, sequences, strings, 2D arrays, 3D arrays, and 4D arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="5eb35-130">Aşağıdaki topluluklara bir göz atın:</span><span class="sxs-lookup"><span data-stu-id="5eb35-130">Consider the following:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

<span data-ttu-id="5eb35-131">C# geliştiricileri, bunları boş bir dilim oluşturmak yerine bir özel durum oluşturması için bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-131">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="5eb35-132">Bu, boş koleksiyonların F # ' ta bir olgusuna göre belirtilmiş bir tasarım karardır.</span><span class="sxs-lookup"><span data-stu-id="5eb35-132">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="5eb35-133">Boş bir F # listesi, başka bir F # listesiyle birleştirilebilir, var olan bir dizeye boş bir dize eklenebilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="5eb35-133">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="5eb35-134">Bu, parametre olarak geçirilen değerlere göre dilimler almak ve boş bir koleksiyon üreterek, F # kodunun kompozisyonu ile uyumlu olacak şekilde dilimlerden yararlanmak için ortak olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eb35-134">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="5eb35-135">3B ve 4D dizileri için sabit Dizin dilimleri</span><span class="sxs-lookup"><span data-stu-id="5eb35-135">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="5eb35-136">F # 3D ve 4D dizileri için, belirli bir dizini "düzeltir" ve diğer boyutları, bu dizinle sabitleyecek şekilde dilimleyin.</span><span class="sxs-lookup"><span data-stu-id="5eb35-136">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="5eb35-137">Bunu göstermek için aşağıdaki 3B diziyi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="5eb35-137">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="5eb35-138">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="5eb35-138">*z = 0*</span></span>
| <span data-ttu-id="5eb35-139">x\y</span><span class="sxs-lookup"><span data-stu-id="5eb35-139">x\y</span></span>   | <span data-ttu-id="5eb35-140">0</span><span class="sxs-lookup"><span data-stu-id="5eb35-140">0</span></span> | <span data-ttu-id="5eb35-141">1</span><span class="sxs-lookup"><span data-stu-id="5eb35-141">1</span></span> |
|-------|---|---|
| <span data-ttu-id="5eb35-142">**0**</span><span class="sxs-lookup"><span data-stu-id="5eb35-142">**0**</span></span> | <span data-ttu-id="5eb35-143">0</span><span class="sxs-lookup"><span data-stu-id="5eb35-143">0</span></span> | <span data-ttu-id="5eb35-144">1</span><span class="sxs-lookup"><span data-stu-id="5eb35-144">1</span></span> |
| <span data-ttu-id="5eb35-145">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb35-145">**1**</span></span> | <span data-ttu-id="5eb35-146">2</span><span class="sxs-lookup"><span data-stu-id="5eb35-146">2</span></span> | <span data-ttu-id="5eb35-147">3</span><span class="sxs-lookup"><span data-stu-id="5eb35-147">3</span></span> |

<span data-ttu-id="5eb35-148">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="5eb35-148">*z = 1*</span></span>
| <span data-ttu-id="5eb35-149">x\y</span><span class="sxs-lookup"><span data-stu-id="5eb35-149">x\y</span></span>   | <span data-ttu-id="5eb35-150">0</span><span class="sxs-lookup"><span data-stu-id="5eb35-150">0</span></span> | <span data-ttu-id="5eb35-151">1</span><span class="sxs-lookup"><span data-stu-id="5eb35-151">1</span></span> |
|-------|---|---|
| <span data-ttu-id="5eb35-152">**0**</span><span class="sxs-lookup"><span data-stu-id="5eb35-152">**0**</span></span> | <span data-ttu-id="5eb35-153">4</span><span class="sxs-lookup"><span data-stu-id="5eb35-153">4</span></span> | <span data-ttu-id="5eb35-154">5</span><span class="sxs-lookup"><span data-stu-id="5eb35-154">5</span></span> |
| <span data-ttu-id="5eb35-155">**1**</span><span class="sxs-lookup"><span data-stu-id="5eb35-155">**1**</span></span> | <span data-ttu-id="5eb35-156">6</span><span class="sxs-lookup"><span data-stu-id="5eb35-156">6</span></span> | <span data-ttu-id="5eb35-157">7</span><span class="sxs-lookup"><span data-stu-id="5eb35-157">7</span></span> |

<span data-ttu-id="5eb35-158">Dilimi diziden ayıklamak istiyorsanız `[| 4; 5 |]` , sabit Dizin dilimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5eb35-158">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

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

<span data-ttu-id="5eb35-159">Son satır, `y` `z` 3B dizisinin ve bunların özetini düzeltir ve `x` matriste karşılık gelen değerleri geri alır.</span><span class="sxs-lookup"><span data-stu-id="5eb35-159">The last line fixes the `y` and `z` indicies of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eb35-160">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eb35-160">See also</span></span>

- [<span data-ttu-id="5eb35-161">Dizinli Özellikler</span><span class="sxs-lookup"><span data-stu-id="5eb35-161">Indexed properties</span></span>](./members/indexed-properties.md)
