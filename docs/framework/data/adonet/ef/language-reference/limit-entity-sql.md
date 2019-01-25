---
title: SINIR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 3c38fd3fc20ad19bdeeca5c02c25de6c8269def6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493826"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="5e92d-102">SINIR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="5e92d-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="5e92d-103">Fiziksel disk belleği, ORDER BY yan tümcesinde LIMIT alt yan tümcesinin kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="5e92d-104">From tümcesi ORDER BY sınırı ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5e92d-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e92d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e92d-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5e92d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="5e92d-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="5e92d-107">Seçilir öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e92d-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="5e92d-108">Bir sınırı ifade alt yan tümcesi bir ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve elde edilen satır sayısı sınırı ifade tarafından sınırlanır.</span><span class="sxs-lookup"><span data-stu-id="5e92d-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="5e92d-109">Örneğin, sınırı 5 sonuç 5 örnekleri veya satır kümesi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="5e92d-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="5e92d-110">SINIRI sınırı bulunması ORDER BY yan tümcesini gerektirir bir özel durumla BAŞA işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="5e92d-111">Bağımsız olarak atla ve sınırı ORDER BY yan tümcesi ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e92d-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e92d-112">Bir varlık Sql sorgusu üst durumunda Geçersiz değiştirici olarak kabul edilir ve SKIP alt yan tümcesi, aynı sorgu ifadesinde vardır.</span><span class="sxs-lookup"><span data-stu-id="5e92d-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="5e92d-113">Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.</span><span class="sxs-lookup"><span data-stu-id="5e92d-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e92d-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e92d-114">Example</span></span>  
 <span data-ttu-id="5e92d-115">Aşağıdaki varlık SQL sorgusu ORDER BY işleci bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için sınır ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e92d-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="5e92d-116">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="5e92d-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5e92d-117">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5e92d-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5e92d-118">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5e92d-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="5e92d-119">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="5e92d-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="5e92d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e92d-120">See also</span></span>
- [<span data-ttu-id="5e92d-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="5e92d-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="5e92d-122">Nasıl yapılır: Sorgu sonuçları sayfasından</span><span class="sxs-lookup"><span data-stu-id="5e92d-122">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)
- [<span data-ttu-id="5e92d-123">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="5e92d-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="5e92d-124">TOP</span><span class="sxs-lookup"><span data-stu-id="5e92d-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
