---
title: Listeler (F#)
description: F# listeleri, öğeleri aynı türde sıralı, sabit bir dizi hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: b48bf04f5ec490b49e63462affc0d4eadebe10ef
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50201630"
---
# <a name="lists"></a><span data-ttu-id="75356-103">Listeler</span><span class="sxs-lookup"><span data-stu-id="75356-103">Lists</span></span>

> [!NOTE]
<span data-ttu-id="75356-104">Bu makaledeki API başvuru bağlantıları için MSDN sürer.</span><span class="sxs-lookup"><span data-stu-id="75356-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="75356-105">Docs.microsoft.com API başvuru tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="75356-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="75356-106">F# listedeki öğeleri aynı türde sıralı, sabit dizisidir.</span><span class="sxs-lookup"><span data-stu-id="75356-106">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="75356-107">Listeler temel işlemleri gerçekleştirmek için işlevleri kullanmak [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="75356-107">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="75356-108">Oluşturma ve başlatma listeler</span><span class="sxs-lookup"><span data-stu-id="75356-108">Creating and Initializing Lists</span></span>

<span data-ttu-id="75356-109">Bir liste öğeleri noktalı virgülle ayrılmış ve kod aşağıdaki satırda gösterildiği gibi köşeli parantezler içinde out açıkça listeleyerek tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75356-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="75356-110">Satır sonları öğeler arasındaki de koyabilirsiniz, bu durumda noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="75356-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="75356-111">İkinci sözdizimi daha okunabilir bir kod öğesi başlatma ifadeleri uzun olduğunda ya da her öğe için bir açıklama eklemek istediğiniz neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="75356-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="75356-112">Normalde, tüm liste öğeleri aynı türde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75356-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="75356-113">Öğeleri olan öğeler bir taban türü olmasını sağlayabilirsiniz belirtilir listesini türetilmiş bir özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="75356-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="75356-114">Aşağıdaki kabul edilebilir, bu nedenle çünkü her ikisi de `Button` ve `CheckBox` öğesinden türetilen `Control`.</span><span class="sxs-lookup"><span data-stu-id="75356-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="75356-115">Aralık işleci tarafından ayrılmış tamsayı tarafından gösterilen bir aralık kullanarak liste öğelerini de tanımlayabilirsiniz (`..`), aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="75356-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="75356-116">Boş bir liste, bir çift köşeli ayraç ile bunların arasında bir şey tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="75356-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="75356-117">Bir sıralama ifadesi, bir liste oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75356-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="75356-118">Bkz: [Sequence ifadeleri](sequences.md#sequence-expressions) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="75356-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="75356-119">Örneğin, aşağıdaki kod, tamsayılar kareler listesini 1'den 10'a oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="75356-120">Listelerle çalışmak için işleçleri</span><span class="sxs-lookup"><span data-stu-id="75356-120">Operators for Working with Lists</span></span>

<span data-ttu-id="75356-121">Kullanarak liste öğelerini ekleyebilirsiniz `::` (olumsuz) işleci.</span><span class="sxs-lookup"><span data-stu-id="75356-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="75356-122">Varsa `list1` olduğu `[2; 3; 4]`, aşağıdaki kod oluşturur `list2` olarak `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="75356-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="75356-123">Kullanarak uyumlu türleri olan listeleri bitiştirebilirsiniz `@` işleci, aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="75356-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="75356-124">Varsa `list1` olduğu `[2; 3; 4]` ve `list2` olduğu `[100; 2; 3; 4]`, bu kod oluşturur `list3` olarak `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="75356-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="75356-125">Liste işlemleri gerçekleştirmek için işlevleri kullanılabilir [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="75356-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="75356-126">F# listelerinde sabit olduğundan, herhangi bir değiştirme işlemi varolan listelerini değiştirmek yerine yeni bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="75356-127">F# listeleri, yani yalnızca listenin başındaki erişim işlemleri O(1), tek bağlantılı liste olarak uygulanır ve öğe erişimi, O ise (*n*).</span><span class="sxs-lookup"><span data-stu-id="75356-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="75356-128">Özellikler</span><span class="sxs-lookup"><span data-stu-id="75356-128">Properties</span></span>

<span data-ttu-id="75356-129">Liste türü, aşağıdaki özellikleri destekler:</span><span class="sxs-lookup"><span data-stu-id="75356-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="75356-130">Özellik</span><span class="sxs-lookup"><span data-stu-id="75356-130">Property</span></span>|<span data-ttu-id="75356-131">Tür</span><span class="sxs-lookup"><span data-stu-id="75356-131">Type</span></span>|<span data-ttu-id="75356-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="75356-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="75356-133">HEAD</span><span class="sxs-lookup"><span data-stu-id="75356-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="75356-134">İlk öğe.</span><span class="sxs-lookup"><span data-stu-id="75356-134">The first element.</span></span>|
|[<span data-ttu-id="75356-135">boş</span><span class="sxs-lookup"><span data-stu-id="75356-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="75356-136">Bir statik özellik uygun türde boş bir liste döndürür.</span><span class="sxs-lookup"><span data-stu-id="75356-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="75356-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="75356-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="75356-138">`true` listeye öğe varsa.</span><span class="sxs-lookup"><span data-stu-id="75356-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="75356-139">Öğesi</span><span class="sxs-lookup"><span data-stu-id="75356-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="75356-140">(Sıfır tabanlı) belirtilen dizindeki öğe.</span><span class="sxs-lookup"><span data-stu-id="75356-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="75356-141">Uzunluğu</span><span class="sxs-lookup"><span data-stu-id="75356-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="75356-142">Öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="75356-142">The number of elements.</span></span>|
|[<span data-ttu-id="75356-143">Tail</span><span class="sxs-lookup"><span data-stu-id="75356-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="75356-144">İlk öğe olmadan listesi.</span><span class="sxs-lookup"><span data-stu-id="75356-144">The list without the first element.</span></span>|
<span data-ttu-id="75356-145">Bu özellikler kullanmanın bazı örnekler aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75356-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="75356-146">Listeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="75356-146">Using Lists</span></span>

<span data-ttu-id="75356-147">Programlama listeleriyle karmaşık işlemleri az miktarda kod ile sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="75356-148">Bu bölümde, işlevsel programlama için önemli olan listelerde yaygın işlemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75356-148">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="75356-149">Özyineleme listeleri</span><span class="sxs-lookup"><span data-stu-id="75356-149">Recursion with Lists</span></span>

<span data-ttu-id="75356-150">Listeleri için yinelemeli teknikler programlama benzersiz olarak uygundur.</span><span class="sxs-lookup"><span data-stu-id="75356-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="75356-151">Her bir liste öğesi üzerinde gerçekleştirilen bir işlem göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="75356-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="75356-152">Listenin başındaki üzerinde çalışan ve ardından özgün listedeki ilk öğe olmadan oluşan küçük bir listedir listenin sonu geçirerek bu yinelemeli olarak yapın, özyineleme sonraki düzeye yeniden.</span><span class="sxs-lookup"><span data-stu-id="75356-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="75356-153">Böyle bir özyinelemeli işlevi yazmak için simgeler işlecini kullanın (`::`) desen eşleştirme içinde sağlayan tail listesini baş ayırmak.</span><span class="sxs-lookup"><span data-stu-id="75356-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="75356-154">Aşağıdaki kod örneği, bir liste işlemleri gerçekleştiren bir özyinelemeli işlev uygulamak için desen eşleştirme kullan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75356-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="75356-155">Önceki kodun küçük listeler için iyi çalışır, ancak daha büyük listeler için yığın taşması.</span><span class="sxs-lookup"><span data-stu-id="75356-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="75356-156">Aşağıdaki kod, accumulator bağımsız değişken, özyinelemeli işlevler ile çalışmak için standart bir yöntemi kullanarak bu kodu geliştirir.</span><span class="sxs-lookup"><span data-stu-id="75356-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="75356-157">Yığın alanı kaydeder işlevi tail özyinelemeli accumulator bağımsız değişken kullanımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="75356-158">İşlev `RemoveAllMultiples` iki liste götüren bir özyinelemeli işlevdir.</span><span class="sxs-lookup"><span data-stu-id="75356-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="75356-159">İlk liste, katları kaldırılacak sayıları içeren ve ikinci listesi sayıları kaldırılacağı listesidir.</span><span class="sxs-lookup"><span data-stu-id="75356-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="75356-160">Aşağıdaki örnek kodda, tüm olmayan-asal sayıları asal sayıları listesini sonucu olarak bırakarak listeden ortadan kaldırmak için bu özyinelemeli işlev kullanır.</span><span class="sxs-lookup"><span data-stu-id="75356-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="75356-161">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-161">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="75356-162">Modül işlevleri</span><span class="sxs-lookup"><span data-stu-id="75356-162">Module Functions</span></span>

<span data-ttu-id="75356-163">[List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) liste öğelerini erişim işlevleri sunar.</span><span class="sxs-lookup"><span data-stu-id="75356-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="75356-164">Head öğesi, en hızlı ve kolay erişim ' dir.</span><span class="sxs-lookup"><span data-stu-id="75356-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="75356-165">Özelliğini kullanın [baş](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) veya modül işlevi [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="75356-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="75356-166">Kuyruk listesini kullanarak erişebileceğiniz [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) özelliği veya [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) işlevi.</span><span class="sxs-lookup"><span data-stu-id="75356-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="75356-167">Dizine göre bir öğeyi bulmak için kullanın [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) işlevi.</span><span class="sxs-lookup"><span data-stu-id="75356-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="75356-168">`List.nth` Listeyi dikkatle inceler.</span><span class="sxs-lookup"><span data-stu-id="75356-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="75356-169">Bu nedenle, O olduğu (*n*).</span><span class="sxs-lookup"><span data-stu-id="75356-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="75356-170">Kodunuzu kullanıyorsa `List.nth` sıklıkla bir dizi yerine bir liste kullanarak düşünmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75356-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="75356-171">Öğe erişimi, diziler O(1) ' dir.</span><span class="sxs-lookup"><span data-stu-id="75356-171">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="75356-172">Boole işlemlerini listeler</span><span class="sxs-lookup"><span data-stu-id="75356-172">Boolean Operations on Lists</span></span>

<span data-ttu-id="75356-173">[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) işlevi, bir liste herhangi bir öğe olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="75356-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="75356-174">[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) işlevi geçerli bir Boolean test listesini döndürür ve öğelerine `true` herhangi bir öğeyi test karşılıyorsa.</span><span class="sxs-lookup"><span data-stu-id="75356-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="75356-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) benzer, ancak iki listelerindeki öğelerin art arda gelen çiftlerini çalışır.</span><span class="sxs-lookup"><span data-stu-id="75356-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="75356-176">Aşağıdaki kod kullanımını gösterir `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="75356-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="75356-177">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-177">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="75356-178">Aşağıdaki örnek, kullanımını gösterir `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="75356-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="75356-179">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-179">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="75356-180">Kullanabileceğiniz [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) tüm liste öğelerinin bir koşulu karşılayıp karşılamadığını sınamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="75356-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="75356-181">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-181">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="75356-182">Benzer şekilde, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) karşılık gelen konumlarda iki listelerindeki tüm öğeleri içeren her bir öğe çiftinin bir Boole ifadesi uygun olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="75356-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="75356-183">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-183">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="75356-184">Sıralama işlemleri listeler</span><span class="sxs-lookup"><span data-stu-id="75356-184">Sort Operations on Lists</span></span>

<span data-ttu-id="75356-185">[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), ve [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) işlevleri sıralama listeler.</span><span class="sxs-lookup"><span data-stu-id="75356-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="75356-186">Sıralama işlevini kullanmak için bu üç işlevlerin belirler.</span><span class="sxs-lookup"><span data-stu-id="75356-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="75356-187">`List.sort` Varsayılan genel karşılaştırma kullanır.</span><span class="sxs-lookup"><span data-stu-id="75356-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="75356-188">Genel karşılaştırma genel karşılaştırma işleve göre genel işleçleri, değerleri karşılaştırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="75356-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="75356-189">Çok çeşitli gibi basit sayısal türler, diziler, kayıtları, ayrılmış birleşimler, listeler, diziler ve uygulayan herhangi bir tür öğe türleri ile verimli bir şekilde çalışır `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="75356-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="75356-190">Türleri uygulayan `System.IComparable`, genel karşılaştırma kullanır `System.IComparable.CompareTo()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="75356-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="75356-191">Genel karşılaştırma ayrıca dizeleri ile çalışır, ancak kültüre bağlı bir sıralama düzeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="75356-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="75356-192">Genel karşılaştırma işlevini türleri gibi desteklenmeyen türler üzerinde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75356-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="75356-193">Ayrıca, varsayılan genel karşılaştırma performansını küçük yapılandırılmış türleri için en iyi seçenektir; Karşılaştırma ve sık sıralanmış gereken büyük yapılandırılmış türleri için uygulamayı düşünün `System.IComparable` verimli uygulaması sağlayarak `System.IComparable.CompareTo()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="75356-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="75356-194">`List.sortBy` Sıralama ölçütü kullanılan bir değer döndüren bir işlev alır ve `List.sortWith` bir karşılaştırma işlevi bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="75356-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="75356-195">Bu ikinci iki İşlevler, karşılaştırma desteklemez veya karşılaştırma kültüre duyarlı dize olduğu gibi daha karmaşık karşılaştırma semantiği gerektirdiğinde türleriyle çalışırken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="75356-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="75356-196">Aşağıdaki örnek, kullanımını gösterir `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="75356-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="75356-197">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-197">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="75356-198">Aşağıdaki örnek, kullanımını gösterir `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="75356-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="75356-199">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-199">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="75356-200">Sonraki örnek, kullanımını gösterir `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="75356-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="75356-201">Bu örnekte, özel bir karşılaştırma işlevi `compareWidgets` önce bir alan karşılaştırmak için kullanılan özel bir tür ve başka bir zaman ilk alan değerlerini eşit.</span><span class="sxs-lookup"><span data-stu-id="75356-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="75356-202">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-202">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="75356-203">Listelerde arama işlemleri</span><span class="sxs-lookup"><span data-stu-id="75356-203">Search Operations on Lists</span></span>

<span data-ttu-id="75356-204">Çok sayıda arama işlemleri listeler için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="75356-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="75356-205">Basit, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), belirli bir koşul ile eşleşen ilk öğe bulmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="75356-206">Aşağıdaki kod örneği, kullanımını gösterir `List.find` bölünebilir 5 listedeki ilk numarası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="75356-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="75356-207">Sonuç 5'tir.</span><span class="sxs-lookup"><span data-stu-id="75356-207">The result is 5.</span></span>

<span data-ttu-id="75356-208">İlk öğeleri dönüştürülür, çağrı [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), bir işlev, alan bir seçenek verir ve ilk seçenek arar değeri olan `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="75356-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="75356-209">Öğe döndürmek yerine `List.pick` sonucunu döndürür `x`.</span><span class="sxs-lookup"><span data-stu-id="75356-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="75356-210">Eşleşen hiçbir öğe bulunamazsa `List.pick` oluşturur `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="75356-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="75356-211">Aşağıdaki kod kullanımını gösterir `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="75356-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="75356-212">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-212">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="75356-213">Arama işlemleri, başka bir grup [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) ve ilgili işlevleri, bir seçenek değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="75356-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="75356-214">`List.tryFind` İşlevi bu tür bir öğe varsa bir koşulu karşılayan bir liste, ancak seçenek değeri ilk öğeyi döndürür `None` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="75356-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="75356-215">Değişim [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) , öğenin yerine bulunması durumunda, öğenin dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="75356-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="75356-216">Bu işlevler, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75356-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="75356-217">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-217">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="75356-218">Aritmetik işlemler listesi</span><span class="sxs-lookup"><span data-stu-id="75356-218">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="75356-219">Toplam ve ortalama gibi yaygın aritmetik işlemleri yerleşik olarak [List Modülü](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="75356-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="75356-220">Çalışmak için [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), liste öğesi türünü desteklemelidir `+` işleci ve sıfır değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="75356-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="75356-221">Tüm yerleşik aritmetik türler bu koşulları karşılayan.</span><span class="sxs-lookup"><span data-stu-id="75356-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="75356-222">Çalışmak için [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), öğe türü olmadan tam sayı türleri dışlar ancak kayan nokta türleri için sağlayan bir geri kalan bölümü desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="75356-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="75356-223">[List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) ve [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) işlevler bir işlev bir parametre olarak alır ve bu işlevin sonuçlarını Topla veya ortalama değerleri hesaplamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75356-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="75356-224">Aşağıdaki kod kullanımını gösterir `List.sum`, `List.sumBy`, ve `List.average`.</span><span class="sxs-lookup"><span data-stu-id="75356-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="75356-225">Çıktı `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="75356-225">The output is `1.000000`.</span></span>

<span data-ttu-id="75356-226">Aşağıdaki kod kullanımını gösterir `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="75356-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="75356-227">Çıktı `5.5`.</span><span class="sxs-lookup"><span data-stu-id="75356-227">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="75356-228">Listeler ve diziler</span><span class="sxs-lookup"><span data-stu-id="75356-228">Lists and Tuples</span></span>

<span data-ttu-id="75356-229">Diziler içeren listeleri zip tarafından yönetilebilir ve işlevleri sıkıştırmasını açın.</span><span class="sxs-lookup"><span data-stu-id="75356-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="75356-230">Bu işlevler, iki tek değerler listesi bir tanımlama grubu listesine birleştirebilir veya listelerini tek değerler bir diziler listesi ayırın.</span><span class="sxs-lookup"><span data-stu-id="75356-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="75356-231">En basit [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) işlevi iki tek öğeleri listesini alır ve tek bir kayıt düzeni çiftlerinin listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="75356-232">Başka bir sürümü [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), üç tek öğeleri listesini alır ve üç öğe içeren demetler tek bir listesini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="75356-233">Aşağıdaki kod örneği, kullanımını gösterir `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="75356-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="75356-234">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-234">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="75356-235">Aşağıdaki kod örneği, kullanımını gösterir `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="75356-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="75356-236">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-236">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="75356-237">Unzip sürümleri, buna karşılık gelen [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) ve [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), tanımlama gruplarının listesini alan ve getiren listeleri bir tanımlama grubu burada ilk liste her bir tanımlama grubunu ilk tüm öğeleri içeren ve ikinci liste, her tanımlama grubu ve benzeri ikinci öğe içerir.</span><span class="sxs-lookup"><span data-stu-id="75356-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="75356-238">Aşağıdaki kod örneği, kullanımını gösterir [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="75356-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="75356-239">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-239">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="75356-240">Aşağıdaki kod örneği, kullanımını gösterir [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="75356-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="75356-241">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-241">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="75356-242">Liste öğeleri üzerinde çalıştırma</span><span class="sxs-lookup"><span data-stu-id="75356-242">Operating on List Elements</span></span>

<span data-ttu-id="75356-243">F# çeşitli liste öğeleri üzerinde işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="75356-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="75356-244">En basit olan [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), listesini her bir öğede bir işlev çağrısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="75356-245">Çeşitlemeler içerir [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), iki listenin öğelerini bir işlem yapmanıza olanak sağlayan [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), olduğu gibi `List.iter` dışında her öğenin dizini olarak geçirilen bir her öğe için çağrılan işlev için bağımsız değişken ve [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), işlevselliğinin bir birleşimi olan `List.iter2` ve `List.iteri`.</span><span class="sxs-lookup"><span data-stu-id="75356-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="75356-246">Aşağıdaki kod örneği, bu işlevler gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="75356-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="75356-247">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-247">The output is as follows:</span></span>

```
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

<span data-ttu-id="75356-248">Liste öğeleri dönüştüren başka bir sık kullanılan işlev [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), her bir liste öğesine bir işlev uygulamak ve tüm sonuçları yeni bir liste olarak yerleştirmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="75356-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) ve [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) birden çok listelerini Al farklılıklar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="75356-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="75356-250">Ayrıca [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) ve [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), öğe ek olarak, her öğenin dizinini geçirilecek işlevi gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="75356-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="75356-251">Arasındaki tek fark `List.mapi2` ve `List.mapi` olan `List.mapi2` iki liste ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="75356-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="75356-252">Aşağıdaki örnekte gösterilmiştir [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="75356-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="75356-253">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-253">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="75356-254">Aşağıdaki örnek kullanımını gösterir `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="75356-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="75356-255">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-255">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="75356-256">Aşağıdaki örnek kullanımını gösterir `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="75356-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="75356-257">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-257">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="75356-258">Aşağıdaki örnek kullanımını gösterir `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="75356-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="75356-259">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-259">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="75356-260">Aşağıdaki örnek kullanımını gösterir `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="75356-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="75356-261">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-261">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="75356-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) benzer `List.map`, her öğe bir liste oluşturur ve bu listeler, son bir liste olarak bitiştirilir.</span><span class="sxs-lookup"><span data-stu-id="75356-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="75356-263">Aşağıdaki kodda, listenin her öğesinin üç sayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="75356-264">Bunların tümünü tek listede toplanır.</span><span class="sxs-lookup"><span data-stu-id="75356-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="75356-265">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-265">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="75356-266">Ayrıca [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), bir Boolean koşulu alır ve belirtilen koşulu karşılayan öğeleri içeren yeni bir liste oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="75356-267">Sonuç listesi `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="75356-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="75356-268">Bir harita ve filtresi bileşimi [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) , dönüştürme ve aynı anda öğeleri seçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="75356-269">`List.choose` bir seçenek listesini her öğeye döndürür ve işlevin seçenek değeri döndürüldüğünde yeni bir öğe için sonuçları listesi döndüren bir işlev uygular `Some`.</span><span class="sxs-lookup"><span data-stu-id="75356-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="75356-270">Aşağıdaki kod kullanımını gösterir `List.choose` büyük harfli bir sözcük dışında bir kelimelerin listesini seçin.</span><span class="sxs-lookup"><span data-stu-id="75356-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="75356-271">Çıktı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="75356-271">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="75356-272">Birden çok listelerde çalışma</span><span class="sxs-lookup"><span data-stu-id="75356-272">Operating on Multiple Lists</span></span>

<span data-ttu-id="75356-273">Listeleri birlikte katılabilir.</span><span class="sxs-lookup"><span data-stu-id="75356-273">Lists can be joined together.</span></span> <span data-ttu-id="75356-274">İki liste birine katılmak için kullanın [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="75356-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="75356-275">İkiden fazla listeleri katılmak için kullanın [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="75356-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="75356-276">Katlama ve tarama işlemleri</span><span class="sxs-lookup"><span data-stu-id="75356-276">Fold and Scan Operations</span></span>

<span data-ttu-id="75356-277">Tüm liste öğelerinin birbirine bazı listeleme işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="75356-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="75356-278">Katlama ve tarama işlemlerini gibidir `List.iter` ve `List.map` her öğe üzerinde bir işlevi çağırır, ancak bu işlemler adlı ek bir parametre sağlayın, *accumulator* , izleme bilgileri hesaplama.</span><span class="sxs-lookup"><span data-stu-id="75356-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="75356-279">Kullanım `List.fold` bir listede bir hesaplama gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="75356-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="75356-280">Aşağıdaki kod örneği, kullanımını gösterir [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) çeşitli işlemler gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="75356-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="75356-281">Listenin sonuna; accumulator `acc` hesaplama devam ettikçe boyunca geçirilen bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="75356-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="75356-282">İlk bağımsız değişken accumulator ve liste öğesi alır ve bu liste öğesi için hesaplama geçiş sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="75356-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="75356-283">İkinci bağımsız değişkeni accumulator ilk değeridir.</span><span class="sxs-lookup"><span data-stu-id="75356-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="75356-284">İşlev adı bir basamak sahip bu işlevlerin sürümleri, birden fazla listede çalışır.</span><span class="sxs-lookup"><span data-stu-id="75356-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="75356-285">Örneğin, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) iki liste üzerinde hesaplamalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="75356-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="75356-286">Aşağıdaki örnek, kullanımını gösterir `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="75356-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="75356-287">`List.fold` ve [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) içinde farklı `List.fold` ek parametresinin son değeri döndürür, ancak `List.scan` ekstra parametresiyle Ara değerlerini (birlikte, son değer) listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="75356-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="75356-288">Örneğin, bu işlevlerin her biri bir ters değişim içerir [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), sırayla farklıdır, listenin sonuna ve bağımsız değişkenlerin sırası.</span><span class="sxs-lookup"><span data-stu-id="75356-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="75356-289">Ayrıca, `List.fold` ve `List.foldBack` farklılıkları, sahip [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) ve [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), eşit uzunluktaki iki liste alır.</span><span class="sxs-lookup"><span data-stu-id="75356-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="75356-290">Her bir öğede yürüten işlev karşılık gelen öğelerle iki listelerin bazı eylemleri gerçekleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75356-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="75356-291">İki liste öğesi türlerinin bir listesi bir banka hesabı işlem tutarlarını içerir aşağıdaki örnekte olduğu gibi farklı olabilir ve diğer liste işlem türü bulunur: havale veya mevzuatı.</span><span class="sxs-lookup"><span data-stu-id="75356-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="75356-292">Toplama gibi bir hesaplama `List.fold` ve `List.foldBack` sonucu bazında geçişi bağımlı değildir çünkü aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="75356-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="75356-293">Aşağıdaki örnekte, `List.foldBack` bir listedeki öğeleri eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="75356-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="75356-294">Aşağıdaki örnek, banka hesabı örneği döndürür.</span><span class="sxs-lookup"><span data-stu-id="75356-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="75356-295">Yeni bir işlem türü eklendiğinde bu süre: bir ilgi hesaplaması.</span><span class="sxs-lookup"><span data-stu-id="75356-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="75356-296">Bitiş bakiyesi bazında işlemleri artık bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="75356-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="75356-297">İşlev [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) bakıma olan `List.fold` ve `List.scan`dışında ayrı bir accumulator etrafında geçirmek yerine `List.reduce` yerine öğe türünün iki bağımsız değişken alan bir işlev alır Bu bağımsız değişkenlerden biri yanı sıra tek bir hesaplama Ara sonuçlarını saklar anlamı accumulator görev yapar.</span><span class="sxs-lookup"><span data-stu-id="75356-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="75356-298">`List.reduce` ilk iki liste öğeleri üzerinde çalıştırılarak başlatılır ve ardından sonraki öğeye yanı sıra işleminin sonucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="75356-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="75356-299">Kendi türüne sahip ayrı bir accumulator olmadığından `List.reduce` yerine kullanılan `List.fold` yalnızca accumulator ve dizinin öğe türü aynı türe sahip olduğunda.</span><span class="sxs-lookup"><span data-stu-id="75356-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="75356-300">Aşağıdaki kod kullanımını gösterir `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="75356-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="75356-301">`List.reduce` sağlanan listesini hiçbir öğe içermeyen bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="75356-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="75356-302">Aşağıdaki kodda, ilk çağrı lambda ifadesine bağımsız değişkenleri 2 ve 4 verilir ve 6 döndürür ve 16 sonucu, bu nedenle sonraki çağrı bağımsız değişkenleri 6 ve 10 verilir.</span><span class="sxs-lookup"><span data-stu-id="75356-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="75356-303">Listeler ve diğer toplama türleri arasında dönüştürme</span><span class="sxs-lookup"><span data-stu-id="75356-303">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="75356-304">`List` Modülü ve dizileri hem dizileri Bu nesnelerden dönüştürme için işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="75356-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="75356-305">İçin veya bir dizi dönüştürmek için [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) veya [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="75356-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="75356-306">İçin veya bir diziden dönüştürmek için [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) veya [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="75356-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="75356-307">Ek işlemler</span><span class="sxs-lookup"><span data-stu-id="75356-307">Additional Operations</span></span>

<span data-ttu-id="75356-308">Listeleri üzerinde ek işlemler hakkında daha fazla bilgi için Kitaplık Başvurusu konusuna [Collections.List Modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="75356-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="75356-309">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75356-309">See also</span></span>

- [<span data-ttu-id="75356-310">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="75356-310">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="75356-311">F# Türleri</span><span class="sxs-lookup"><span data-stu-id="75356-311">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="75356-312">Diziler</span><span class="sxs-lookup"><span data-stu-id="75356-312">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="75356-313">Diziler</span><span class="sxs-lookup"><span data-stu-id="75356-313">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="75356-314">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="75356-314">Options</span></span>](options.md)
