---
title: "SINIR (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c0b2a421b1187fcf88278b66f3225133330a3033
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="limit-entity-sql"></a><span data-ttu-id="431ce-102">SINIR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="431ce-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="431ce-103">Fiziksel disk belleği, ORDER BY yan tümcesinde LIMIT alt yan tümcesinin kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="431ce-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="431ce-104">ORDER BY from yan tümcesi sınırı ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="431ce-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431ce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431ce-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="431ce-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="431ce-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="431ce-107">Seçilecek öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="431ce-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="431ce-108">İfade LIMIT alt yan ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve sonuçta elde edilen satır sayısı sınırı ifadeyle kısıtlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="431ce-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="431ce-109">Örneğin, sınır 5 sonuç 5 örnekleri veya satır kümesini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="431ce-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="431ce-110">SINIR sınırı bulunması ORDER BY yan tümcesi gerektirir özel durumla dön işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="431ce-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="431ce-111">Bağımsız olarak atla ve sınırı ORDER BY yan tümcesi ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="431ce-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="431ce-112">Varlık Sql sorgusu üst varsa geçersiz değiştirici olarak kabul edilir ve SKIP alt yan tümcesinin aynı sorgu ifadesinde yok.</span><span class="sxs-lookup"><span data-stu-id="431ce-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="431ce-113">Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.</span><span class="sxs-lookup"><span data-stu-id="431ce-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="431ce-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="431ce-114">Example</span></span>  
 <span data-ttu-id="431ce-115">Aşağıdaki varlık SQL sorgusunu ORDER BY işleci sınırı ile bir SELECT deyiminde döndürülen nesne üzerinde kullanılan sıralama düzenini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="431ce-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="431ce-116">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="431ce-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="431ce-117">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="431ce-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="431ce-118">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="431ce-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="431ce-119">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="431ce-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="431ce-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="431ce-120">See Also</span></span>  
 [<span data-ttu-id="431ce-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="431ce-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="431ce-122">Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası</span><span class="sxs-lookup"><span data-stu-id="431ce-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="431ce-123">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="431ce-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="431ce-124">TOP</span><span class="sxs-lookup"><span data-stu-id="431ce-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
