---
description: 'Daha fazla bilgi edinin: bir dizideki öğeleri döndürün veya atlayın'
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 6eba93562d4c6a8ffa4150453deed88844d4e297
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695144"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="e389c-103">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="e389c-103">Return Or Skip Elements in a Sequence</span></span>

<span data-ttu-id="e389c-104">İşleci kullanarak <xref:System.Linq.Queryable.Take%2A> bir dizide verilen sayıda öğeyi döndürün ve sonra kalanı atlayın.</span><span class="sxs-lookup"><span data-stu-id="e389c-104">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="e389c-105"><xref:System.Linq.Queryable.Skip%2A>Bir dizide verilen sayıda öğeyi atlamak için işlecini kullanın ve ardından kalanı geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="e389c-105">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e389c-106"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="e389c-106"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="e389c-107">Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.</span><span class="sxs-lookup"><span data-stu-id="e389c-107">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e389c-108"><xref:System.Linq.Queryable.Skip%2A>SQL yan tümcesiyle bir alt sorgu kullanarak çevirir `NOT EXISTS` .</span><span class="sxs-lookup"><span data-stu-id="e389c-108">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="e389c-109">Bu çeviri aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e389c-109">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="e389c-110">Bağımsız değişken bir küme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e389c-110">The argument must be a set.</span></span> <span data-ttu-id="e389c-111">Sıralı olsa bile çoklu kümeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e389c-111">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="e389c-112">Oluşturulan sorgu, üzerinde uygulanan temel sorgu için oluşturulan sorgudan çok daha karmaşık olabilir <xref:System.Linq.Queryable.Skip%2A> .</span><span class="sxs-lookup"><span data-stu-id="e389c-112">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="e389c-113">Bu karmaşıklık, performans düşüşüyle ve hatta zaman aşımına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e389c-113">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e389c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e389c-114">Example</span></span>  

 <span data-ttu-id="e389c-115">Aşağıdaki örnek, `Take` işe alınan ilk beş ' u seçmek için kullanır `Employees` .</span><span class="sxs-lookup"><span data-stu-id="e389c-115">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="e389c-116">Koleksiyonun öncelikle tarafından sıralandığı unutulmamalıdır `HireDate` .</span><span class="sxs-lookup"><span data-stu-id="e389c-116">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="e389c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="e389c-117">Example</span></span>  

 <span data-ttu-id="e389c-118">Aşağıdaki örnek, <xref:System.Linq.Queryable.Skip%2A> en pahalı 10 dışında tümünü seçmek için kullanır `Products` .</span><span class="sxs-lookup"><span data-stu-id="e389c-118">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="e389c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e389c-119">Example</span></span>  

 <span data-ttu-id="e389c-120">Aşağıdaki örnek, <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> yöntemlerini ilk 50 kaydı atlamak için birleştirir ve sonra sonraki 10 ' u döndürür.</span><span class="sxs-lookup"><span data-stu-id="e389c-120">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="e389c-121"><xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemler yalnızca sıralı kümelere karşı iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e389c-121"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="e389c-122">Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="e389c-122">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="e389c-123">SQL 'de sıralama sınırlamaları nedeniyle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veya işlecinin bağımsız değişkeninin sıralamasını <xref:System.Linq.Queryable.Take%2A> <xref:System.Linq.Queryable.Skip%2A> işlecin sonucuna taşımaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="e389c-123">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e389c-124">Çeviri SQL Server 2000 ve SQL Server 2005 için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e389c-124">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="e389c-125"><xref:System.Linq.Queryable.Skip%2A>Herhangi bir karmaşıklık sorgusu ile kullanmayı planlıyorsanız SQL Server 2005 kullanın.</span><span class="sxs-lookup"><span data-stu-id="e389c-125">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="e389c-126">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server 2000 için aşağıdaki sorguyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e389c-126">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e389c-127">sıralamayı SQL kodundaki sonuna aşağıdaki gibi gider:</span><span class="sxs-lookup"><span data-stu-id="e389c-127">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="e389c-128"><xref:System.Linq.Queryable.Take%2A>Ve <xref:System.Linq.Queryable.Skip%2A> birlikte zincirlendiği zaman, belirtilen tüm sıralama tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e389c-128">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="e389c-129">Aksi takdirde, sonuçlar tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="e389c-129">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="e389c-130">SQL belirtimine dayalı negatif olmayan, sabit integral bağımsız değişkenleri için her ikisi de <xref:System.Linq.Queryable.Take%2A> <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e389c-130">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e389c-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e389c-131">See also</span></span>

- [<span data-ttu-id="e389c-132">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="e389c-132">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="e389c-133">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="e389c-133">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
