---
title: "Dönüş veya bir dizi Atla öğeleri"
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
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f8fed70e5eafb096ae2e7b2da882e1e4f6c8ed63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="0f336-102">Dönüş veya bir dizi Atla öğeleri</span><span class="sxs-lookup"><span data-stu-id="0f336-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="0f336-103">Kullanım <xref:System.Linq.Queryable.Take%2A> işleci bir dizisinde öğeleri, verilen sayıda dönün ve kalanını atlayın.</span><span class="sxs-lookup"><span data-stu-id="0f336-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="0f336-104">Kullanım <xref:System.Linq.Queryable.Skip%2A> dizisindeki öğelerin verilen bir sayının atlamayı ve geri kalan dönmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="0f336-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f336-105"><xref:System.Linq.Enumerable.Take%2A>ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 karşı sorgularda kullanıldığında belirli sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="0f336-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="0f336-106">Daha fazla bilgi için "Atlayın ve SQL Server 2000'de özel durumlar alın" girdisinde bkz [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="0f336-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0f336-107">çevirir <xref:System.Linq.Queryable.Skip%2A> SQL ile bir alt sorgu kullanarak `NOT EXISTS` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="0f336-107"> translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="0f336-108">Bu çeviri aşağıdaki sınırlamalara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0f336-108">This translation has the following limitations:</span></span>  
  
-   <span data-ttu-id="0f336-109">Bağımsız değişkeni bir küme olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f336-109">The argument must be a set.</span></span> <span data-ttu-id="0f336-110">Multisets, sipariş olsa bile desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0f336-110">Multisets are not supported, even if ordered.</span></span>  
  
-   <span data-ttu-id="0f336-111">Oluşturulan sorgu üretileceği temel sorgu için oluşturulan sorgu çok daha karmaşık olabilir <xref:System.Linq.Queryable.Skip%2A> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0f336-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="0f336-112">Bu karmaşıklık performans düşüklüğü veya hatta bir zaman aşımı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f336-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f336-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f336-113">Example</span></span>  
 <span data-ttu-id="0f336-114">Aşağıdaki örnek kullanır `Take` ilk beş seçmek için `Employees` işe.</span><span class="sxs-lookup"><span data-stu-id="0f336-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="0f336-115">Koleksiyon önce tarafından sıralanan Not `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="0f336-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="0f336-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f336-116">Example</span></span>  
 <span data-ttu-id="0f336-117">Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Skip%2A> en pahalı 10 dışında tüm seçmek için `Products`.</span><span class="sxs-lookup"><span data-stu-id="0f336-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="0f336-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f336-118">Example</span></span>  
 <span data-ttu-id="0f336-119">Aşağıdaki örnek birleştirir <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> ilk 50 kaydı atlayın ve sonraki 10 dönmek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="0f336-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="0f336-120"><xref:System.Linq.Queryable.Take%2A>ve <xref:System.Linq.Queryable.Skip%2A> işlemleri yalnızca sıralı kümelerine göre iyi tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="0f336-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="0f336-121">Sırasız kümeleri veya multisets anlamları tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="0f336-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="0f336-122">SQL'de sıralama sınırlamalar nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağımsız değişkeni sıralama taşımayı dener <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin sonucu işleci.</span><span class="sxs-lookup"><span data-stu-id="0f336-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f336-123">Çeviri için farklı [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ve [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f336-123">Translation is different for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] and [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span> <span data-ttu-id="0f336-124">Kullanmayı planlıyorsanız, <xref:System.Linq.Queryable.Skip%2A> herhangi karmaşıklık query ile birlikte kullanma [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f336-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span>  
  
 <span data-ttu-id="0f336-125">Aşağıdakileri göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için sorgu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="0f336-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0f336-126">SQL kodda sonuna şu şekilde sıralama taşır:</span><span class="sxs-lookup"><span data-stu-id="0f336-126"> moves the ordering to the end in the SQL code, as follows:</span></span>  
  
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
  
 <span data-ttu-id="0f336-127">Zaman <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> olan birbirine zincirlenmiş, tüm belirtilen sıralama tutarlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f336-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="0f336-128">Aksi takdirde, sonuçları tanımlanmamış.</span><span class="sxs-lookup"><span data-stu-id="0f336-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="0f336-129">Negatif olmayan için tam sayı sabit bağımsız değişkenler tabanlı SQL belirtimi her ikisi de <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmış olması.</span><span class="sxs-lookup"><span data-stu-id="0f336-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f336-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f336-130">See Also</span></span>  
 [<span data-ttu-id="0f336-131">Sorgu örnekleri</span><span class="sxs-lookup"><span data-stu-id="0f336-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="0f336-132">Standart sorgu işleci çevirisi</span><span class="sxs-lookup"><span data-stu-id="0f336-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
