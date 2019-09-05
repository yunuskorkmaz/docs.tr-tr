---
title: SıNıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 432dfe2c8b2b87daf885be6de4da9bbeaaa37638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250441"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="e9ff8-102">SıNıR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e9ff8-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="e9ff8-103">Fiziksel sayfalama, ORDER BY yan tümcesinde LIMIT alt yan tümcesi kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="e9ff8-104">SıNıR, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9ff8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9ff8-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e9ff8-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e9ff8-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="e9ff8-107">Seçilecek öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="e9ff8-108">Bir sınır ifadesi alt yan tümcesi ORDER BY yan tümcesinde mevcutsa, sorgu sıralama belirtimine göre sıralanır ve sonuç olarak satır sayısı sınır ifadesi ile kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="e9ff8-109">Örneğin, sınır 5, sonuç kümesini 5 örnek veya satır olarak kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="e9ff8-110">SıNıR, ORDER BY yan tümcesinin mevcut olmasını gerektiren sınır ile en üst ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="e9ff8-111">SKIP ve LIMIT, ORDER BY yan tümcesiyle birlikte bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9ff8-112">En üstteki değiştirici ve SKIP alt yan tümcesi aynı sorgu ifadesinde varsa, bir varlık SQL sorgusu geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="e9ff8-113">ÜST ifade, sınır ifadesine göre değiştirilerek sorgunun yeniden yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9ff8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9ff8-114">Example</span></span>  
 <span data-ttu-id="e9ff8-115">Aşağıdaki Entity SQL sorgusu, SELECT ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için LIMIT ile ORDER BY işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="e9ff8-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e9ff8-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e9ff8-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e9ff8-118">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e9ff8-119">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="e9ff8-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="e9ff8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9ff8-120">See also</span></span>

- [<span data-ttu-id="e9ff8-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="e9ff8-121">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="e9ff8-122">[Nasıl yapılır: Sorgu sonuçları aracılığıyla sayfa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e9ff8-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="e9ff8-123">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="e9ff8-123">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="e9ff8-124">TOP</span><span class="sxs-lookup"><span data-stu-id="e9ff8-124">TOP</span></span>](top-entity-sql.md)
