---
title: Diziler
description: 'F # programlama dilinde dizileri oluşturmayı ve kullanmayı öğrenin.'
ms.date: 08/13/2020
ms.openlocfilehash: 37f781ccd2c7bc2ca2c7b93bda53bbb3ea93b504
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608501"
---
# <a name="arrays"></a><span data-ttu-id="bf3a8-103">Diziler</span><span class="sxs-lookup"><span data-stu-id="bf3a8-103">Arrays</span></span>

<span data-ttu-id="bf3a8-104">Diziler, aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı ve değişebilir koleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="bf3a8-105">Dizi oluştur</span><span class="sxs-lookup"><span data-stu-id="bf3a8-105">Create arrays</span></span>

<span data-ttu-id="bf3a8-106">Çeşitli yollarla diziler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-106">You can create arrays in several ways.</span></span> <span data-ttu-id="bf3a8-107">`[|` `|]` Aşağıdaki örneklerde gösterildiği gibi, ve arasında ardışık değerleri noktalı virgülle ayırarak küçük bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="bf3a8-108">Ayrıca her öğeyi ayrı bir satıra koyabilirsiniz, bu durumda noktalı virgül ayırıcı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="bf3a8-109">Dizi öğelerinin türü, kullanılan değişmez değerlerden çıkarılan ve tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="bf3a8-110">Aşağıdaki kod bir hataya neden olur, çünkü 1,0 bir float ve 2 ve 3 tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="bf3a8-111">Diziler oluşturmak için dizi ifadelerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="bf3a8-112">Aşağıda, 1 ile 10 arasında bir tamsayı kare dizisi oluşturan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="bf3a8-113">Tüm öğelerin sıfıra başlatıldığı bir dizi oluşturmak için kullanın `Array.zeroCreate` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="bf3a8-114">Erişim öğeleri</span><span class="sxs-lookup"><span data-stu-id="bf3a8-114">Access elements</span></span>

<span data-ttu-id="bf3a8-115">Dizi öğelerine bir nokta işleci ( `.` ) ve köşeli ayraçlar (ve) kullanarak erişebilirsiniz `[` `]` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="bf3a8-116">Dizi dizinleri 0 ' dan başlar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-116">Array indexes start at 0.</span></span>

<span data-ttu-id="bf3a8-117">Ayrıca, dizi öğelerine, dizinin bir alt aralığını belirtmenizi sağlayan dilim gösterimini kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="bf3a8-118">Dilim gösterimi örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="bf3a8-119">Dilim gösterimi kullanıldığında, dizinin yeni bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="bf3a8-120">Dizi türleri ve modülleri</span><span class="sxs-lookup"><span data-stu-id="bf3a8-120">Array types and modules</span></span>

<span data-ttu-id="bf3a8-121">Tüm F # dizilerinin türü .NET Framework türüdür <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bf3a8-122">Bu nedenle, F # dizileri ' de bulunan tüm işlevleri destekler <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bf3a8-123">[ `Array` Modül](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) , tek boyutlu dizilerde işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="bf3a8-124">Modüller, `Array2D` `Array3D` ve `Array4D` sırasıyla iki, üç ve dört boyutun dizilerindeki işlemleri destekleyen işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="bf3a8-125">Kullanarak dörtten büyük dizi dizileri oluşturabilirsiniz <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="bf3a8-126">Basit işlevler</span><span class="sxs-lookup"><span data-stu-id="bf3a8-126">Simple functions</span></span>

<span data-ttu-id="bf3a8-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) bir öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="bf3a8-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) bir dizinin uzunluğuna izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="bf3a8-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) bir öğeyi belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="bf3a8-130">Aşağıdaki kod örneği, bu işlevlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="bf3a8-131">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="bf3a8-132">Dizi oluşturan işlevler</span><span class="sxs-lookup"><span data-stu-id="bf3a8-132">Functions that create arrays</span></span>

<span data-ttu-id="bf3a8-133">Çeşitli işlevler, var olan bir dizi gerekmeden diziler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="bf3a8-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) herhangi bir öğe içermeyen yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="bf3a8-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) belirtilen boyuttaki bir dizi oluşturur ve tüm öğeleri sağlanmış değerlere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="bf3a8-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) öğeleri oluşturmak için bir boyut ve bir işlev verildiğinde bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="bf3a8-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) tüm öğelerin, dizinin türü için sıfır değere başlatıldığı bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="bf3a8-138">Aşağıdaki kod bu işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="bf3a8-139">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="bf3a8-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) Varolan bir diziden kopyalanmış öğeleri içeren yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="bf3a8-141">Kopyanın basit bir kopya olduğunu, yani öğe türü bir başvuru türü ise, temeldeki nesne değil yalnızca başvurunun kopyalanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="bf3a8-142">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="bf3a8-143">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="bf3a8-144">Dize `Test1` yalnızca ilk dizide görünür çünkü yeni bir öğe oluşturma işlemi içindeki başvurunun üzerine yazar, `firstArray` ancak hala içinde mevcut olan boş bir dizeye özgün başvuruyu etkilemez `secondArray` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="bf3a8-145">Dize `Test2` her iki dizide de görünür çünkü `Insert` türdeki işlem, <xref:System.Text.StringBuilder?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> her iki dizide de başvurulan temel nesneyi etkiler.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="bf3a8-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) bir dizinin alt aralığından yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="bf3a8-147">Başlangıç dizinini ve uzunluğunu belirterek alt aralığı belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="bf3a8-148">Aşağıdaki kod öğesinin kullanımını gösterir `Array.sub` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="bf3a8-149">Çıktı, alt dizinin 5. öğede başlayacağını ve 10 öğe içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="bf3a8-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) Varolan iki diziyi birleştirerek yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="bf3a8-151">Aşağıdaki kodda **Array. Append**gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="bf3a8-152">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="bf3a8-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) Yeni bir diziye dahil etmek için bir dizinin öğelerini seçer.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="bf3a8-154">Aşağıdaki kod gösterilmektedir `Array.choose` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="bf3a8-155">Dizinin öğe türünün, seçenek türünde döndürülen değer türüyle eşleşmesi gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="bf3a8-156">Bu örnekte, öğe türü ' dir `int` ve seçenek, `elem*elem - 1` kayan noktalı sayı olarak bir polinom işlevinin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="bf3a8-157">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="bf3a8-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) Varolan bir dizinin her bir dizi öğesinde belirtilen bir işlevi çalıştırır ve ardından işlev tarafından oluşturulan öğeleri toplar ve bunları yeni bir dizide birleştirir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="bf3a8-159">Aşağıdaki kod gösterilmektedir `Array.collect` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="bf3a8-160">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="bf3a8-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) dizi dizisini alır ve bunları tek bir dizi halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="bf3a8-162">Aşağıdaki kod gösterilmektedir `Array.concat` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="bf3a8-163">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="bf3a8-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) bir Boolean koşul işlevi alır ve yalnızca koşulun doğru olduğu Giriş dizisindeki öğeleri içeren yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="bf3a8-165">Aşağıdaki kod gösterilmektedir `Array.filter` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="bf3a8-166">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="bf3a8-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) Varolan bir dizinin sırasını tersine çevirerek yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="bf3a8-168">Aşağıdaki kod gösterilmektedir `Array.rev` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="bf3a8-169">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="bf3a8-170">Aşağıdaki örnekte gösterildiği gibi, ardışık düzen işlecini () kullanarak dizileri dönüştüren dizi modülündeki işlevleri kolayca birleştirebilirsiniz `|>` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="bf3a8-171">Çıktı</span><span class="sxs-lookup"><span data-stu-id="bf3a8-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="bf3a8-172">Çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="bf3a8-172">Multidimensional arrays</span></span>

<span data-ttu-id="bf3a8-173">Çok boyutlu bir dizi oluşturulabilir, ancak çok boyutlu bir dizi değişmez değeri yazmak için sözdizimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="bf3a8-174">[`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html)Dizi öğelerinden oluşan dizilerden bir dizi oluşturmak için işlecini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="bf3a8-175">Diziler dizi veya liste sabit değerleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="bf3a8-176">Örneğin, aşağıdaki kod iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="bf3a8-177">Ayrıca, işlevini [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) iki boyutun dizilerini başlatmak için de kullanabilirsiniz ve benzer işlevler üç ve dört boyutlu diziler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="bf3a8-178">Bu işlevler, öğeleri oluşturmak için kullanılan bir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="bf3a8-179">Bir işlev belirtmek yerine bir başlangıç değeri olarak ayarlanan öğeleri içeren iki boyutlu bir dizi oluşturmak için, [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) en fazla dört boyuta kadar diziler için de kullanılabilir olan işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="bf3a8-180">Aşağıdaki kod örneği, önce istenen öğeleri içeren bir dizi dizinin nasıl oluşturulacağını gösterir ve ardından `Array2D.init` istenen iki boyutlu diziyi oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="bf3a8-181">Dizi dizin oluşturma ve dilimleme sözdizimi, sıralama 4 ' e kadar olan diziler için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="bf3a8-182">Birden çok boyutta bir dizin belirttiğinizde, aşağıdaki kod örneğinde gösterildiği gibi, dizinleri ayırmak için virgül kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="bf3a8-183">İki boyutlu bir dizinin türü olarak yazılır `<type>[,]` (örneğin,, `int[,]` `double[,]` ) ve üç boyutlu bir dizinin türü `<type>[,,]` , daha yüksek boyutlarda diziler için olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="bf3a8-184">Tek boyutlu diziler için kullanılabilen işlevlerin yalnızca bir alt kümesi, çok boyutlu diziler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="bf3a8-185">Dizi Dilimleme ve çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="bf3a8-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="bf3a8-186">İki boyutlu bir dizide (bir matris), aralıkları belirterek ve `*` tüm satırları veya sütunları belirtmek için bir joker karakter () karakterini kullanarak bir alt matrisi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="bf3a8-187">Çok boyutlu bir diziyi, aynı veya alt boyutun alt dizileri halinde parçalara ayırmayı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="bf3a8-188">Örneğin, tek bir satır veya sütun belirterek bir matreden bir vektör elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="bf3a8-189">Bu dilimleme sözdizimini, öğe erişim işleçleri ve aşırı yüklenmiş yöntemler uygulayan türler için kullanabilirsiniz `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="bf3a8-190">Örneğin, aşağıdaki kod F # 2D dizisini sarmalayan bir matris türü oluşturur, dizi dizini oluşturma desteği sağlamak için bir öğe özelliği uygular ve üç sürümünü uygular `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="bf3a8-191">Bu kodu matris türleriniz için bir şablon olarak kullanacaksanız, bu bölümde açıklanan tüm Dilimleme işlemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="bf3a8-192">Diziler üzerinde Boole işlevleri</span><span class="sxs-lookup"><span data-stu-id="bf3a8-192">Boolean functions on arrays</span></span>

<span data-ttu-id="bf3a8-193">[`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) Sırasıyla bir veya iki dizide bulunan işlevler ve test öğeleri.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="bf3a8-194">Bu işlevler bir test işlevi alır ve `true` koşulu karşılayan bir öğe (veya öğe çifti) varsa döndürülür `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="bf3a8-195">Aşağıdaki kod, ve kullanımını göstermektedir `Array.exists` `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="bf3a8-196">Bu örneklerde, bağımsız değişkenlerden yalnızca biri uygulanarak, bu durumlarda işlev bağımsız değişkeni olarak yeni işlevler oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="bf3a8-197">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="bf3a8-198">Benzer şekilde, işlevi [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) her öğenin bir Boole koşulunu karşılayıp karşılamadığını tespit etmek için bir diziyi sınar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="bf3a8-199">Çeşitleme, [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) aynı şeyi eşit uzunlukta iki dizinin öğelerini içeren bir Boolean işlevi kullanarak yapar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="bf3a8-200">Aşağıdaki kod, bu işlevlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="bf3a8-201">Bu örneklerin çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="bf3a8-202">Dizileri ara</span><span class="sxs-lookup"><span data-stu-id="bf3a8-202">Search arrays</span></span>

<span data-ttu-id="bf3a8-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) bir Boole işlevi alır ve işlevin döndürdüğü ilk öğeyi döndürür `true` ya da <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> koşulu karşılayan bir öğe bulunursa, öğesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="bf3a8-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex)`Array.find`,, öğesinin kendisi yerine öğesinin dizinini döndürmesi dışında, gibidir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="bf3a8-205">Aşağıdaki kod, `Array.find` `Array.findIndex` hem mükemmel bir kare hem de kusursuz küp olan bir sayıyı bulmak için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="bf3a8-206">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="bf3a8-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) , `Array.find` , sonucu bir seçenek türü olması dışında, bir öğe bulunmazsa, öğesini döndürür `None` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="bf3a8-208">`Array.tryFind``Array.find`bir eşleşen öğenin dizide olup olmadığını bilinmediğinizde yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="bf3a8-209">Benzer şekilde, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) `Array.findIndex` seçenek türünün dönüş değeri olması dışında, benzer.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="bf3a8-210">Hiçbir öğe bulunmazsa, seçeneği olur `None` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="bf3a8-211">Aşağıdaki kod öğesinin kullanımını gösterir `Array.tryFind` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="bf3a8-212">Bu kod, önceki koda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="bf3a8-213">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="bf3a8-214">[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)Öğesini bulmaya ek olarak bir öğesi dönüştürmeniz gerektiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="bf3a8-215">Sonuç, işlevin dönüştürülmüş öğeyi bir seçenek değeri olarak döndürdüğü ilk öğedir, ya da `None` böyle bir öğe bulunmazsa.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="bf3a8-216">Aşağıdaki kod öğesinin kullanımını gösterir `Array.tryPick` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="bf3a8-217">Bu durumda, bir lambda ifadesi yerine, kodu basitleştirmek için birkaç yerel yardımcı işlev tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="bf3a8-218">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="bf3a8-219">Diziler üzerinde hesaplamalar gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="bf3a8-219">Perform computations on arrays</span></span>

<span data-ttu-id="bf3a8-220">[`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average)İşlevi dizideki her öğenin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="bf3a8-221">Bu, kayan nokta türleri de dahil olmak üzere, bir tamsayı ile tam bölme desteği olan öğe türleriyle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="bf3a8-222">[`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy)İşlevi her öğe üzerinde bir işlev çağırma sonuçlarının ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="bf3a8-223">Bir integral türü dizisi için öğesini kullanabilir `Array.averageBy` ve işlevin her öğeyi hesaplama için bir kayan nokta türüne dönüştürmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="bf3a8-224">[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) Öğe türü destekliyorsa, en büyük veya en küçük öğeyi almak için veya kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="bf3a8-225">Benzer şekilde, ancak [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) önce bir işlevin yürütülmesini, belki de karşılaştırmayı destekleyen bir türe dönüştürülmeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="bf3a8-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) bir dizinin öğelerini ekler ve [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) her bir öğeye bir işlev çağırır ve sonuçları birlikte ekler.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="bf3a8-227">Dönüş değerlerini depolamadan bir dizideki her öğe üzerinde bir işlevi yürütmek için kullanın [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="bf3a8-228">Eşit uzunlukta iki dizi içeren bir işlev için kullanın [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="bf3a8-229">Ayrıca, işlevin sonuçlarının bir dizisini tutmanız gerekiyorsa, [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) veya kullanın [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , tek seferde iki dizi üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="bf3a8-230">Çeşitlemeler [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) ve [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) öğenin dizine eklenmesine izin verir; aynı değer ve için de geçerlidir [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="bf3a8-231">,,,, [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) Ve işlevleri, [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) bir dizinin tüm öğelerini içeren algoritmaları içerir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="bf3a8-232">Benzer şekilde, Çeşitlemeler [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) ve [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) iki dizi üzerinde hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="bf3a8-233">Hesaplamalar gerçekleştirmeye yönelik bu işlevler, [liste modülündeki](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)aynı adlı işlevlere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="bf3a8-234">Kullanım örnekleri için bkz. [listeler](lists.md).</span><span class="sxs-lookup"><span data-stu-id="bf3a8-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="bf3a8-235">Dizileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="bf3a8-235">Modify arrays</span></span>

<span data-ttu-id="bf3a8-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) bir öğeyi belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="bf3a8-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) bir dizideki öğe aralığını belirtilen değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="bf3a8-238">Aşağıdaki kod bir örneği sağlar `Array.fill` .</span><span class="sxs-lookup"><span data-stu-id="bf3a8-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="bf3a8-239">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bf3a8-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="bf3a8-240">Bir [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) dizinin alt bölümünü başka bir diziye kopyalamak için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="bf3a8-241">Diğer türlere ve diğer türlerden Dönüştür</span><span class="sxs-lookup"><span data-stu-id="bf3a8-241">Convert to and from other types</span></span>

<span data-ttu-id="bf3a8-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) bir listeden bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="bf3a8-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) diziden bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="bf3a8-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) ve [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) dizi türünden bu diğer koleksiyon türlerine Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="bf3a8-245">Dizileri Sırala</span><span class="sxs-lookup"><span data-stu-id="bf3a8-245">Sort arrays</span></span>

<span data-ttu-id="bf3a8-246">[`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort)Genel karşılaştırma işlevini kullanarak bir diziyi sıralamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="bf3a8-247">Anahtar [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) olarak adlandırılan ve anahtardaki genel karşılaştırma işlevini kullanarak sıralamak için bir değer oluşturan *key*bir işlev belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="bf3a8-248">[`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)Özel bir karşılaştırma işlevi sağlamak istiyorsanız kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="bf3a8-249">`Array.sort`, `Array.sortBy` ve `Array.sortWith` All sıralanmış diziyi yeni bir dizi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="bf3a8-250">Çeşitlemeler, [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) ve yeni bir [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) tane döndürmek yerine mevcut diziyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="bf3a8-251">Diziler ve tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="bf3a8-251">Arrays and tuples</span></span>

<span data-ttu-id="bf3a8-252">İşlevler ve dizi kümesi [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) çiftlerinin dizilerini dizi dizilerine ve tersine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="bf3a8-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) ve, [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) üç öğe tanımlama grubuyla veya üç dizi tanımlama grubu ile çalıştıkları sürece benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="bf3a8-254">Diziler üzerinde paralel hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="bf3a8-254">Parallel computations on arrays</span></span>

<span data-ttu-id="bf3a8-255">Modülü [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) diziler üzerinde paralel hesaplamalar gerçekleştirmeye yönelik işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="bf3a8-256">Bu modül, sürüm 4 ' ten önceki .NET Framework sürümlerini hedefleyen uygulamalarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf3a8-257">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf3a8-257">See also</span></span>

- [<span data-ttu-id="bf3a8-258">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="bf3a8-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="bf3a8-259">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="bf3a8-259">F# Types</span></span>](fsharp-types.md)
