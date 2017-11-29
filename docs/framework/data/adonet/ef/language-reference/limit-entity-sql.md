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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c890bf6950f94c04350902276193f5a43239f63f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="limit-entity-sql"></a><span data-ttu-id="baba7-102">SINIR (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="baba7-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="baba7-103">Fiziksel disk belleği, ORDER BY yan tümcesinde LIMIT alt yan tümcesinin kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="baba7-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="baba7-104">ORDER BY from yan tümcesi sınırı ayrı olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="baba7-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baba7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baba7-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="baba7-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="baba7-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="baba7-107">Seçilecek öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="baba7-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="baba7-108">İfade LIMIT alt yan ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve sonuçta elde edilen satır sayısı sınırı ifadeyle kısıtlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="baba7-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="baba7-109">Örneğin, sınır 5 sonuç 5 örnekleri veya satır kümesini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="baba7-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="baba7-110">SINIR sınırı bulunması ORDER BY yan tümcesi gerektirir özel durumla dön işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="baba7-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="baba7-111">Bağımsız olarak atla ve sınırı ORDER BY yan tümcesi ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="baba7-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baba7-112">Varlık Sql sorgusu üst varsa geçersiz değiştirici olarak kabul edilir ve SKIP alt yan tümcesinin aynı sorgu ifadesinde yok.</span><span class="sxs-lookup"><span data-stu-id="baba7-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="baba7-113">Sorgu TOP ifadesi için sınır ifade değiştirerek yazılması.</span><span class="sxs-lookup"><span data-stu-id="baba7-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baba7-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="baba7-114">Example</span></span>  
 <span data-ttu-id="baba7-115">Aşağıdaki varlık SQL sorgusunu ORDER BY işleci sınırı ile bir SELECT deyiminde döndürülen nesne üzerinde kullanılan sıralama düzenini belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="baba7-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="baba7-116">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="baba7-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="baba7-117">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="baba7-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="baba7-118">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="baba7-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="baba7-119">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="baba7-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="baba7-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="baba7-120">See Also</span></span>  
 [<span data-ttu-id="baba7-121">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="baba7-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="baba7-122">Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası</span><span class="sxs-lookup"><span data-stu-id="baba7-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="baba7-123">Disk belleği</span><span class="sxs-lookup"><span data-stu-id="baba7-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="baba7-124">SAYFANIN ÜSTÜ</span><span class="sxs-lookup"><span data-stu-id="baba7-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
