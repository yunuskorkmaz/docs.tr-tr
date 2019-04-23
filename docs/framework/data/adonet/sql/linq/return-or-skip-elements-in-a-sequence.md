---
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 885e6bc011041320a3dc7b17d84b2541bf030adf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168317"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="05714-102">Dizideki Öğeleri Döndürme veya Atlama</span><span class="sxs-lookup"><span data-stu-id="05714-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="05714-103">Kullanım <xref:System.Linq.Queryable.Take%2A> işleci bir dizideki öğeler, verilen sayıda dönün ve sonra kalanını atlayın.</span><span class="sxs-lookup"><span data-stu-id="05714-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="05714-104">Kullanım <xref:System.Linq.Queryable.Skip%2A> işleci bir dizideki öğelerin verilen bir sayının atlamayı ve sonra kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="05714-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05714-105"><xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 sorguları içinde kullanıldığında belirli sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="05714-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="05714-106">"Atla ve SQL Server 2000'de özel durumlar'ı Al" girdisinde daha fazla bilgi için bkz. [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="05714-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="05714-107">çevirir <xref:System.Linq.Queryable.Skip%2A> SQL ile bir alt sorgu kullanarak `NOT EXISTS` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="05714-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="05714-108">Bu çeviri aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="05714-108">This translation has the following limitations:</span></span>  
  
-   <span data-ttu-id="05714-109">Bağımsız değişken bir küme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05714-109">The argument must be a set.</span></span> <span data-ttu-id="05714-110">Multisets, sipariş bile desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="05714-110">Multisets are not supported, even if ordered.</span></span>  
  
-   <span data-ttu-id="05714-111">Oluşturulan sorgu, üzerinde temel sorgu için oluşturulan sorgu çok daha karmaşık <xref:System.Linq.Queryable.Skip%2A> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="05714-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="05714-112">Bu karmaşıklığı, performans veya hatta bir zaman aşımı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="05714-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05714-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="05714-113">Example</span></span>  
 <span data-ttu-id="05714-114">Aşağıdaki örnekte `Take` ilk beş seçilecek `Employees` işe.</span><span class="sxs-lookup"><span data-stu-id="05714-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="05714-115">Koleksiyonun varsayılan olarak sıralanır Not `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="05714-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="05714-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="05714-116">Example</span></span>  
 <span data-ttu-id="05714-117">Aşağıdaki örnekte <xref:System.Linq.Queryable.Skip%2A> en pahalı 10 tüm seçilecek `Products`.</span><span class="sxs-lookup"><span data-stu-id="05714-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="05714-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="05714-118">Example</span></span>  
 <span data-ttu-id="05714-119">Aşağıdaki örnek birleştirir <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> ilk 50 kaydı atlayabilir ve ardından sonraki 10 döndürmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="05714-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="05714-120"><xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemlerdir sıralı kümelerine göre yalnızca iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="05714-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="05714-121">Sırasız kümeleri veya multisets semantiği tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="05714-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="05714-122">SQL'de sıralama sınırlamaları nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağımsız değişkeni sıralama taşımaya <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin sonucunu işleci.</span><span class="sxs-lookup"><span data-stu-id="05714-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05714-123">Çeviri için farklı [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ve [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05714-123">Translation is different for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] and [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span> <span data-ttu-id="05714-124">Kullanmayı planlıyorsanız <xref:System.Linq.Queryable.Skip%2A> ile bir sorgu tüm karmaşıklığı [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05714-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span>  
  
 <span data-ttu-id="05714-125">Aşağıdakileri göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="05714-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="05714-126">SQL kodunda sonuna aşağıdaki şekilde sıralama taşır:</span><span class="sxs-lookup"><span data-stu-id="05714-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```  
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
  
 <span data-ttu-id="05714-127">Zaman <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> olan birbirine zincirlenmiş, tüm belirtilen sıralama tutarlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05714-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="05714-128">Aksi takdirde, sonuçlar tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="05714-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="05714-129">Negatif olmayan için sabit tamsayı bağımsız değişkenleri temel SQL belirtimine her ikisi de <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmış olması.</span><span class="sxs-lookup"><span data-stu-id="05714-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05714-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05714-130">See also</span></span>

- [<span data-ttu-id="05714-131">Sorgu Örnekleri</span><span class="sxs-lookup"><span data-stu-id="05714-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="05714-132">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="05714-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
