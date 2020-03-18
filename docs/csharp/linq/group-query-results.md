---
title: Grup sorgu sonuçları (C#'da LINQ)
description: C#'da LINQ kullanarak sonuçları nasıl gruplatacağız öğrenin.
ms.date: 12/01/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: 577a358c31fcf5346e7aab7a2e2b6be10fd1beff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688468"
---
# <a name="group-query-results"></a><span data-ttu-id="c0096-103">Sorgu sonuçlarını gruplandırma</span><span class="sxs-lookup"><span data-stu-id="c0096-103">Group query results</span></span>

<span data-ttu-id="c0096-104">Gruplandırma, LINQ'un en güçlü özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="c0096-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="c0096-105">Aşağıdaki örnekler, verilerin çeşitli şekillerde nasıl gruplatını göstereceğimi gösterir:</span><span class="sxs-lookup"><span data-stu-id="c0096-105">The following examples show how to group data in various ways:</span></span>

- <span data-ttu-id="c0096-106">Tek bir mülkle.</span><span class="sxs-lookup"><span data-stu-id="c0096-106">By a single property.</span></span>

- <span data-ttu-id="c0096-107">Bir dize özelliğinin ilk harfiyle.</span><span class="sxs-lookup"><span data-stu-id="c0096-107">By the first letter of a string property.</span></span>

- <span data-ttu-id="c0096-108">Sayısal olarak hesaplanmış bir aralıkla.</span><span class="sxs-lookup"><span data-stu-id="c0096-108">By a computed numeric range.</span></span>

- <span data-ttu-id="c0096-109">Boolean edicate veya başka bir ifade ile.</span><span class="sxs-lookup"><span data-stu-id="c0096-109">By Boolean predicate or other expression.</span></span>

- <span data-ttu-id="c0096-110">Bileşik bir anahtarla.</span><span class="sxs-lookup"><span data-stu-id="c0096-110">By a compound key.</span></span>

<span data-ttu-id="c0096-111">Buna ek olarak, son iki sorgu, sonuçlarını yalnızca öğrencinin adını ve soyadını içeren yeni bir anonim türe yansıttır.</span><span class="sxs-lookup"><span data-stu-id="c0096-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="c0096-112">Daha fazla bilgi için [grup yan tümcesi'ne](../language-reference/keywords/group-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c0096-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0096-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0096-113">Example</span></span>

<span data-ttu-id="c0096-114">Bu konudaki tüm örnekleraşağıdaki yardımcı sınıfları ve veri kaynaklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0096-114">All the examples in this topic use the following helper classes and data sources.</span></span>

[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]

## <a name="example"></a><span data-ttu-id="c0096-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0096-115">Example</span></span>

<span data-ttu-id="c0096-116">Aşağıdaki örnek, grup anahtarı olarak öğenin tek bir özelliğini kullanarak kaynak öğelerinin nasıl gruplayaalın yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0096-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="c0096-117">Bu durumda `string`anahtar, öğrencinin soyadıdır.</span><span class="sxs-lookup"><span data-stu-id="c0096-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="c0096-118">Anahtar için bir alt dize kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c0096-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="c0096-119">Gruplandırma işlemi türü için varsayılan eşitlik karşılayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0096-119">The grouping operation uses the default equality comparer for the type.</span></span>

<span data-ttu-id="c0096-120">Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0096-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c0096-121">Yöntemdeki çağrı deyimini `sc.GroupBySingleProperty()`' ' ' olarak değiştirin `Main`</span><span class="sxs-lookup"><span data-stu-id="c0096-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>

[!code-csharp[csProgGuideLINQ#17](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]

## <a name="example"></a><span data-ttu-id="c0096-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0096-122">Example</span></span>

<span data-ttu-id="c0096-123">Aşağıdaki örnek, grup anahtarı için nesnenin özelliği dışında bir şey kullanarak kaynak öğelerinasıl gruplendirilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0096-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="c0096-124">Bu örnekte anahtar, öğrencinin soyadının ilk harfidir.</span><span class="sxs-lookup"><span data-stu-id="c0096-124">In this example, the key is the first letter of the student's last name.</span></span>

<span data-ttu-id="c0096-125">Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0096-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c0096-126">Yöntemdeki çağrı deyimini `sc.GroupBySubstring()`' ' ' olarak değiştirin `Main`</span><span class="sxs-lookup"><span data-stu-id="c0096-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>

[!code-csharp[csProgGuideLINQ#18](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]

## <a name="example"></a><span data-ttu-id="c0096-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0096-127">Example</span></span>

<span data-ttu-id="c0096-128">Aşağıdaki örnekte, grup anahtarı olarak sayısal aralık kullanılarak kaynak öğelerinin nasıl gruplaşılaşı yapılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c0096-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="c0096-129">Sorgu daha sonra sonuçları yalnızca ad ve soyad ve öğrencinin ait olduğu yüzdelik aralığını içeren anonim bir türe dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c0096-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="c0096-130">Sonuçları görüntülemek için tam `Student` nesneyi kullanmak gerekli olmadığından anonim bir tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c0096-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="c0096-131">`GetPercentile`öğrencinin ortalama puanına göre yüzdelik bir artış hesaplayan bir yardımcı işlevdir.</span><span class="sxs-lookup"><span data-stu-id="c0096-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="c0096-132">Yöntem 0 ile 10 arasında bir arayla bir sonda döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0096-132">The method returns an integer between 0 and 10.</span></span>

[!code-csharp[csProgGuideLINQ#50](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]

<span data-ttu-id="c0096-133">Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0096-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c0096-134">Yöntemdeki çağrı deyimini `sc.GroupByRange()`' ' ' olarak değiştirin `Main`</span><span class="sxs-lookup"><span data-stu-id="c0096-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>

[!code-csharp[csProgGuideLINQ#19](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]

## <a name="example"></a><span data-ttu-id="c0096-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0096-135">Example</span></span>

<span data-ttu-id="c0096-136">Aşağıdaki örnek, boolean karşılaştırma ifadesini kullanarak kaynak öğelerinin nasıl gruplandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0096-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="c0096-137">Bu örnekte, Boolean ifadesi bir öğrencinin ortalama sınav puanının 75'ten fazla olup olmadığını test eder.</span><span class="sxs-lookup"><span data-stu-id="c0096-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="c0096-138">Önceki örneklerde olduğu gibi, tam kaynak öğesi gerekli olmadığından sonuçlar anonim bir türe yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="c0096-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="c0096-139">Anonim türdeki özelliklerin `Key` üyeüzerinde özellik haline geldiğini ve sorgu yürütüldüğünde adıyla erişilenebileni unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c0096-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>

<span data-ttu-id="c0096-140">Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0096-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c0096-141">Yöntemdeki çağrı deyimini `sc.GroupByBoolean()`' ' ' olarak değiştirin `Main`</span><span class="sxs-lookup"><span data-stu-id="c0096-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>

[!code-csharp[csProgGuideLINQ#20](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]

## <a name="example"></a><span data-ttu-id="c0096-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0096-142">Example</span></span>

<span data-ttu-id="c0096-143">Aşağıdaki örnek, birden çok değer içeren bir anahtarı kapsüllemek için anonim bir türün nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0096-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="c0096-144">Bu örnekte, ilk anahtar değeri öğrencinin soyadının ilk harfidir.</span><span class="sxs-lookup"><span data-stu-id="c0096-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="c0096-145">İkinci anahtar değer, öğrencinin ilk sınavda 85 üzerinden puan alıp almadığına dair bir Boolean'dır.</span><span class="sxs-lookup"><span data-stu-id="c0096-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="c0096-146">Gruplara anahtardaki herhangi bir özelliğe göre sipariş verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0096-146">You can order the groups by any property in the key.</span></span>

<span data-ttu-id="c0096-147">Aşağıdaki yöntemi sınıfa `StudentClass` yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0096-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="c0096-148">Yöntemdeki çağrı deyimini `sc.GroupByCompositeKey()`' ' ' olarak değiştirin `Main`</span><span class="sxs-lookup"><span data-stu-id="c0096-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>

[!code-csharp[csProgGuideLINQ#21](~/samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]

## <a name="see-also"></a><span data-ttu-id="c0096-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0096-149">See also</span></span>

- <xref:System.Linq.Enumerable.GroupBy%2A>
- <xref:System.Linq.IGrouping%602>
- [<span data-ttu-id="c0096-150">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c0096-150">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="c0096-151">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="c0096-151">group clause</span></span>](../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="c0096-152">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="c0096-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="c0096-153">Gruplandırma İşleminde Alt Sorgu Yap</span><span class="sxs-lookup"><span data-stu-id="c0096-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="c0096-154">İç Içe Grup Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0096-154">Create a Nested Group</span></span>](create-a-nested-group.md)
- [<span data-ttu-id="c0096-155">Verileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="c0096-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
