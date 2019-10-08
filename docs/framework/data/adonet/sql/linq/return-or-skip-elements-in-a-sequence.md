---
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 7c98681493738b4e94ed14417fa1437efb6c12ac
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003314"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="af294-102">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="af294-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="af294-103">Bir dizide verilen sayıda öğe döndürmek için <xref:System.Linq.Queryable.Take%2A> işlecini kullanın ve ardından kalanı atlayın.</span><span class="sxs-lookup"><span data-stu-id="af294-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="af294-104">Bir dizide verilen sayıda öğeyi atlamak için <xref:System.Linq.Queryable.Skip%2A> işlecini kullanın ve ardından kalanı geri döndürün.</span><span class="sxs-lookup"><span data-stu-id="af294-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af294-105"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları zaman belirli sınırlamalara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="af294-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="af294-106">Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.</span><span class="sxs-lookup"><span data-stu-id="af294-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="af294-107">, SQL `NOT EXISTS` yan tümcesiyle bir alt sorgu kullanarak <xref:System.Linq.Queryable.Skip%2A> çevirir.</span><span class="sxs-lookup"><span data-stu-id="af294-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="af294-108">Bu çeviri aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="af294-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="af294-109">Bağımsız değişken bir küme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af294-109">The argument must be a set.</span></span> <span data-ttu-id="af294-110">Sıralı olsa bile çoklu kümeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="af294-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="af294-111">Oluşturulan sorgu <xref:System.Linq.Queryable.Skip%2A> ' ın uygulandığı temel sorgu için oluşturulan sorgudan çok daha karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="af294-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="af294-112">Bu karmaşıklık, performans düşüşüyle ve hatta zaman aşımına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="af294-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af294-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="af294-113">Example</span></span>  
 <span data-ttu-id="af294-114">Aşağıdaki örnek ilk beş `Employees` ' i seçmek için `Take` kullanır.</span><span class="sxs-lookup"><span data-stu-id="af294-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="af294-115">Koleksiyonun öncelikle `HireDate` ile sıralanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="af294-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="af294-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="af294-116">Example</span></span>  
 <span data-ttu-id="af294-117">Aşağıdaki örnek, en pahalı 10 `Products` dışında tümünü seçmek için <xref:System.Linq.Queryable.Skip%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="af294-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="af294-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="af294-118">Example</span></span>  
 <span data-ttu-id="af294-119">Aşağıdaki örnek, ilk 50 kayıtları atlamak için <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> yöntemlerini birleştirir ve ardından sonraki 10 ' u döndürür.</span><span class="sxs-lookup"><span data-stu-id="af294-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="af294-120"><xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemleri yalnızca sıralı kümelere karşı iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="af294-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="af294-121">Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="af294-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="af294-122">SQL 'de sıralama sınırlamaları nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin bağımsız değişkeninin sıralamasını işlecin sonucuna taşımaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="af294-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af294-123">Çeviri SQL Server 2000 ve SQL Server 2005 için farklıdır.</span><span class="sxs-lookup"><span data-stu-id="af294-123">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="af294-124">@No__t-0 ' ı herhangi bir karmaşıklık sorgusu ile kullanmayı planlıyorsanız, SQL Server 2005 ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="af294-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="af294-125">SQL Server 2000 için aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgusunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="af294-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="af294-126">, sıralamayı SQL kodundaki sonuna aşağıdaki gibi taşıdır:</span><span class="sxs-lookup"><span data-stu-id="af294-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
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
  
 <span data-ttu-id="af294-127">@No__t-0 ve <xref:System.Linq.Queryable.Skip%2A> birlikte zincirlendiği zaman, belirtilen tüm sıralama tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af294-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="af294-128">Aksi takdirde, sonuçlar tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="af294-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="af294-129">SQL belirtimine dayalı negatif olmayan, sabit tamsayı bağımsız değişkenleri için hem <xref:System.Linq.Queryable.Take%2A> hem de <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="af294-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af294-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af294-130">See also</span></span>

- [<span data-ttu-id="af294-131">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="af294-131">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="af294-132">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="af294-132">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
