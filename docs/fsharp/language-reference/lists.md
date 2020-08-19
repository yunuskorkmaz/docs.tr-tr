---
title: Listeler
description: 'Aynı türdeki sıralı, sabit bir öğe serisi olan F # listeleri hakkında bilgi edinin.'
ms.date: 08/13/2020
ms.openlocfilehash: 16d7195039d25cf63630f5cc3be6563b1bf45c44
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559173"
---
# <a name="lists"></a><span data-ttu-id="d1413-103">Listeler</span><span class="sxs-lookup"><span data-stu-id="d1413-103">Lists</span></span>

<span data-ttu-id="d1413-104">F # ' daki bir liste, aynı türde olan sıralı, sabit bir öğe serisidir.</span><span class="sxs-lookup"><span data-stu-id="d1413-104">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="d1413-105">Listelerde temel işlemleri gerçekleştirmek için, [liste modülündeki](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)işlevleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-105">To perform basic operations on lists, use the functions in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="d1413-106">Liste oluşturma ve başlatma</span><span class="sxs-lookup"><span data-stu-id="d1413-106">Creating and Initializing Lists</span></span>

<span data-ttu-id="d1413-107">Aşağıdaki kod satırında gösterildiği gibi, noktalı virgülle ayırarak ve köşeli parantez içine alınmış öğeleri açıkça listeleyerek bir liste tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-107">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="d1413-108">Ayrıca, öğelerin arasına satır sonları koyabilirsiniz, bu durumda noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d1413-108">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="d1413-109">İkinci sözdizimi, öğe başlatma ifadeleri daha uzun olduğunda veya her öğe için bir açıklama eklemek istediğinizde daha okunabilir kod oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-109">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="d1413-110">Normalde, tüm liste öğeleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1413-110">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="d1413-111">Bir özel durum, öğelerin temel tür olarak belirtildiği bir listenin türetilmiş tür öğelerine sahip olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-111">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="d1413-112">Bu nedenle, her ikisi `Button` ve `CheckBox` öğesinden türetiğinden aşağıdakiler kabul edilebilir `Control` .</span><span class="sxs-lookup"><span data-stu-id="d1413-112">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="d1413-113">Ayrıca `..` , aşağıdaki kodda gösterildiği gibi, Aralık işleci () ile ayrılmış tamsayılar tarafından belirtilen bir aralığı kullanarak liste öğelerini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-113">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="d1413-114">Boş bir liste, aralarında hiçbir şey olmadan köşeli ayraç çifti ile belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-114">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="d1413-115">Bir liste oluşturmak için bir dizi ifadesi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-115">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="d1413-116">Daha fazla bilgi için bkz. [dizi ifadeleri](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="d1413-116">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="d1413-117">Örneğin, aşağıdaki kod, 1 ile 10 arasındaki sayıların karelerinin bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1413-117">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="d1413-118">Listelerle çalışma için işleçler</span><span class="sxs-lookup"><span data-stu-id="d1413-118">Operators for Working with Lists</span></span>

<span data-ttu-id="d1413-119">(Cons) işlecini kullanarak bir listeye öğe ekleyebilirsiniz `::` .</span><span class="sxs-lookup"><span data-stu-id="d1413-119">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="d1413-120">`list1`İse `[2; 3; 4]` , aşağıdaki kod `list2` olarak oluşturulur `[100; 2; 3; 4]` .</span><span class="sxs-lookup"><span data-stu-id="d1413-120">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="d1413-121">Aşağıdaki kodda olduğu gibi işlecini kullanarak uyumlu türleri olan listeleri birleştirebilirsiniz `@` .</span><span class="sxs-lookup"><span data-stu-id="d1413-121">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="d1413-122">, `list1` Ve ise, `[2; 3; 4]` `list2` `[100; 2; 3; 4]` Bu kod olarak oluşturulur `list3` `[2; 3; 4; 100; 2; 3; 4]` .</span><span class="sxs-lookup"><span data-stu-id="d1413-122">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="d1413-123">Listelerde işlem gerçekleştirmeye yönelik işlevler, [liste modülünde](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d1413-123">Functions for performing operations on lists are available in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

<span data-ttu-id="d1413-124">F # içindeki listeler sabit olduğundan, tüm değiştirme işlemleri var olan listeleri değiştirmek yerine yeni listeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1413-124">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="d1413-125">F # içindeki listeler, listedir bağlantılı listeler olarak uygulanır. Bu, yalnızca listenin baş başlarına erişen işlemlerin O (1) ve öğe erişiminin ise O (*n*) olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d1413-125">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="d1413-126">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d1413-126">Properties</span></span>

<span data-ttu-id="d1413-127">Liste türü aşağıdaki özellikleri destekler:</span><span class="sxs-lookup"><span data-stu-id="d1413-127">The list type supports the following properties:</span></span>

|<span data-ttu-id="d1413-128">Özellik</span><span class="sxs-lookup"><span data-stu-id="d1413-128">Property</span></span>|<span data-ttu-id="d1413-129">Tür</span><span class="sxs-lookup"><span data-stu-id="d1413-129">Type</span></span>|<span data-ttu-id="d1413-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1413-130">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="d1413-131">Başlı</span><span class="sxs-lookup"><span data-stu-id="d1413-131">Head</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head)|`'T`|<span data-ttu-id="d1413-132">İlk öğesi.</span><span class="sxs-lookup"><span data-stu-id="d1413-132">The first element.</span></span>|
|[<span data-ttu-id="d1413-133">Olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="d1413-133">Empty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Empty)|`'T list`|<span data-ttu-id="d1413-134">Uygun türdeki boş bir liste döndüren statik özellik.</span><span class="sxs-lookup"><span data-stu-id="d1413-134">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="d1413-135">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="d1413-135">IsEmpty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#IsEmpty)|`bool`|<span data-ttu-id="d1413-136">`true` listede öğe yoksa.</span><span class="sxs-lookup"><span data-stu-id="d1413-136">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="d1413-137">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1413-137">Item</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Item)|`'T`|<span data-ttu-id="d1413-138">Belirtilen dizindeki öğe (sıfır tabanlı).</span><span class="sxs-lookup"><span data-stu-id="d1413-138">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="d1413-139">Uzunluk</span><span class="sxs-lookup"><span data-stu-id="d1413-139">Length</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Length)|`int`|<span data-ttu-id="d1413-140">Öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="d1413-140">The number of elements.</span></span>|
|[<span data-ttu-id="d1413-141">Kuyruk</span><span class="sxs-lookup"><span data-stu-id="d1413-141">Tail</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail)|`'T list`|<span data-ttu-id="d1413-142">İlk öğesi olmayan liste.</span><span class="sxs-lookup"><span data-stu-id="d1413-142">The list without the first element.</span></span>|

<span data-ttu-id="d1413-143">Aşağıda bu özellikleri kullanmaya ilişkin bazı örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1413-143">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="d1413-144">Listeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="d1413-144">Using Lists</span></span>

<span data-ttu-id="d1413-145">Listelerle programlama, az miktarda kodla karmaşık işlemler gerçekleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1413-145">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="d1413-146">Bu bölümde, işlevsel programlama için önemli olan listelerle ilgili genel işlemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1413-146">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="d1413-147">Listelerle özyineleme</span><span class="sxs-lookup"><span data-stu-id="d1413-147">Recursion with Lists</span></span>

<span data-ttu-id="d1413-148">Listeler özyinelemeli programlama tekniklerine benzersiz bir şekilde uygundur.</span><span class="sxs-lookup"><span data-stu-id="d1413-148">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="d1413-149">Listenin her öğesinde gerçekleştirilmesi gereken bir işlem düşünün.</span><span class="sxs-lookup"><span data-stu-id="d1413-149">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="d1413-150">Bu işlemi, listenin başından yararlanarak ve sonra listenin kuyruğunu geçirerek, ilk öğe olmayan orijinal listeden oluşan daha küçük bir liste olan bir sonraki özyineleme düzeyine geri dönerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-150">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="d1413-151">Bu tür bir özyinelemeli işlevi yazmak için, `::` bir listenin başını bir kuyruklu ayırmanızı sağlayan, model eşleme içinde Cons işlecini () kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-151">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="d1413-152">Aşağıdaki kod örneği, bir liste üzerinde işlemler gerçekleştiren özyinelemeli bir işlevi uygulamak için nasıl model eşleştirmesinin kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d1413-152">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="d1413-153">Önceki kod küçük listeler için iyi sonuç verir, ancak daha büyük listeler için yığın taşar.</span><span class="sxs-lookup"><span data-stu-id="d1413-153">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="d1413-154">Aşağıdaki kod, özyinelemeli işlevlerle çalışmaya yönelik standart bir yöntem olan bir biriktirici bağımsız değişkeni kullanarak bu kodda gelişir.</span><span class="sxs-lookup"><span data-stu-id="d1413-154">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="d1413-155">Biriktiricidir bağımsız değişkeninin kullanılması, yığın alanı kaydeden işlev kuyruklu özyinelemeli olur.</span><span class="sxs-lookup"><span data-stu-id="d1413-155">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="d1413-156">İşlevi, `RemoveAllMultiples` iki liste alan özyinelemeli bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="d1413-156">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="d1413-157">İlk liste, katları kaldırılacak olan sayıları ve ikinci liste ise sayıların kaldırılacağı liste olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d1413-157">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="d1413-158">Aşağıdaki örnekteki kod, bu özyinelemeli işlevi bir listeden tüm asal olmayan sayıları ortadan kaldırmak için kullanır ve sonuç olarak asal sayıların bir listesini bırakır.</span><span class="sxs-lookup"><span data-stu-id="d1413-158">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="d1413-159">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-159">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="d1413-160">Modül Işlevleri</span><span class="sxs-lookup"><span data-stu-id="d1413-160">Module Functions</span></span>

<span data-ttu-id="d1413-161">[Liste modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) , bir listenin öğelerine erişen işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1413-161">The [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) provides functions that access the elements of a list.</span></span> <span data-ttu-id="d1413-162">Baş öğe, erişimin en hızlı ve en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="d1413-162">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="d1413-163">Özellik [kafasını](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) veya [List. Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head)modül işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-163">Use the property [Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) or the module function [List.head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head).</span></span> <span data-ttu-id="d1413-164">[Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) özelliğini veya [List. tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) işlevini kullanarak bir listenin kuyruğunu erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-164">You can access the tail of a list by using the [Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) property or the [List.tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) function.</span></span> <span data-ttu-id="d1413-165">Dizine göre bir öğe bulmak için [List. nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) işlevini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-165">To find an element by index, use the [List.nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) function.</span></span> <span data-ttu-id="d1413-166">`List.nth` listede yer geçer.</span><span class="sxs-lookup"><span data-stu-id="d1413-166">`List.nth` traverses the list.</span></span> <span data-ttu-id="d1413-167">Bu nedenle, O (*n*).</span><span class="sxs-lookup"><span data-stu-id="d1413-167">Therefore, it is O(*n*).</span></span> <span data-ttu-id="d1413-168">Kodunuz `List.nth` sıklıkla kullanılıyorsa, bir liste yerine bir dizi kullanmayı düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-168">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="d1413-169">Dizilerde öğe erişimi O (1).</span><span class="sxs-lookup"><span data-stu-id="d1413-169">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="d1413-170">Listelerde Boole Işlemleri</span><span class="sxs-lookup"><span data-stu-id="d1413-170">Boolean Operations on Lists</span></span>

<span data-ttu-id="d1413-171">[List. IsEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) işlevi bir listenin herhangi bir öğeye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d1413-171">The [List.isEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) function determines whether a list has any elements.</span></span>

<span data-ttu-id="d1413-172">[List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) işlevi bir listenin öğelerine Boole testi uygular ve `true` herhangi bir öğe, testi karşılıyorsa döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1413-172">The [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="d1413-173">[List. exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) benzerdir ancak iki listede ardışık öğe çiftlerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="d1413-173">[List.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="d1413-174">Aşağıdaki kod öğesinin kullanımını gösterir `List.exists` .</span><span class="sxs-lookup"><span data-stu-id="d1413-174">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="d1413-175">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-175">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="d1413-176">Aşağıdaki örnek öğesinin kullanımını gösterir `List.exists2` .</span><span class="sxs-lookup"><span data-stu-id="d1413-176">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="d1413-177">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-177">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="d1413-178">List [. forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) ' i kullanarak bir listedeki tüm öğelerin bir koşula uyup uymadığını test etmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="d1413-178">You can use [List.forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="d1413-179">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-179">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="d1413-180">Benzer şekilde, [List. forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) , iki liste içindeki karşılık gelen konumlarda bulunan tüm öğelerin her bir öğe çiftini Içeren bir Boolean ifade karşılayıp karşılamadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d1413-180">Similarly, [List.forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="d1413-181">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-181">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="d1413-182">Listelerde sıralama Işlemleri</span><span class="sxs-lookup"><span data-stu-id="d1413-182">Sort Operations on Lists</span></span>

<span data-ttu-id="d1413-183">[List. Sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy)ve [List. sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) işlevleri sıralama listeleri.</span><span class="sxs-lookup"><span data-stu-id="d1413-183">The [List.sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List.sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy), and [List.sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) functions sort lists.</span></span> <span data-ttu-id="d1413-184">Sıralama işlevi, bu üç işlevden hangisini kullanacağınızı belirler.</span><span class="sxs-lookup"><span data-stu-id="d1413-184">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="d1413-185">`List.sort` Varsayılan genel karşılaştırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1413-185">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="d1413-186">Genel karşılaştırma, değerleri karşılaştırmak için genel karşılaştırma işlevini temel alan genel işleçleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1413-186">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="d1413-187">Basit sayısal türler, tanımlama grupları, kayıtlar, ayırt edici birleşimler, listeler, diziler ve uygulayan herhangi bir tür gibi çok sayıda öğe türü ile verimli bir şekilde çalışmaktadır `System.IComparable` .</span><span class="sxs-lookup"><span data-stu-id="d1413-187">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="d1413-188">Uygulayan türler için `System.IComparable` , genel karşılaştırma `System.IComparable.CompareTo()` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1413-188">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="d1413-189">Genel karşılaştırma dizelerle de birlikte çalışarak, ancak kültüre bağımsız bir sıralama düzeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1413-189">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="d1413-190">Genel karşılaştırma, işlev türleri gibi desteklenmeyen türlerde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1413-190">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="d1413-191">Ayrıca, varsayılan genel karşılaştırmanın performansı, küçük yapılandırılmış türler için en iyisidir; sıklıkla karşılaştırılması ve sıralanması gereken daha büyük yapılandırılmış türler için, `System.IComparable` yöntemini uygulamayı ve verimli bir uygulama sağlamayı düşünün `System.IComparable.CompareTo()` .</span><span class="sxs-lookup"><span data-stu-id="d1413-191">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="d1413-192">`List.sortBy` sıralama ölçütü olarak kullanılan bir değer döndüren bir işlev alır ve bir `List.sortWith` karşılaştırma işlevini bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="d1413-192">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="d1413-193">Bu ikinci iki işlev, karşılaştırmayı desteklemeyen türlerle çalışırken ya da karşılaştırma, kültüre duyarlı dizeler söz konusu olduğunda olduğu gibi daha karmaşık karşılaştırma semantiği gerektirdiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d1413-193">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="d1413-194">Aşağıdaki örnek öğesinin kullanımını gösterir `List.sort` .</span><span class="sxs-lookup"><span data-stu-id="d1413-194">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="d1413-195">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-195">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="d1413-196">Aşağıdaki örnek öğesinin kullanımını gösterir `List.sortBy` .</span><span class="sxs-lookup"><span data-stu-id="d1413-196">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="d1413-197">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-197">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="d1413-198">Sonraki örnek öğesinin kullanımını gösterir `List.sortWith` .</span><span class="sxs-lookup"><span data-stu-id="d1413-198">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="d1413-199">Bu örnekte, özel karşılaştırma işlevi öncelikle bir `compareWidgets` özel türün bir alanını ve ardından ilk alanın değerleri eşitse başka bir değeri karşılaştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1413-199">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="d1413-200">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-200">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="d1413-201">Listelerde arama Işlemleri</span><span class="sxs-lookup"><span data-stu-id="d1413-201">Search Operations on Lists</span></span>

<span data-ttu-id="d1413-202">Listeler için çok sayıda arama işlemi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d1413-202">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="d1413-203">En basit, [List. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), belirli bir koşulla eşleşen ilk öğeyi bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1413-203">The simplest, [List.find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="d1413-204">Aşağıdaki kod örneği, `List.find` bir listede 5 ' e bölünebilen ilk sayıyı bulmak için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1413-204">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="d1413-205">Sonuç 5 ' tir.</span><span class="sxs-lookup"><span data-stu-id="d1413-205">The result is 5.</span></span>

<span data-ttu-id="d1413-206">Öğelerin önce dönüştürülmesi gerekiyorsa, bir seçenek döndüren bir işlevi alan [List. Pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick)çağırın ve olan ilk seçenek değerini arar `Some(x)` .</span><span class="sxs-lookup"><span data-stu-id="d1413-206">If the elements must be transformed first, call [List.pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="d1413-207">Öğesini döndürmek yerine `List.pick` sonucunu döndürür `x` .</span><span class="sxs-lookup"><span data-stu-id="d1413-207">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="d1413-208">Eşleşen bir öğe bulunamazsa, `List.pick` oluşturur `System.Collections.Generic.KeyNotFoundException` .</span><span class="sxs-lookup"><span data-stu-id="d1413-208">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="d1413-209">Aşağıdaki kod öğesinin kullanımını gösterir `List.pick` .</span><span class="sxs-lookup"><span data-stu-id="d1413-209">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="d1413-210">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-210">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="d1413-211">Başka bir arama işlemleri grubu olan [List. tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) ve related işlevleri, bir seçenek değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1413-211">Another group of search operations, [List.tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) and related functions, return an option value.</span></span> <span data-ttu-id="d1413-212">İşlevi, böyle bir öğe varsa bir `List.tryFind` koşulu karşılayan bir listenin ilk öğesini döndürür, ancak değilse seçenek değeri `None` .</span><span class="sxs-lookup"><span data-stu-id="d1413-212">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="d1413-213">Çeşitleme [listesi. tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) , öğenin kendisi yerine, varsa, öğesinin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1413-213">The variation [List.tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="d1413-214">Bu işlevler aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1413-214">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="d1413-215">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-215">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="d1413-216">Listelerde aritmetik Işlemler</span><span class="sxs-lookup"><span data-stu-id="d1413-216">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="d1413-217">Toplam ve ortalama gibi yaygın aritmetik işlemler [liste modülüne](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)yerleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1413-217">Common arithmetic operations such as sum and average are built into the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="d1413-218">[List. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum)ile çalışmak için liste öğesi türü `+` işleci desteklemelidir ve sıfır değerine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1413-218">To work with [List.sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="d1413-219">Tüm yerleşik aritmetik türler bu koşulları karşılar.</span><span class="sxs-lookup"><span data-stu-id="d1413-219">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="d1413-220">[List. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average)ile çalışmak için, öğe türü, bir geri kalanı olmadan bir bölüm desteklemelidir, bu da integral türlerini dışlar, ancak kayan nokta türlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d1413-220">To work with [List.average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="d1413-221">[List. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) ve [List. averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) işlevleri bir işlevi parametre olarak alır ve bu işlevin sonuçları Sum veya Average değerlerini hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1413-221">The [List.sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) and [List.averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="d1413-222">Aşağıdaki kod,, ve kullanımını gösterir `List.sum` `List.sumBy` `List.average` .</span><span class="sxs-lookup"><span data-stu-id="d1413-222">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="d1413-223">Çıktı `1.000000` .</span><span class="sxs-lookup"><span data-stu-id="d1413-223">The output is `1.000000`.</span></span>

<span data-ttu-id="d1413-224">Aşağıdaki kod öğesinin kullanımını gösterir `List.averageBy` .</span><span class="sxs-lookup"><span data-stu-id="d1413-224">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="d1413-225">Çıktı `5.5` .</span><span class="sxs-lookup"><span data-stu-id="d1413-225">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="d1413-226">Listeler ve tanımlama grupları</span><span class="sxs-lookup"><span data-stu-id="d1413-226">Lists and Tuples</span></span>

<span data-ttu-id="d1413-227">Tanımlama gruplarını içeren listeler, zip ve unzip işlevleri tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-227">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="d1413-228">Bu işlevler, tek değerlerden oluşan iki listeyi tek bir tanımlama grubu içinde birleştirir veya bir tanımlama grubu listesini tek değerlerden oluşan iki listeye ayırır.</span><span class="sxs-lookup"><span data-stu-id="d1413-228">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="d1413-229">En basit [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) işlevi, tek öğelerin iki listesini alır ve dizi kümesi çiftlerinin tek bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1413-229">The simplest [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="d1413-230">Farklı bir sürüm olan [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), tek öğelerin üç listesini alır ve üç öğesi olan bir tanımlama grubu listesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1413-230">Another version, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="d1413-231">Aşağıdaki kod örneği öğesinin kullanımını gösterir `List.zip` .</span><span class="sxs-lookup"><span data-stu-id="d1413-231">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="d1413-232">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-232">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="d1413-233">Aşağıdaki kod örneği öğesinin kullanımını gösterir `List.zip3` .</span><span class="sxs-lookup"><span data-stu-id="d1413-233">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="d1413-234">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-234">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="d1413-235">Karşılık gelen unzip sürümleri, [List. unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) ve [List. unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), tanımlama grubu ve dönüş listelerinin listesini alır, burada ilk liste her bir tanımlama grubunda ilk olan tüm öğeleri içerir ve ikinci liste her bir tanımlama grubunun ikinci öğesini içerir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="d1413-235">The corresponding unzip versions, [List.unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) and [List.unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="d1413-236">Aşağıdaki kod örneği [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1413-236">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="d1413-237">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-237">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="d1413-238">Aşağıdaki kod örneği [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1413-238">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="d1413-239">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-239">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="d1413-240">Liste öğelerinde çalışma</span><span class="sxs-lookup"><span data-stu-id="d1413-240">Operating on List Elements</span></span>

<span data-ttu-id="d1413-241">F #, liste öğelerinde çeşitli işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d1413-241">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="d1413-242">Listenin her öğesinde bir işlevi çağırmanızı sağlayan en basit [List. iter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter).</span><span class="sxs-lookup"><span data-stu-id="d1413-242">The simplest is [List.iter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="d1413-243">Her bir öğenin dizininin her öğe için çağrılan işleve bir bağımsız değişken olarak geçirilmesi ve ve işlevlerinin bir birleşimi [List.iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri)olan List. iteri2 ' yi, bu iki listenin öğelerinde bir işlem gerçekleştirmenize olanak sağlayan varyasyonlar Include [List. iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2) `List.iter` [List.iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2) `List.iter2` `List.iteri` .</span><span class="sxs-lookup"><span data-stu-id="d1413-243">Variations include [List.iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), which enables you to perform an operation on elements of two lists, [List.iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="d1413-244">Aşağıdaki kod örneği bu işlevleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1413-244">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="d1413-245">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-245">The output is as follows:</span></span>

```console
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="d1413-246">Liste öğelerini dönüştüren başka bir sık kullanılan işlev List [. Map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map)olur ve bu, bir listedeki her öğeye bir işlev uygulamanıza ve tüm sonuçların yeni bir listeye yerleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1413-246">Another frequently used function that transforms list elements is [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="d1413-247">[List. map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) ve [List. map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) birden çok liste alan değişimlerdir.</span><span class="sxs-lookup"><span data-stu-id="d1413-247">[List.map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) and [List.map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) are variations that take multiple lists.</span></span> <span data-ttu-id="d1413-248">[List. mapi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) ve [List. mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2)öğesini de kullanabilirsiniz. Buna ek olarak, işlevine her öğenin dizinini geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1413-248">You can also use [List.mapi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) and [List.mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="d1413-249">Ve arasındaki tek fark `List.mapi2` , `List.mapi` `List.mapi2` iki liste ile birlikte çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="d1413-249">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="d1413-250">Aşağıdaki örnekte [List. Map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map)gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d1413-250">The following example illustrates [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="d1413-251">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-251">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="d1413-252">Aşağıdaki örnek öğesinin kullanımını gösterir `List.map2` .</span><span class="sxs-lookup"><span data-stu-id="d1413-252">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="d1413-253">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-253">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="d1413-254">Aşağıdaki örnek öğesinin kullanımını gösterir `List.map3` .</span><span class="sxs-lookup"><span data-stu-id="d1413-254">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="d1413-255">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-255">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="d1413-256">Aşağıdaki örnek öğesinin kullanımını gösterir `List.mapi` .</span><span class="sxs-lookup"><span data-stu-id="d1413-256">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="d1413-257">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-257">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="d1413-258">Aşağıdaki örnek öğesinin kullanımını gösterir `List.mapi2` .</span><span class="sxs-lookup"><span data-stu-id="d1413-258">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="d1413-259">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-259">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="d1413-260">[List. Collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) , `List.map` her öğe bir liste ürettiğinden ve tüm bu listelerin son bir liste ile bitiştirildiği durumlar haricinde gibidir.</span><span class="sxs-lookup"><span data-stu-id="d1413-260">[List.collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="d1413-261">Aşağıdaki kodda, listenin her bir öğesi üç sayı üretir.</span><span class="sxs-lookup"><span data-stu-id="d1413-261">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="d1413-262">Bunların hepsi tek bir listede toplanır.</span><span class="sxs-lookup"><span data-stu-id="d1413-262">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="d1413-263">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-263">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="d1413-264">Ayrıca, Boolean koşulunu alan ve yalnızca verilen koşulu karşılayan öğelerden oluşan yeni bir liste üreten [List. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter)öğesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1413-264">You can also use [List.filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="d1413-265">Elde edilen liste `[2; 4; 6]` .</span><span class="sxs-lookup"><span data-stu-id="d1413-265">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="d1413-266">Map ve Filter, [List.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) Select birleşimi, öğeleri aynı anda dönüştürmenizi ve seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1413-266">A combination of map and filter, [List.choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="d1413-267">`List.choose` bir listedeki her öğeye bir seçenek döndüren bir işlev uygular ve işlev seçenek değerini döndürdüğünde öğelerin sonuçlarının yeni bir listesini döndürür `Some` .</span><span class="sxs-lookup"><span data-stu-id="d1413-267">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="d1413-268">Aşağıdaki kod, `List.choose` bir sözcük listesinden büyük harfli sözcükler seçmek için kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1413-268">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="d1413-269">Çıktı aşağıdaki şekilde olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d1413-269">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="d1413-270">Birden çok liste üzerinde çalışma</span><span class="sxs-lookup"><span data-stu-id="d1413-270">Operating on Multiple Lists</span></span>

<span data-ttu-id="d1413-271">Listeler birlikte birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-271">Lists can be joined together.</span></span> <span data-ttu-id="d1413-272">İki listeyi tek tek birleştirmek için [List. Append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-272">To join two lists into one, use [List.append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append).</span></span> <span data-ttu-id="d1413-273">İkiden fazla listeyi birleştirmek için [List. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-273">To join more than two lists, use [List.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="d1413-274">Katlama ve tarama Işlemleri</span><span class="sxs-lookup"><span data-stu-id="d1413-274">Fold and Scan Operations</span></span>

<span data-ttu-id="d1413-275">Bazı liste işlemleri liste öğeleri arasında bağımlılıkları kapsar.</span><span class="sxs-lookup"><span data-stu-id="d1413-275">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="d1413-276">Katlama ve tarama işlemleri, `List.iter` `List.map` her öğe üzerinde bir işlevi çağırmanıza benzer ancak bu işlemler, hesaplama aracılığıyla bilgi taşıyan bir ek parametre sağlar. *accumulator*</span><span class="sxs-lookup"><span data-stu-id="d1413-276">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="d1413-277">`List.fold`Bir liste üzerinde hesaplama gerçekleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-277">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="d1413-278">Aşağıdaki kod örneği, çeşitli işlemleri gerçekleştirmek için [List. Fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) öğesinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1413-278">The following code example demonstrates the use of [List.fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) to perform various operations.</span></span>

<span data-ttu-id="d1413-279">Listeye çapraz ve Biriktirici, `acc` Hesaplama ilerledikçe geçen bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="d1413-279">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="d1413-280">İlk bağımsız değişken, biriktiriciden ve List öğesini alır ve bu liste öğesi için hesaplamanın ara sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1413-280">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="d1413-281">İkinci bağımsız değişken, biriktiricinin ilk değeridir.</span><span class="sxs-lookup"><span data-stu-id="d1413-281">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="d1413-282">İşlev adında basamak olan bu işlevlerin sürümleri birden fazla listede çalışır.</span><span class="sxs-lookup"><span data-stu-id="d1413-282">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="d1413-283">Örneğin, [List. fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) iki listede hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d1413-283">For example, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) performs computations on two lists.</span></span>

<span data-ttu-id="d1413-284">Aşağıdaki örnek öğesinin kullanımını gösterir `List.fold2` .</span><span class="sxs-lookup"><span data-stu-id="d1413-284">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="d1413-285">`List.fold` ve [List. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) , `List.fold` ek parametrenin son değerini döndüren ' de farklılık gösterir, ancak `List.scan` ek parametrenin ara değerlerinin (son değeri ile birlikte) listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d1413-285">`List.fold` and [List.scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="d1413-286">Bu işlevlerin her biri, listenin geri alındığı sırada ve bağımsız değişkenlerin sırası farklı olan [List. foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack)gibi bir ters çeşitleme içerir.</span><span class="sxs-lookup"><span data-stu-id="d1413-286">Each of these functions includes a reverse variation, for example, [List.foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="d1413-287">Ayrıca, `List.fold` ve aynı `List.foldBack` uzunlukta iki liste alan Çeşitlemeler, [List. fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) ve [List. foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2)' i de vardır.</span><span class="sxs-lookup"><span data-stu-id="d1413-287">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) and [List.foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), that take two lists of equal length.</span></span> <span data-ttu-id="d1413-288">Her öğe üzerinde yürütülen işlev, bazı eylemler gerçekleştirmek için her iki listedeki ilgili öğeleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-288">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="d1413-289">Aşağıdaki örnekte olduğu gibi, iki listenin öğe türleri farklı olabilir. Bu, bir liste bir banka hesabı için işlem tutarlarını içerir ve diğer liste işlemin türünü içerir: depozito veya çekme al.</span><span class="sxs-lookup"><span data-stu-id="d1413-289">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="d1413-290">Toplama gibi bir hesaplama için, `List.fold` `List.foldBack` sonuç çapraz geçiş sırasına bağlı olmadığından aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d1413-290">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="d1413-291">Aşağıdaki örnekte, `List.foldBack` bir listedeki öğeleri eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1413-291">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="d1413-292">Aşağıdaki örnek, banka hesabı örneğine geri döner.</span><span class="sxs-lookup"><span data-stu-id="d1413-292">The following example returns to the bank account example.</span></span> <span data-ttu-id="d1413-293">Yeni bir işlem türü eklendiğinde bu kez bir vade farkının hesaplanması.</span><span class="sxs-lookup"><span data-stu-id="d1413-293">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="d1413-294">Bitiş bakiyesi artık işlem sırasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d1413-294">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="d1413-295">İşlev [listesi. küçültme](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) biraz benzer ve aynı şekilde, `List.fold` `List.scan` ayrı bir Biriktiricinin etrafında geçiş yerine `List.reduce` iki bağımsız değişken alan bir işlev alır, ancak bu bağımsız değişkenlerden biri yalnızca bir değil, bu bağımsız değişkenlerden biri de, hesaplamanın ara sonucunu depoladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d1413-295">The function [List.reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="d1413-296">`List.reduce` ilk iki liste öğesinde çalışmaya başlar ve sonra işlemin sonucunu Next öğesiyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1413-296">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="d1413-297">Kendi türüne sahip ayrı bir biriktiricidir çünkü, `List.reduce` `List.fold` yalnızca biriktiricidir ve öğe türü aynı türde olduğunda ' nin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1413-297">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="d1413-298">Aşağıdaki kod öğesinin kullanımını gösterir `List.reduce` .</span><span class="sxs-lookup"><span data-stu-id="d1413-298">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="d1413-299">`List.reduce` Belirtilen listede öğe yoksa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d1413-299">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="d1413-300">Aşağıdaki kodda, lambda ifadesine yapılan ilk çağrıya 2 ve 4 bağımsız değişkenleri verilir ve 6, sonraki çağrıya ise 6 ve 10 bağımsız değişkenleri verilir, dolayısıyla sonuç 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="d1413-300">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="d1413-301">Listeler ve diğer koleksiyon türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d1413-301">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="d1413-302">`List`Modülü, hem sıralara hem de dizilere dönüştürme için işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1413-302">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="d1413-303">Bir diziye veya bir diziye dönüştürmek için [List. toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) veya [List. ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-303">To convert to or from a sequence, use [List.toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) or [List.ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq).</span></span> <span data-ttu-id="d1413-304">Bir diziye veya bir diziyi dönüştürmek için [List. ToArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) veya [List. ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1413-304">To convert to or from an array, use [List.toArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) or [List.ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="d1413-305">Ek Işlemler</span><span class="sxs-lookup"><span data-stu-id="d1413-305">Additional Operations</span></span>

<span data-ttu-id="d1413-306">Listelerle ilgili ek işlemler hakkında daha fazla bilgi için bkz. kitaplık başvurusu konu [listesi modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="d1413-306">For information about additional operations on lists, see the library reference topic [List Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1413-307">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1413-307">See also</span></span>

- [<span data-ttu-id="d1413-308">F # dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="d1413-308">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="d1413-309">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="d1413-309">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="d1413-310">Diziler</span><span class="sxs-lookup"><span data-stu-id="d1413-310">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="d1413-311">Diziler</span><span class="sxs-lookup"><span data-stu-id="d1413-311">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="d1413-312">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d1413-312">Options</span></span>](options.md)
