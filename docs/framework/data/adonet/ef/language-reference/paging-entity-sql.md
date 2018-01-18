---
title: "Disk belleği (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6398edb34a2389b113970444d98eec33f4833b93
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="paging-entity-sql"></a><span data-ttu-id="f18c9-102">Disk belleği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="f18c9-102">Paging (Entity SQL)</span></span>
<span data-ttu-id="f18c9-103">Fiziksel disk belleği kullanılarak yapılabilir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f18c9-103">Physical paging can be performed by using the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="f18c9-104">Belirleyici biçimde fiziksel disk belleği gerçekleştirmek için atla ve sınırı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f18c9-104">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="f18c9-105">Yalnızca bir determinsitic olmayan şekilde sonuç satır sayısı kısıtlamak istiyorsanız, kullanması gereken [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f18c9-105">If you only want to restrict the number of rows in the result in a non-determinsitic way, you should use [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span> <span data-ttu-id="f18c9-106">TOP ve SKIP/LIMIT karşılıklı olarak birbirini dışlar.</span><span class="sxs-lookup"><span data-stu-id="f18c9-106">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="f18c9-107">ÜST genel bakış</span><span class="sxs-lookup"><span data-stu-id="f18c9-107">TOP Overview</span></span>  
 <span data-ttu-id="f18c9-108">SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştiricisi izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir.</span><span class="sxs-lookup"><span data-stu-id="f18c9-108">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="f18c9-109">TOP alt yan tümcesi, yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir.</span><span class="sxs-lookup"><span data-stu-id="f18c9-109">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="f18c9-110">Daha fazla bilgi için bkz: [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f18c9-110">For more information, see [TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="f18c9-111">ATLA ve sınırı genel bakış</span><span class="sxs-lookup"><span data-stu-id="f18c9-111">SKIP And LIMIT Overview</span></span>  
 <span data-ttu-id="f18c9-112">ATLA ve sınırı ORDER BY yan tümcesi parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f18c9-112">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="f18c9-113">SKIP ifadesi alt yan bir ORDER BY yan tümcesinde varsa, sonuçları sıralama belirtimine göre sıralanır ve sonuç kümesi hemen sonra SKIP ifadesi sonraki satırdan başlayan satırlara dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="f18c9-113">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="f18c9-114">Örneğin, Atla 5 ilk beş satırını atlar ve İleri altıncı satırdaki döndürür.</span><span class="sxs-lookup"><span data-stu-id="f18c9-114">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="f18c9-115">İfade LIMIT alt yan ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve sonuçta elde edilen satır sayısı sınırı ifadeyle kısıtlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f18c9-115">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="f18c9-116">Örneğin, sınır 5 sonuç beş örneği veya satır kümesini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f18c9-116">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="f18c9-117">ATLA ve sınırı birlikte kullanılması gerekmez; yalnızca atlayın veya yalnızca ORDER BY yan tümcesi ile SINIRLAYABİLİRSİNİZ.</span><span class="sxs-lookup"><span data-stu-id="f18c9-117">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="f18c9-118">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="f18c9-118">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="f18c9-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="f18c9-119">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [<span data-ttu-id="f18c9-120">LIMIT</span><span class="sxs-lookup"><span data-stu-id="f18c9-120">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [<span data-ttu-id="f18c9-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="f18c9-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="f18c9-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f18c9-122">See Also</span></span>  
 [<span data-ttu-id="f18c9-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f18c9-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f18c9-124">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f18c9-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="f18c9-125">Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası</span><span class="sxs-lookup"><span data-stu-id="f18c9-125">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
