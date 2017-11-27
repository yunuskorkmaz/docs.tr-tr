---
title: "Null karşılaştırmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fefbd3894063c0298a7ad5110ed6867408869107
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="null-comparisons"></a><span data-ttu-id="ee793-102">Null karşılaştırmaları</span><span class="sxs-lookup"><span data-stu-id="ee793-102">Null Comparisons</span></span>
<span data-ttu-id="ee793-103">A `null` veri kaynağındaki değer, değer bilinmeyen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee793-103">A `null` value in the data source indicates that the value is unknown.</span></span> <span data-ttu-id="ee793-104">İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular, kontrol edebilirsiniz null değerleri bu nedenle, bazı hesaplamalar veya karşılaştırmaları yalnızca geçerli veya boş olan satırlar üzerinde gerçekleştirilen veri.</span><span class="sxs-lookup"><span data-stu-id="ee793-104">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries, you can check for null values so that certain calculations or comparisons are only performed on rows that have valid, or non-null, data.</span></span> <span data-ttu-id="ee793-105">CLR null semantiği, ancak veri kaynağı null semantiği farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee793-105">CLR null semantics, however, may differ from the null semantics of the data source.</span></span> <span data-ttu-id="ee793-106">Çoğu veritabanları, null karşılaştırma işlemek için üç değerli mantığı sürümünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee793-106">Most databases use a version of three-valued logic to handle null comparisons.</span></span> <span data-ttu-id="ee793-107">Diğer bir deyişle, bir null değer karşılaştırmak için değerlendirmez `true` veya `false`, için değerlendirir `unknown`.</span><span class="sxs-lookup"><span data-stu-id="ee793-107">That is, a comparison against a null value does not evaluate to `true` or `false`, it evaluates to `unknown`.</span></span> <span data-ttu-id="ee793-108">Genellikle bu ANSI null değerlere uygulamasıdır, ancak bu her zaman geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="ee793-108">Often this is an implementation of ANSI nulls, but this is not always the case.</span></span>  
  
 <span data-ttu-id="ee793-109">SQL Server'da varsayılan olarak, null eşittir null karşılaştırma null değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee793-109">By default in SQL Server, the null-equals-null comparison returns a null value.</span></span> <span data-ttu-id="ee793-110">Aşağıdaki örnekte, satırları nerede `ShipDate` null sonuç kümesinden hariç tutulur ve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] deyimi 0 satır döndürebildiği.</span><span class="sxs-lookup"><span data-stu-id="ee793-110">In the following example, the rows where `ShipDate` is null are excluded from the result set, and the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] statement would return 0 rows.</span></span>  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 <span data-ttu-id="ee793-111">Null eşittir null karşılaştırma doğru döndüğü bu CLR null semantiğini çok farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="ee793-111">This is very different from the CLR null semantics, where the null-equals-null comparison returns true.</span></span>  
  
 <span data-ttu-id="ee793-112">Aşağıdaki LINQ sorgusu CLR ifade edilir, ancak veri kaynağında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ee793-112">The following LINQ query is expressed in the CLR, but it is executed in the data source.</span></span> <span data-ttu-id="ee793-113">CLR semantiği veri kaynağında uyulacaktır garanti olduğundan, beklenen bir davranış belirsiz.</span><span class="sxs-lookup"><span data-stu-id="ee793-113">Because there is no guarantee that CLR semantics will be honored at the data source, the expected behavior is indeterminate.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a><span data-ttu-id="ee793-114">Anahtar Seçici</span><span class="sxs-lookup"><span data-stu-id="ee793-114">Key Selectors</span></span>  
 <span data-ttu-id="ee793-115">A *anahtar Seçici* standart sorgu işleçleri bir anahtarı bir öğeden çıkarmak için kullanılan bir işlev.</span><span class="sxs-lookup"><span data-stu-id="ee793-115">A *key selector* is a function used in the standard query operators to extract a key from an element.</span></span> <span data-ttu-id="ee793-116">Anahtar Seçici işlevinde bir ifadenin bir sabit ile karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee793-116">In the key selector function, an expression can be compared with a constant.</span></span> <span data-ttu-id="ee793-117">CLR boş semantiği bir ifade null bir sabite karşılaştırılır veya iki null sabit karşılaştırılır sergilenen.</span><span class="sxs-lookup"><span data-stu-id="ee793-117">CLR null semantics are exhibited if an expression is compared to a null constant or if two null constants are compared.</span></span> <span data-ttu-id="ee793-118">İki sütun veri kaynağındaki null değerler ile karşılaştırıldığında, mağaza null semantiği sergilenen.</span><span class="sxs-lookup"><span data-stu-id="ee793-118">Store null semantics are exhibited if two columns with null values in the data source are compared.</span></span> <span data-ttu-id="ee793-119">Anahtar Seçici gruplandırma ve standart sorgu işleçleri gibi sıralama çoğunda bulunan <xref:System.Linq.Queryable.GroupBy%2A>ve anahtarları olarak siparişe seçin veya sorgu sonuçları gruplandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee793-119">Key selectors are found in many of the grouping and ordering standard query operators, such as <xref:System.Linq.Queryable.GroupBy%2A>, and are used to select keys by which to order or group the query results.</span></span>  
  
## <a name="null-property-on-a-null-object"></a><span data-ttu-id="ee793-120">Null özellik Null bir nesne üzerinde</span><span class="sxs-lookup"><span data-stu-id="ee793-120">Null Property on a Null Object</span></span>  
 <span data-ttu-id="ee793-121">İçinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], null bir nesne özelliklerini null.</span><span class="sxs-lookup"><span data-stu-id="ee793-121">In the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], the properties of a null object are null.</span></span> <span data-ttu-id="ee793-122">CLR içinde null bir nesnenin bir özelliğini başvuru girişiminde bulunduğunuzda alacak bir <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="ee793-122">When you attempt to reference a property of a null object in the CLR, you will receive a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="ee793-123">LINQ Sorgu null bir nesnenin bir özelliğini içerir, bu tutarsız davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee793-123">When a LINQ query involves a property of a null object, this can result in inconsistent behavior.</span></span>  
  
 <span data-ttu-id="ee793-124">Örneğin, sorguda aşağıdaki dönüştürme `NewProduct` sonuçlanabilir komut ağacı katmanda yapılır `Introduced` özelliği null olması.</span><span class="sxs-lookup"><span data-stu-id="ee793-124">For example, in the following query, the cast to `NewProduct` is done in the command tree layer, which might result in the `Introduced` property being null.</span></span> <span data-ttu-id="ee793-125">Veritabanı boş karşılaştırmalar tanımladıysanız şekilde <xref:System.DateTime> karşılaştırma doğru olarak değerlendirir, satır dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="ee793-125">If the database defined null comparisons such that the <xref:System.DateTime> comparison evaluates to true, the row will be included.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a><span data-ttu-id="ee793-126">Toplama işlevlerinin Null koleksiyonlarını geçirme</span><span class="sxs-lookup"><span data-stu-id="ee793-126">Passing Null Collections to Aggregate Functions</span></span>  
 <span data-ttu-id="ee793-127">İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], destekleyen bir koleksiyonu geçirdiğinizde `IQueryable` bir toplama işlevi için veritabanına toplama işlemleri gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ee793-127">In [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], when you pass a collection that supports `IQueryable` to an aggregate function, aggregate operations are performed at the database.</span></span> <span data-ttu-id="ee793-128">Bellek içinde gerçekleştirilen bir sorgu ve veritabanına gerçekleştirilen sorgu sonuçları farklılıklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee793-128">There might be differences in the results of a query that was performed in-memory and a query that was performed at the database.</span></span> <span data-ttu-id="ee793-129">Herhangi bir eşleşme varsa bir bellek içi sorgusu ile sorgu sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee793-129">With an in-memory query, if there are no matches, the query returns zero.</span></span> <span data-ttu-id="ee793-130">Adlı veritabanı, aynı sorgu döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="ee793-130">At the database, the same query returns `null`.</span></span> <span data-ttu-id="ee793-131">Varsa bir `null` LINQ Toplama işlevi için geçirilen değer, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="ee793-131">If a `null` value is passed to a LINQ aggregate function, an exception will be thrown.</span></span> <span data-ttu-id="ee793-132">Olası kabul etmek için `null` değerleri, cast türleri ve türlerin boş değer atanabilir türler için sorgu sonuçlarını almak özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ee793-132">To accept possible `null` values, cast the types and the properties of the types that receive query results to nullable types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee793-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee793-133">See Also</span></span>  
 [<span data-ttu-id="ee793-134">LINQ to Entities sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ee793-134">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
