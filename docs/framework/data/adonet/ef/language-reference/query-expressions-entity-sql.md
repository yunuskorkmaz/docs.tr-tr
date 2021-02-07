---
description: 'Hakkında daha fazla bilgi edinin: sorgu Ifadeleri (Entity SQL)'
title: Sorgu Ifadeleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 218e7db0e812bd43a92d3145bc4bf96244ef6a3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696041"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="ad59e-103">Sorgu Ifadeleri (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ad59e-103">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="ad59e-104">Sorgu ifadesi birçok farklı sorgu işlecini tek bir sözdizimi halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ad59e-104">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="ad59e-105">Aşağıdakiler dahil olmak üzere çeşitli tür ifadeler sağlar: [değişmez değerler](literals-entity-sql.md), [Parametreler](parameters-entity-sql.md), [değişkenler](variables-entity-sql.md), işleçler, [işlevler](functions-entity-sql.md), set işleçleri, vb.</span><span class="sxs-lookup"><span data-stu-id="ad59e-105">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="ad59e-106">Daha fazla bilgi için bkz. [Entity SQL başvurusu](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="ad59e-106">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="ad59e-107">Yan tümceler</span><span class="sxs-lookup"><span data-stu-id="ad59e-107">Clauses</span></span>  

 <span data-ttu-id="ad59e-108">Sorgu ifadesi bir nesne koleksiyonuna art arda işlemler uygulayan bir dizi yan tümcelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ad59e-108">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="ad59e-109">Standart a SQL SELECT ifadesinde bulunan yan tümceleri temel alır: [Select](select-entity-sql.md), [from](from-entity-sql.md), [WHERE](where-entity-sql.md), [Group By](group-by-entity-sql.md), [HAVING](having-entity-sql.md)ve [order by](order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ad59e-109">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="ad59e-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="ad59e-110">Scope</span></span>  

 <span data-ttu-id="ad59e-111">FROM yan tümcesinde tanımlanan adlar, KIMDEN kapsamında, soldan sağa doğru bir şekilde tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ad59e-111">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="ad59e-112">JOIN listesinde, ifadeler listede daha önce tanımlanan adlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="ad59e-112">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="ad59e-113">FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri FROM kapsamına eklenmez: her zaman diğer ad-nitelenmiş ad aracılığıyla başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad59e-113">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="ad59e-114">Normal olarak, SELECT ifadesinin tüm parçaları FROM kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ad59e-114">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad59e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad59e-115">See also</span></span>

- [<span data-ttu-id="ad59e-116">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ad59e-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
