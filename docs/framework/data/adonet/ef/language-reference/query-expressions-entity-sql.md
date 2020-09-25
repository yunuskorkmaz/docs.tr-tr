---
title: Sorgu Ifadeleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: ca6b79b4b3d3326a74780345decf58367596adb0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175609"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="c740f-102">Sorgu Ifadeleri (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c740f-102">Query Expressions (Entity SQL)</span></span>

<span data-ttu-id="c740f-103">Sorgu ifadesi birçok farklı sorgu işlecini tek bir sözdizimi halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="c740f-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="c740f-104">Aşağıdakiler dahil olmak üzere çeşitli tür ifadeler sağlar: [değişmez değerler](literals-entity-sql.md), [Parametreler](parameters-entity-sql.md), [değişkenler](variables-entity-sql.md), işleçler, [işlevler](functions-entity-sql.md), set işleçleri, vb.</span><span class="sxs-lookup"><span data-stu-id="c740f-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="c740f-105">Daha fazla bilgi için bkz. [Entity SQL başvurusu](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="c740f-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="c740f-106">Yan tümceler</span><span class="sxs-lookup"><span data-stu-id="c740f-106">Clauses</span></span>  

 <span data-ttu-id="c740f-107">Sorgu ifadesi bir nesne koleksiyonuna art arda işlemler uygulayan bir dizi yan tümcelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c740f-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="c740f-108">Standart a SQL SELECT ifadesinde bulunan yan tümceleri temel alır: [Select](select-entity-sql.md), [from](from-entity-sql.md), [WHERE](where-entity-sql.md), [Group By](group-by-entity-sql.md), [HAVING](having-entity-sql.md)ve [order by](order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="c740f-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="c740f-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="c740f-109">Scope</span></span>  

 <span data-ttu-id="c740f-110">FROM yan tümcesinde tanımlanan adlar, KIMDEN kapsamında, soldan sağa doğru bir şekilde tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c740f-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="c740f-111">JOIN listesinde, ifadeler listede daha önce tanımlanan adlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c740f-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="c740f-112">FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri FROM kapsamına eklenmez: her zaman diğer ad-nitelenmiş ad aracılığıyla başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c740f-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="c740f-113">Normal olarak, SELECT ifadesinin tüm parçaları FROM kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c740f-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c740f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c740f-114">See also</span></span>

- [<span data-ttu-id="c740f-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="c740f-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
