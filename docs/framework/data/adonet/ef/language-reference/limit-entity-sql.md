---
description: 'Daha fazla bilgi edinin: LIMIT (Entity SQL)'
title: SıNıR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 873f3fd5ed83d04313aff92bf1f97e07001c3f08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748212"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="5ac8f-103">SıNıR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5ac8f-103">LIMIT (Entity SQL)</span></span>

<span data-ttu-id="5ac8f-104">Fiziksel sayfalama, ORDER BY yan tümcesinde LIMIT alt yan tümcesi kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-104">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="5ac8f-105">SıNıR, ORDER BY yan tümcesinde ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-105">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac8f-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5ac8f-106">Syntax</span></span>  
  
```sql  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ac8f-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="5ac8f-107">Arguments</span></span>  

 `n`  
 <span data-ttu-id="5ac8f-108">Seçilecek öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-108">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="5ac8f-109">Bir sınır ifadesi alt yan tümcesi ORDER BY yan tümcesinde mevcutsa, sorgu sıralama belirtimine göre sıralanır ve sonuç olarak satır sayısı sınır ifadesi ile kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-109">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="5ac8f-110">Örneğin, sınır 5, sonuç kümesini 5 örnek veya satır olarak kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-110">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="5ac8f-111">SıNıR, ORDER BY yan tümcesinin mevcut olmasını gerektiren sınır ile en üst ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-111">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="5ac8f-112">SKIP ve LIMIT, ORDER BY yan tümcesiyle birlikte bağımsız olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-112">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ac8f-113">En üstteki değiştirici ve SKIP alt yan tümcesi aynı sorgu ifadesinde varsa, bir varlık SQL sorgusu geçersiz olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-113">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="5ac8f-114">ÜST ifade, sınır ifadesine göre değiştirilerek sorgunun yeniden yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-114">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ac8f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac8f-115">Example</span></span>  

 <span data-ttu-id="5ac8f-116">Aşağıdaki Entity SQL sorgusu, SELECT ifadesinde döndürülen nesneler üzerinde kullanılan sıralama düzenini belirtmek için LIMIT ile ORDER BY işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-116">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="5ac8f-117">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5ac8f-118">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5ac8f-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5ac8f-119">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5ac8f-120">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="5ac8f-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIMIT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="5ac8f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac8f-121">See also</span></span>

- [<span data-ttu-id="5ac8f-122">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="5ac8f-122">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="5ac8f-123">[Nasıl yapılır: sorgu sonuçları aracılığıyla sayfa oluşturma](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5ac8f-123">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="5ac8f-124">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="5ac8f-124">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="5ac8f-125">Sayfanın Üstü</span><span class="sxs-lookup"><span data-stu-id="5ac8f-125">TOP</span></span>](top-entity-sql.md)
