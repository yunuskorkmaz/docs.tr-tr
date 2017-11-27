---
title: "Grup sorgu sonuçları"
description: "Sonuçları gruplandırmak nasıl."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: ca68cf96a2c27bbd1999d5445c14fc93e8e2566c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="group-query-results"></a><span data-ttu-id="5798b-104">Grup sorgu sonuçları</span><span class="sxs-lookup"><span data-stu-id="5798b-104">Group query results</span></span>

<span data-ttu-id="5798b-105">Gruplandırma LINQ en güçlü özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="5798b-105">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="5798b-106">Aşağıdaki örnekler, çeşitli şekillerde verilerin nasıl gruplanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5798b-106">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="5798b-107">Tek bir özelliğe göre.</span><span class="sxs-lookup"><span data-stu-id="5798b-107">By a single property.</span></span>  
  
-   <span data-ttu-id="5798b-108">Bir dize özelliği ilk harfi ile.</span><span class="sxs-lookup"><span data-stu-id="5798b-108">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="5798b-109">Hesaplanan sayısal bir aralık tarafından.</span><span class="sxs-lookup"><span data-stu-id="5798b-109">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="5798b-110">Boole koşulu veya diğer ifade.</span><span class="sxs-lookup"><span data-stu-id="5798b-110">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="5798b-111">Bileşik bir anahtar.</span><span class="sxs-lookup"><span data-stu-id="5798b-111">By a compound key.</span></span>  
  
 <span data-ttu-id="5798b-112">Ayrıca, son iki sorgu sonuçları Öğrenci ilk yalnızca içeren ve Soyadı yeni bir anonim tür yansıtın.</span><span class="sxs-lookup"><span data-stu-id="5798b-112">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="5798b-113">Daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5798b-113">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5798b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5798b-114">Example</span></span>  
 <span data-ttu-id="5798b-115">Bu konudaki tüm örnekleri aşağıdaki yardımcı sınıfları ve veri kaynaklarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5798b-115">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="5798b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5798b-116">Example</span></span>  
 <span data-ttu-id="5798b-117">Aşağıdaki örnek Grup anahtarı olarak öğesinin tek bir özelliğini kullanarak kaynağı öğeleri gruplandırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5798b-117">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="5798b-118">Bu durumda anahtarıdır bir `string`, öğrencinin son adı.</span><span class="sxs-lookup"><span data-stu-id="5798b-118">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="5798b-119">Anahtar için bir alt dizesi kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5798b-119">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="5798b-120">Gruplama işleminin türü için varsayılan eşitlik karşılaştırıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5798b-120">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="5798b-121">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5798b-121">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="5798b-122">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="5798b-122">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="5798b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="5798b-123">Example</span></span>  
 <span data-ttu-id="5798b-124">Aşağıdaki örnek, nesnenin bir özelliğini dışında bir şey için Grup anahtarı kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5798b-124">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="5798b-125">Bu örnekte, öğrencinin son adının ilk harfi anahtardır.</span><span class="sxs-lookup"><span data-stu-id="5798b-125">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="5798b-126">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5798b-126">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="5798b-127">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="5798b-127">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="5798b-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="5798b-128">Example</span></span>  
 <span data-ttu-id="5798b-129">Aşağıdaki örnek, sayısal bir aralık bir Grup anahtarı kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5798b-129">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="5798b-130">Sorgu sonuçları yalnızca ilk ve son adı ve Öğrenci ait olduğu yüzdebirlik aralığı içeren bir anonim tür sonra projeleri.</span><span class="sxs-lookup"><span data-stu-id="5798b-130">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="5798b-131">Anonim bir tür tam kullanmak için gerekli olmadığı için kullanılan `Student` sonuçları görüntülemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="5798b-131">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="5798b-132">`GetPercentile`bir yüzde birlik hesaplar yardımcı bir işlev öğrencinin ortalama puanı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="5798b-132">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="5798b-133">Yöntemi, 0 ile 10 arasında bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5798b-133">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="5798b-134">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5798b-134">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="5798b-135">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="5798b-135">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="5798b-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="5798b-136">Example</span></span>  
 <span data-ttu-id="5798b-137">Aşağıdaki örnek, bir Boolean karşılaştırma deyimi kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5798b-137">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="5798b-138">Bu örnekte, öğrencinin ortalama incelemesi puan 75 büyük olup Boole ifadesi sınar.</span><span class="sxs-lookup"><span data-stu-id="5798b-138">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="5798b-139">Önceki örneklerde olduğu gibi tam kaynak öğesi gerekli değildir çünkü sonuçları anonim bir tür öngörülen.</span><span class="sxs-lookup"><span data-stu-id="5798b-139">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="5798b-140">Anonim tür özelliklerinde üzerinde özellikleri hale Not `Key` üye ve sorgu çalıştırıldığında adıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5798b-140">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="5798b-141">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5798b-141">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="5798b-142">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="5798b-142">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="5798b-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="5798b-143">Example</span></span>  
 <span data-ttu-id="5798b-144">Aşağıdaki örnek anonim bir tür birden çok değer içeren bir anahtar kapsüllemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5798b-144">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="5798b-145">Bu örnekte, ilk anahtar öğrencinin son adının ilk harfi değerdir.</span><span class="sxs-lookup"><span data-stu-id="5798b-145">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="5798b-146">İkinci anahtar Öğrenci 85 üzerinde ilk incelemesi üzerinde skoru olup olmadığını belirten bir Boole değeri değerdir.</span><span class="sxs-lookup"><span data-stu-id="5798b-146">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="5798b-147">Anahtar herhangi bir özellik tarafından grupları sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5798b-147">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="5798b-148">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5798b-148">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="5798b-149">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="5798b-149">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5798b-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5798b-150">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="5798b-151">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5798b-151">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="5798b-152">Group tümcesi</span><span class="sxs-lookup"><span data-stu-id="5798b-152">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="5798b-153">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="5798b-153">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="5798b-154">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="5798b-154">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="5798b-155">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="5798b-155">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="5798b-156">Verileri gruplandırma</span><span class="sxs-lookup"><span data-stu-id="5798b-156">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
