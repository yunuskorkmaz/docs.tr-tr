---
title: Diziler
description: F# Programlama dilinde diziler oluşturmayı ve kullanmayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 8470e01087e417635bcd5c528df9b9e089cbf59f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320499"
---
# <a name="arrays"></a><span data-ttu-id="3e03b-103">Diziler</span><span class="sxs-lookup"><span data-stu-id="3e03b-103">Arrays</span></span>

> [!NOTE]
> <span data-ttu-id="3e03b-104">API başvuru bağlantısı sizi MSDN 'ye götürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="3e03b-105">Docs.microsoft.com API başvurusu tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="3e03b-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="3e03b-106">Diziler, aynı türde olan ardışık veri öğelerinin sabit boyutlu, sıfır tabanlı ve değişebilir koleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="3e03b-107">Diziler oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e03b-107">Creating Arrays</span></span>

<span data-ttu-id="3e03b-108">Çeşitli yollarla diziler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-108">You can create arrays in several ways.</span></span> <span data-ttu-id="3e03b-109">Aşağıdaki örneklerde gösterildiği gibi `[|` ve `|]` arasında ardışık değerleri listeleyerek ve noktalı virgülle ayırarak küçük bir dizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="3e03b-110">Ayrıca her öğeyi ayrı bir satıra koyabilirsiniz, bu durumda noktalı virgül ayırıcı isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="3e03b-111">Dizi öğelerinin türü, kullanılan değişmez değerlerden çıkarılan ve tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="3e03b-112">Aşağıdaki kod bir hataya neden olur, çünkü 1,0 bir float ve 2 ve 3 tamsayılardır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="3e03b-113">Diziler oluşturmak için dizi ifadelerini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="3e03b-114">Aşağıda, 1 ile 10 arasında bir tamsayı kare dizisi oluşturan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="3e03b-115">Tüm öğelerin sıfıra başlatıldığı bir dizi oluşturmak için `Array.zeroCreate`kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a><span data-ttu-id="3e03b-116">Öğelere erişme</span><span class="sxs-lookup"><span data-stu-id="3e03b-116">Accessing Elements</span></span>

<span data-ttu-id="3e03b-117">Dizi öğelerine, nokta işleci (`.`) ve köşeli ayraçlar (`[` ve `]`) kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="3e03b-118">Dizi dizinleri 0 ' dan başlar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-118">Array indexes start at 0.</span></span>

<span data-ttu-id="3e03b-119">Ayrıca, dizi öğelerine, dizinin bir alt aralığını belirtmenizi sağlayan dilim gösterimini kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="3e03b-120">Dilim gösterimi örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="3e03b-121">Dilim gösterimi kullanıldığında, dizinin yeni bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-121">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="3e03b-122">Dizi türleri ve modülleri</span><span class="sxs-lookup"><span data-stu-id="3e03b-122">Array Types and Modules</span></span>

<span data-ttu-id="3e03b-123">Tüm F# dizilerin türü <xref:System.Array?displayProperty=nameWithType>.NET Framework türüdür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e03b-124">Bu nedenle F# , diziler <xref:System.Array?displayProperty=nameWithType>bulunan tüm işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="3e03b-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3e03b-125">Kitaplık modülü, tek boyutlu diziler üzerindeki işlemleri destekler [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) .</span><span class="sxs-lookup"><span data-stu-id="3e03b-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="3e03b-126">`Array2D`, `Array3D`ve `Array4D` modüller, sırasıyla iki, üç ve dört boyutun dizilerindeki işlemleri destekleyen işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="3e03b-127"><xref:System.Array?displayProperty=nameWithType>kullanarak, dörtten büyük dizi dizileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="3e03b-128">Basit Işlevler</span><span class="sxs-lookup"><span data-stu-id="3e03b-128">Simple Functions</span></span>

<span data-ttu-id="3e03b-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) bir öğe alır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="3e03b-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) bir dizinin uzunluğuna izin verir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="3e03b-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) bir öğeyi belirtilen bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="3e03b-132">Aşağıdaki kod örneği, bu işlevlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="3e03b-133">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-133">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="3e03b-134">Dizi oluşturan işlevler</span><span class="sxs-lookup"><span data-stu-id="3e03b-134">Functions That Create Arrays</span></span>

<span data-ttu-id="3e03b-135">Çeşitli işlevler, var olan bir dizi gerekmeden diziler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="3e03b-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) hiçbir öğe içermeyen yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="3e03b-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) , belirtilen boyuttaki bir dizi oluşturur ve tüm öğeleri sağlanmış değerlere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="3e03b-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) , öğeleri oluşturmak için bir boyut ve bir işlev verilen bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="3e03b-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) , tüm öğelerin dizinin türü için sıfır değere başlatıldığı bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="3e03b-140">Aşağıdaki kod bu işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="3e03b-141">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-141">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="3e03b-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) , var olan bir diziden kopyalanmış öğeleri içeren yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="3e03b-143">Kopyanın basit bir kopya olduğunu, yani öğe türü bir başvuru türü ise, temeldeki nesne değil yalnızca başvurunun kopyalanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="3e03b-144">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="3e03b-145">Önceki kodun çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-145">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="3e03b-146">`Test1` dize yalnızca ilk dizide görünür çünkü yeni bir öğe oluşturma işlemi `firstArray` başvurunun üzerine yazar, ancak özgün başvuruyu `secondArray`hala mevcut olan boş bir dizeye etkilemez.</span><span class="sxs-lookup"><span data-stu-id="3e03b-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="3e03b-147">`Test2` dize her iki dizide de görünür çünkü <xref:System.Text.StringBuilder?displayProperty=nameWithType> türündeki `Insert` işlem, her iki dizide de başvurulan temel <xref:System.Text.StringBuilder?displayProperty=nameWithType> nesnesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="3e03b-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="3e03b-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) dizideki bir alt aralıktan yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="3e03b-149">Başlangıç dizinini ve uzunluğunu belirterek alt aralığı belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="3e03b-150">Aşağıdaki kod `Array.sub`kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="3e03b-151">Çıktı, alt dizinin 5. öğede başlayacağını ve 10 öğe içerdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="3e03b-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) , iki mevcut diziyi birleştirerek yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="3e03b-153">Aşağıdaki kodda **Array. Append**gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="3e03b-154">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-154">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="3e03b-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) yeni bir diziye dahil etmek için bir dizinin öğelerini seçer.</span><span class="sxs-lookup"><span data-stu-id="3e03b-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="3e03b-156">Aşağıdaki kod `Array.choose`gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="3e03b-157">Dizinin öğe türünün, seçenek türünde döndürülen değer türüyle eşleşmesi gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="3e03b-158">Bu örnekte, öğe türü `int` ve seçeneği bir polinom işlevinin, `elem*elem - 1`, kayan noktalı sayı olarak oluşur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="3e03b-159">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-159">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="3e03b-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) , var olan bir dizinin her dizi öğesinde belirtilen bir işlevi çalıştırır ve ardından işlev tarafından oluşturulan öğeleri toplar ve bunları yeni bir dizide birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="3e03b-161">Aşağıdaki kod `Array.collect`gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="3e03b-162">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-162">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="3e03b-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) diziler dizisini alır ve bunları tek bir dizide birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="3e03b-164">Aşağıdaki kod `Array.concat`gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="3e03b-165">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-165">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="3e03b-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) bir Boolean koşulu işlevi alır ve yalnızca koşulun doğru olduğu Giriş dizisindeki öğeleri içeren yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="3e03b-167">Aşağıdaki kod `Array.filter`gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="3e03b-168">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-168">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="3e03b-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) , var olan bir dizinin sırasını tersine çevirerek yeni bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="3e03b-170">Aşağıdaki kod `Array.rev`gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="3e03b-171">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-171">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="3e03b-172">Aşağıdaki örnekte gösterildiği gibi, ardışık düzen işlecini (`|>`) kullanarak dizileri dönüştüren dizi modülündeki işlevleri kolayca birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="3e03b-173">Çıktı</span><span class="sxs-lookup"><span data-stu-id="3e03b-173">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="3e03b-174">Çok Boyutlu Diziler</span><span class="sxs-lookup"><span data-stu-id="3e03b-174">Multidimensional Arrays</span></span>

<span data-ttu-id="3e03b-175">Çok boyutlu bir dizi oluşturulabilir, ancak çok boyutlu bir dizi değişmez değeri yazmak için sözdizimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="3e03b-176">Dizi öğelerinden oluşan dizilerden bir dizi oluşturmak için işleç [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="3e03b-177">Diziler dizi veya liste sabit değerleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="3e03b-178">Örneğin, aşağıdaki kod iki boyutlu bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="3e03b-179">Ayrıca, iki boyutun dizilerini başlatmak için [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) işlevini ve üç ve dört boyutun dizileri için de benzer işlevler kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="3e03b-180">Bu işlevler, öğeleri oluşturmak için kullanılan bir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="3e03b-181">Bir işlev belirtmek yerine bir başlangıç değeri olarak ayarlanan öğeleri içeren iki boyutlu bir dizi oluşturmak için, en fazla dört boyuta kadar diziler için de kullanılabilen [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="3e03b-182">Aşağıdaki kod örneği, önce istenen öğeleri içeren bir dizi dizinin nasıl oluşturulacağını gösterir ve ardından istenen iki boyutlu diziyi oluşturmak için `Array2D.init` kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="3e03b-183">Dizi dizin oluşturma ve dilimleme sözdizimi, sıralama 4 ' e kadar olan diziler için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="3e03b-184">Birden çok boyutta bir dizin belirttiğinizde, aşağıdaki kod örneğinde gösterildiği gibi, dizinleri ayırmak için virgül kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="3e03b-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="3e03b-185">İki boyutlu bir dizinin türü `<type>[,]` olarak yazılır (örneğin, `int[,]`, `double[,]`) ve üç boyutlu bir dizinin türü, daha yüksek boyutlarda diziler için `<type>[,,]`olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="3e03b-186">Tek boyutlu diziler için kullanılabilen işlevlerin yalnızca bir alt kümesi, çok boyutlu diziler için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="3e03b-187">Daha fazla bilgi için bkz. [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d)ve [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="3e03b-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="3e03b-188">Dizi Dilimleme ve çok boyutlu diziler</span><span class="sxs-lookup"><span data-stu-id="3e03b-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="3e03b-189">İki boyutlu bir dizide (bir matris), aralıkları belirterek ve tüm satırları veya sütunları belirtmek için bir joker (`*`) karakteri kullanarak bir alt matrisi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="3e03b-190">F# 3,1 itibariyle, çok boyutlu bir diziyi aynı veya daha düşük boyutun alt dizileri halinde parçalara ayırmayı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="3e03b-191">Örneğin, tek bir satır veya sütun belirterek bir matreden bir vektör elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="3e03b-192">Öğe erişim işleçlerini ve aşırı yüklenmiş `GetSlice` yöntemlerini uygulayan türler için bu dilimleme sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="3e03b-193">Örneğin, aşağıdaki kod, F# 2B diziyi sarmalayan bir matris türü oluşturur, dizi dizini oluşturma desteği sağlamak Için bir öğe özelliği uygular ve üç `GetSlice`sürümünü uygular.</span><span class="sxs-lookup"><span data-stu-id="3e03b-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="3e03b-194">Bu kodu matris türleriniz için bir şablon olarak kullanacaksanız, bu bölümde açıklanan tüm Dilimleme işlemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="3e03b-195">Diziler üzerinde Boole Işlevleri</span><span class="sxs-lookup"><span data-stu-id="3e03b-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="3e03b-196">İşlevler, sırasıyla bir veya iki dizide test öğeleri [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) ve [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) .</span><span class="sxs-lookup"><span data-stu-id="3e03b-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="3e03b-197">Bu işlevler bir test işlevi alır ve koşulu karşılayan bir öğe (veya `Array.exists2`için öğe çifti) varsa `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="3e03b-198">Aşağıdaki kod `Array.exists` ve `Array.exists2`kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="3e03b-199">Bu örneklerde, bağımsız değişkenlerden yalnızca biri uygulanarak, bu durumlarda işlev bağımsız değişkeni olarak yeni işlevler oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="3e03b-200">Önceki kodun çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-200">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="3e03b-201">Benzer şekilde, işlevi [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) bir diziyi, her öğenin bir Boole koşulunu karşılayıp karşılamadığını belirleyecek şekilde sınar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="3e03b-202">Çeşitleme [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) , aynı şeyi eşit uzunlukta iki dizinin öğelerini Içeren bir Boolean işlevi kullanarak yapar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="3e03b-203">Aşağıdaki kod, bu işlevlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="3e03b-204">Bu örneklerin çıktısı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-204">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="3e03b-205">Dizileri arama</span><span class="sxs-lookup"><span data-stu-id="3e03b-205">Searching Arrays</span></span>

<span data-ttu-id="3e03b-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) bir Boole işlevi alır ve işlevin `true`döndürdüğü ilk öğeyi döndürür ya da koşulu karşılayan hiçbir öğe bulunursa bir <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="3e03b-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) `Array.find`gibidir, ancak öğenin kendisi yerine öğesinin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="3e03b-208">Aşağıdaki kod, hem mükemmel bir kare hem de kusursuz küp olan bir sayıyı bulmak için `Array.find` ve `Array.findIndex` kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="3e03b-209">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-209">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="3e03b-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) `Array.find`gibidir, ancak sonucu bir seçenek türüdür ve hiçbir öğe bulunmazsa `None` döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="3e03b-211">bir eşleşen öğenin dizide olup olmadığını bilemezsiniz `Array.find` yerine `Array.tryFind` kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="3e03b-212">Benzer şekilde, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) gibi, seçenek türü de dönüş değeridir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="3e03b-213">Hiçbir öğe bulunmazsa, seçenek `None`.</span><span class="sxs-lookup"><span data-stu-id="3e03b-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="3e03b-214">Aşağıdaki kod `Array.tryFind`kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="3e03b-215">Bu kod, önceki koda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="3e03b-216">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-216">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="3e03b-217">Bir öğeyi bulmanın yanı sıra dönüştürmeniz gerektiğinde [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="3e03b-218">Sonuç, işlevin dönüştürülmüş öğeyi bir seçenek değeri olarak döndürdüğü ilk öğedir veya böyle bir öğe bulunmazsa `None`.</span><span class="sxs-lookup"><span data-stu-id="3e03b-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="3e03b-219">Aşağıdaki kod `Array.tryPick`kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="3e03b-220">Bu durumda, bir lambda ifadesi yerine, kodu basitleştirmek için birkaç yerel yardımcı işlev tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="3e03b-221">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-221">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="3e03b-222">Diziler üzerinde hesaplamalar gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3e03b-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="3e03b-223">[`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) işlevi dizideki her öğenin ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="3e03b-224">Bu, kayan nokta türleri de dahil olmak üzere, bir tamsayı ile tam bölme desteği olan öğe türleriyle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e03b-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="3e03b-225">[`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) işlevi, her öğe üzerinde bir işlev çağırma sonuçlarının ortalamasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="3e03b-226">Bir integral türü dizisi için `Array.averageBy` kullanabilir ve işlevin her öğeyi hesaplama için bir kayan nokta türüne dönüştürmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="3e03b-227">Öğe türü destekliyorsa, en büyük veya en küçük öğeyi almak için [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) veya [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="3e03b-228">Benzer şekilde, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) ve [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) önce bir işlevin yürütülmesini, belki de karşılaştırmayı destekleyen bir türe dönüştürmek için izin verir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="3e03b-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) bir dizinin öğelerini ekler ve [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) her öğe üzerinde bir işlev çağırır ve sonuçları birlikte ekler.</span><span class="sxs-lookup"><span data-stu-id="3e03b-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="3e03b-230">Dönüş değerlerini depolamadan bir dizideki her öğe üzerinde bir işlevi yürütmek için [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="3e03b-231">Eşit uzunlukta iki dizi içeren bir işlev için [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc)kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="3e03b-232">Ayrıca, işlevin sonuçlarının bir dizisini tutmanız gerekiyorsa, tek seferde iki dizide çalışan [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) veya [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c)kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="3e03b-233">[`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) ve [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) Çeşitlemeler, öğenin dizininin hesaplamasına dahil olmasını sağlar; [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) ve [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0)için de aynı değer geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="3e03b-234">İşlevler [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)ve [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) , bir dizinin tüm öğelerini içeren algoritmaları yürütür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="3e03b-235">Benzer şekilde, Çeşitlemeler [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) ve [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) iki dizide hesaplamalar yapar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="3e03b-236">Hesaplamalar gerçekleştirmeye yönelik bu işlevler, [liste modülündeki](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)aynı adlı işlevlere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="3e03b-237">Kullanım örnekleri için bkz. [listeler](lists.md).</span><span class="sxs-lookup"><span data-stu-id="3e03b-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="3e03b-238">Dizileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="3e03b-238">Modifying Arrays</span></span>

<span data-ttu-id="3e03b-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) bir öğeyi belirtilen bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="3e03b-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) dizideki öğe aralığını belirtilen bir değere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="3e03b-241">Aşağıdaki kod, `Array.fill`bir örneğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e03b-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="3e03b-242">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3e03b-242">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="3e03b-243">Bir dizinin alt bölümünü başka bir diziye kopyalamak için [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="3e03b-244">Diğer türlere ve diğer türlerden dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3e03b-244">Converting to and from Other Types</span></span>

<span data-ttu-id="3e03b-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) bir listeden dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="3e03b-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) diziden bir dizi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e03b-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="3e03b-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) ve [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) , dizi türünden bu diğer koleksiyon türlerine dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="3e03b-248">Dizileri sıralama</span><span class="sxs-lookup"><span data-stu-id="3e03b-248">Sorting Arrays</span></span>

<span data-ttu-id="3e03b-249">Genel karşılaştırma işlevini kullanarak bir diziyi sıralamak için [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="3e03b-250">Anahtardaki genel karşılaştırma işlevini kullanarak sıralamak için, *anahtar*olarak adlandırılan bir değer oluşturan bir işlevi belirtmek için [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="3e03b-251">Özel bir karşılaştırma işlevi sağlamak istiyorsanız [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e03b-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="3e03b-252">`Array.sort`, `Array.sortBy`ve `Array.sortWith` tümü sıralanmış diziyi yeni bir dizi olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="3e03b-253">Çeşitlemeler [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)ve [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) yeni bir dizi döndürmek yerine mevcut diziyi değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="3e03b-254">Diziler ve tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="3e03b-254">Arrays and Tuples</span></span>

<span data-ttu-id="3e03b-255">İşlevler [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) ve [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) dizi kümesi çiftlerinin dizilerini dizi dizilerine ve tam tersi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="3e03b-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="3e03b-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) ve [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) , üç öğe tanımlama grubuyla veya üç dizi tanımlama grubu ile çalıştıkları sürece benzerdir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="3e03b-257">Diziler üzerinde paralel hesaplamalar</span><span class="sxs-lookup"><span data-stu-id="3e03b-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="3e03b-258">Modül [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) diziler üzerinde paralel hesaplamalar gerçekleştirmek için işlevler içerir.</span><span class="sxs-lookup"><span data-stu-id="3e03b-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="3e03b-259">Bu modül, sürüm 4 ' ten önceki .NET Framework sürümlerini hedefleyen uygulamalarda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e03b-260">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e03b-260">See also</span></span>

- [<span data-ttu-id="3e03b-261">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3e03b-261">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="3e03b-262">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="3e03b-262">F# Types</span></span>](fsharp-types.md)
