---
title: Sorgu sonuçlarını gruplandırma (C# üzerinde LINQ)
description: Grup C# içinde LINQ kullanarak sonuçları öğrenin.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857859"
---
# <a name="group-query-results"></a><span data-ttu-id="1a3bc-103">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="1a3bc-103">Group query results</span></span>

<span data-ttu-id="1a3bc-104">Gruplandırma LINQ en güçlü özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="1a3bc-105">Aşağıdaki örnekler, çeşitli yollarla verilerin nasıl gruplanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1a3bc-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="1a3bc-106">Tek bir özelliğe göre.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-106">By a single property.</span></span>

- <span data-ttu-id="1a3bc-107">Bir dize özelliği ilk harfi ile.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="1a3bc-108">Tarafından hesaplanan bir sayısal aralık.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-108">By a computed numeric range.</span></span>

- <span data-ttu-id="1a3bc-109">Boole koşulu veya diğer ifade.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="1a3bc-110">Bileşik bir anahtar.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-110">By a compound key.</span></span>

<span data-ttu-id="1a3bc-111">Ayrıca, son iki sorguların sonuçlarını Öğrenci ilk yalnızca içeriyor ve Soyadı yeni bir anonim tür proje.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="1a3bc-112">Daha fazla bilgi için [group yan tümcesi](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1a3bc-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="1a3bc-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a3bc-113">Example</span></span>

<span data-ttu-id="1a3bc-114">Bu konunun tüm örnekleri aşağıdaki yardımcı sınıflar ve veri kaynaklarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="1a3bc-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a3bc-115">Example</span></span>

<span data-ttu-id="1a3bc-116">Aşağıdaki örnek, tek bir özellik öğesinin Grup anahtarı kullanarak kaynak öğeleri gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="1a3bc-117">Bu durumda bu anahtar, bir `string`, öğrencinin soyadı.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="1a3bc-118">Anahtar için bir alt dizesi kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="1a3bc-119">Gruplandırma işlemi türü için varsayılan eşitlik karşılaştırıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="1a3bc-120">Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="1a3bc-121">Arama deyiminde değiştirme `Main` yönteme `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="1a3bc-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a3bc-122">Example</span></span>

<span data-ttu-id="1a3bc-123">Aşağıdaki örnek, nesnenin bir özelliğini dışında bir şey için Grup anahtarı kullanarak kaynak öğeleri gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="1a3bc-124">Bu örnekte, öğrencinin son adının ilk harfi bir anahtardır.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="1a3bc-125">Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="1a3bc-126">Arama deyiminde değiştirme `Main` yönteme `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="1a3bc-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a3bc-127">Example</span></span>

<span data-ttu-id="1a3bc-128">Aşağıdaki örnek, sayısal aralık bir Grup anahtarı kullanarak kaynak öğeleri gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="1a3bc-129">Sorgu sonuçları yalnızca ilk ve son adı ve Öğrenci ait olduğu yüzdebirlik aralığı içeren bir anonim tür ardından yansıtıyor.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="1a3bc-130">Anonim bir tür, tam olarak kullanmak için gerekli olmadığından kullanılan `Student` sonuçları görüntülemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="1a3bc-131">`GetPercentile` yüzde hesaplayan bir yardımcı işlevi, öğrencinin ortalama puanına göre temel alır.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="1a3bc-132">Yöntemi, 0 ile 10 arasında bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="1a3bc-133">Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="1a3bc-134">Arama deyiminde değiştirme `Main` yönteme `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="1a3bc-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a3bc-135">Example</span></span>

<span data-ttu-id="1a3bc-136">Aşağıdaki örnek, bir Boolean karşılaştırma ifadesi kullanarak kaynak öğeleri gruplandırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="1a3bc-137">Bu örnekte, bir öğrencinin ortalama sınavı puanı 75 büyük olup Boole ifadesi test eder.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="1a3bc-138">Önceki örneklerde olduğu gibi tam kaynak öğesi gerekli değildir çünkü sonuçları anonim bir tür yansıtılan.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="1a3bc-139">Anonim tür özellikleri Özellikler üzerinde hale geleceğini unutmayın `Key` üyesi ve sorgu yürütüldüğünde adı tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="1a3bc-140">Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="1a3bc-141">Arama deyiminde değiştirme `Main` yönteme `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="1a3bc-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a3bc-142">Example</span></span>

<span data-ttu-id="1a3bc-143">Aşağıdaki örnek, birden çok değer içeren bir anahtar yalıtılacak anonim bir tür kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="1a3bc-144">Bu örnekte, ilk anahtar değeri öğrencinin Soyadı İlk harfidir.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="1a3bc-145">İkinci anahtar değeri Öğrenci 85 üzerinde ilk sınavı üzerinde puanlanmış olup olmadığını belirten Boolean bir değer var.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="1a3bc-146">Grupları anahtarında herhangi bir özelliğe göre sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="1a3bc-147">Aşağıdaki yönteme yapıştırın `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="1a3bc-148">Arama deyiminde değiştirme `Main` yönteme `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="1a3bc-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a3bc-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [<span data-ttu-id="1a3bc-150">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1a3bc-150">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="1a3bc-151">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="1a3bc-151">group clause</span></span>](../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="1a3bc-152">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="1a3bc-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="1a3bc-153">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="1a3bc-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="1a3bc-154">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a3bc-154">Create a Nested Group</span></span>](create-a-nested-group.md)
- [<span data-ttu-id="1a3bc-155">Verileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="1a3bc-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
