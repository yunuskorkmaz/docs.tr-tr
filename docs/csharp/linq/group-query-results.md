---
title: Grup sorgu sonuçları
description: Sonuçları gruplandırmak nasıl.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: cb7808bfdd86dd23882d0722b87b1e013a84141e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289041"
---
# <a name="group-query-results"></a><span data-ttu-id="497db-103">Grup sorgu sonuçları</span><span class="sxs-lookup"><span data-stu-id="497db-103">Group query results</span></span>

<span data-ttu-id="497db-104">Gruplandırma LINQ en güçlü özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="497db-104">Grouping is one of the most powerful capabilities of LINQ.</span></span> <span data-ttu-id="497db-105">Aşağıdaki örnekler, çeşitli şekillerde verilerin nasıl gruplanacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="497db-105">The following examples show how to group data in various ways:</span></span>  
  
-   <span data-ttu-id="497db-106">Tek bir özelliğe göre.</span><span class="sxs-lookup"><span data-stu-id="497db-106">By a single property.</span></span>  
  
-   <span data-ttu-id="497db-107">Bir dize özelliği ilk harfi ile.</span><span class="sxs-lookup"><span data-stu-id="497db-107">By the first letter of a string property.</span></span>  
  
-   <span data-ttu-id="497db-108">Hesaplanan sayısal bir aralık tarafından.</span><span class="sxs-lookup"><span data-stu-id="497db-108">By a computed numeric range.</span></span>  
  
-   <span data-ttu-id="497db-109">Boole koşulu veya diğer ifade.</span><span class="sxs-lookup"><span data-stu-id="497db-109">By Boolean predicate or other expression.</span></span>  
  
-   <span data-ttu-id="497db-110">Bileşik bir anahtar.</span><span class="sxs-lookup"><span data-stu-id="497db-110">By a compound key.</span></span>  
  
 <span data-ttu-id="497db-111">Ayrıca, son iki sorgu sonuçları Öğrenci ilk yalnızca içeren ve Soyadı yeni bir anonim tür yansıtın.</span><span class="sxs-lookup"><span data-stu-id="497db-111">In addition, the last two queries project their results into a new anonymous type that contains only the student's first and last name.</span></span> <span data-ttu-id="497db-112">Daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="497db-112">For more information, see the [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="497db-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="497db-113">Example</span></span>  
 <span data-ttu-id="497db-114">Bu konudaki tüm örnekleri aşağıdaki yardımcı sınıfları ve veri kaynaklarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="497db-114">All the examples in this topic use the following helper classes and data sources.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="497db-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="497db-115">Example</span></span>  
 <span data-ttu-id="497db-116">Aşağıdaki örnek Grup anahtarı olarak öğesinin tek bir özelliğini kullanarak kaynağı öğeleri gruplandırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="497db-116">The following example shows how to group source elements by using a single property of the element as the group key.</span></span> <span data-ttu-id="497db-117">Bu durumda anahtarıdır bir `string`, öğrencinin son adı.</span><span class="sxs-lookup"><span data-stu-id="497db-117">In this case the key is a `string`, the student's last name.</span></span> <span data-ttu-id="497db-118">Anahtar için bir alt dizesi kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="497db-118">It is also possible to use a substring for the key.</span></span> <span data-ttu-id="497db-119">Gruplama işleminin türü için varsayılan eşitlik karşılaştırıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="497db-119">The grouping operation uses the default equality comparer for the type.</span></span>  
  
 <span data-ttu-id="497db-120">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="497db-120">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="497db-121">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupBySingleProperty()`.</span><span class="sxs-lookup"><span data-stu-id="497db-121">Change the calling statement in the `Main` method to `sc.GroupBySingleProperty()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="497db-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="497db-122">Example</span></span>  
 <span data-ttu-id="497db-123">Aşağıdaki örnek, nesnenin bir özelliğini dışında bir şey için Grup anahtarı kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="497db-123">The following example shows how to group source elements by using something other than a property of the object for the group key.</span></span> <span data-ttu-id="497db-124">Bu örnekte, öğrencinin son adının ilk harfi anahtardır.</span><span class="sxs-lookup"><span data-stu-id="497db-124">In this example, the key is the first letter of the student's last name.</span></span>  
  
 <span data-ttu-id="497db-125">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="497db-125">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="497db-126">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupBySubstring()`.</span><span class="sxs-lookup"><span data-stu-id="497db-126">Change the calling statement in the `Main` method to `sc.GroupBySubstring()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="497db-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="497db-127">Example</span></span>  
 <span data-ttu-id="497db-128">Aşağıdaki örnek, sayısal bir aralık bir Grup anahtarı kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="497db-128">The following example shows how to group source elements by using a numeric range as a group key.</span></span> <span data-ttu-id="497db-129">Sorgu sonuçları yalnızca ilk ve son adı ve Öğrenci ait olduğu yüzdebirlik aralığı içeren bir anonim tür sonra projeleri.</span><span class="sxs-lookup"><span data-stu-id="497db-129">The query then projects the results into an anonymous type that contains only the first and last name and the percentile range to which the student belongs.</span></span> <span data-ttu-id="497db-130">Anonim bir tür tam kullanmak için gerekli olmadığı için kullanılan `Student` sonuçları görüntülemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="497db-130">An anonymous type is used because it is not necessary to use the complete `Student` object to display the results.</span></span> <span data-ttu-id="497db-131">`GetPercentile` bir yüzde birlik hesaplar yardımcı bir işlev öğrencinin ortalama puanı üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="497db-131">`GetPercentile` is a helper function that calculates a percentile based on the student's average score.</span></span> <span data-ttu-id="497db-132">Yöntemi, 0 ile 10 arasında bir tamsayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="497db-132">The method returns an integer between 0 and 10.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 <span data-ttu-id="497db-133">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="497db-133">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="497db-134">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByRange()`.</span><span class="sxs-lookup"><span data-stu-id="497db-134">Change the calling statement in the `Main` method to `sc.GroupByRange()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="497db-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="497db-135">Example</span></span>  
 <span data-ttu-id="497db-136">Aşağıdaki örnek, bir Boolean karşılaştırma deyimi kullanarak kaynağı öğeleri gruplandırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="497db-136">The following example shows how to group source elements by using a Boolean comparison expression.</span></span> <span data-ttu-id="497db-137">Bu örnekte, öğrencinin ortalama incelemesi puan 75 büyük olup Boole ifadesi sınar.</span><span class="sxs-lookup"><span data-stu-id="497db-137">In this example, the Boolean expression tests whether a student's average exam score is greater than 75.</span></span> <span data-ttu-id="497db-138">Önceki örneklerde olduğu gibi tam kaynak öğesi gerekli değildir çünkü sonuçları anonim bir tür öngörülen.</span><span class="sxs-lookup"><span data-stu-id="497db-138">As in previous examples, the results are projected into an anonymous type because the complete source element is not needed.</span></span> <span data-ttu-id="497db-139">Anonim tür özelliklerinde üzerinde özellikleri hale Not `Key` üye ve sorgu çalıştırıldığında adıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="497db-139">Note that the properties in the anonymous type become properties on the `Key` member and can be accessed by name when the query is executed.</span></span>  
  
 <span data-ttu-id="497db-140">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="497db-140">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="497db-141">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByBoolean()`.</span><span class="sxs-lookup"><span data-stu-id="497db-141">Change the calling statement in the `Main` method to `sc.GroupByBoolean()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="497db-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="497db-142">Example</span></span>  
 <span data-ttu-id="497db-143">Aşağıdaki örnek anonim bir tür birden çok değer içeren bir anahtar kapsüllemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="497db-143">The following example shows how to use an anonymous type to encapsulate a key that contains multiple values.</span></span> <span data-ttu-id="497db-144">Bu örnekte, ilk anahtar öğrencinin son adının ilk harfi değerdir.</span><span class="sxs-lookup"><span data-stu-id="497db-144">In this example, the first key value is the first letter of the student's last name.</span></span> <span data-ttu-id="497db-145">İkinci anahtar Öğrenci 85 üzerinde ilk incelemesi üzerinde skoru olup olmadığını belirten bir Boole değeri değerdir.</span><span class="sxs-lookup"><span data-stu-id="497db-145">The second key value is a Boolean that specifies whether the student scored over 85 on the first exam.</span></span> <span data-ttu-id="497db-146">Anahtar herhangi bir özellik tarafından grupları sıralayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="497db-146">You can order the groups by any property in the key.</span></span>  
  
 <span data-ttu-id="497db-147">Aşağıdaki yöntem içine yapıştırma `StudentClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="497db-147">Paste the following method into the `StudentClass` class.</span></span> <span data-ttu-id="497db-148">Arama deyiminde değiştirme `Main` yöntemine `sc.GroupByCompositeKey()`.</span><span class="sxs-lookup"><span data-stu-id="497db-148">Change the calling statement in the `Main` method to `sc.GroupByCompositeKey()`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="497db-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="497db-149">See also</span></span>  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [<span data-ttu-id="497db-150">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="497db-150">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="497db-151">group yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="497db-151">group clause</span></span>](../language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="497db-152">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="497db-152">Anonymous Types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="497db-153">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="497db-153">Perform a Subquery on a Grouping Operation</span></span>](perform-a-subquery-on-a-grouping-operation.md)  
 [<span data-ttu-id="497db-154">İç içe geçmiş grup oluşturma</span><span class="sxs-lookup"><span data-stu-id="497db-154">Create a Nested Group</span></span>](create-a-nested-group.md)  
 [<span data-ttu-id="497db-155">Verileri Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="497db-155">Grouping Data</span></span>](../programming-guide/concepts/linq/grouping-data.md)
