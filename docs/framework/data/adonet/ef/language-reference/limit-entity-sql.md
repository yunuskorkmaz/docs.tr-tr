---
title: SINIR (varlık SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 44b28ec265a18632e936ba05e25840a03f68da90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119021"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="ab33b-102">SINIR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ab33b-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="ab33b-103">Fiziksel disk belleği, ORDER BY yan tümcesinde LIMIT alt yan tümcesinin kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ab33b-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="ab33b-104">From tümcesi ORDER BY sınırı ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ab33b-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab33b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab33b-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab33b-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ab33b-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="ab33b-107">Seçilir öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="ab33b-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="ab33b-108">Bir sınırı ifade alt yan tümcesi bir ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve elde edilen satır sayısı sınırı ifade tarafından sınırlanır.</span><span class="sxs-lookup"><span data-stu-id="ab33b-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="ab33b-109">Örneğin, sınırı 5 sonuç 5 örnekleri veya satır kümesi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="ab33b-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="ab33b-110">SINIRI sınırı bulunması ORDER BY yan tümcesini gerektirir bir özel durumla BAŞA işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ab33b-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="ab33b-111">Bağımsız olarak atla ve sınırı ORDER BY yan tümcesi ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab33b-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab33b-112">Bir varlık Sql sorgusu üst durumunda Geçersiz değiştirici olarak kabul edilir ve SKIP alt yan tümcesi, aynı sorgu ifadesinde vardır.</span><span class="sxs-lookup"><span data-stu-id="ab33b-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="ab33b-113">Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.</span><span class="sxs-lookup"><span data-stu-id="ab33b-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab33b-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab33b-114">Example</span></span>  
 <span data-ttu-id="ab33b-115">Aşağıdaki varlık SQL sorgusu ORDER BY işleci bir SELECT deyiminde döndürülen nesneler üzerinde kullanılan sıralama düzeni belirlemek için sınır ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="ab33b-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="ab33b-116">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="ab33b-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ab33b-117">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ab33b-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ab33b-118">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ab33b-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ab33b-119">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ab33b-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="ab33b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab33b-120">See also</span></span>

- [<span data-ttu-id="ab33b-121">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="ab33b-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="ab33b-122">Nasıl yapılır: Sorgu sonuçları sayfasından</span><span class="sxs-lookup"><span data-stu-id="ab33b-122">How to: Page Through Query Results</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [<span data-ttu-id="ab33b-123">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="ab33b-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="ab33b-124">TOP</span><span class="sxs-lookup"><span data-stu-id="ab33b-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
