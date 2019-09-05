---
title: Sorgu Ifadeleri (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249269"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="3ac68-102">Sorgu Ifadeleri (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3ac68-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="3ac68-103">Sorgu ifadesi birçok farklı sorgu işlecini tek bir sözdizimi halinde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="3ac68-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3ac68-104">Aşağıdakiler dahil olmak üzere çeşitli tür ifadeler sağlar: [değişmez değerler](literals-entity-sql.md), [Parametreler](parameters-entity-sql.md), [değişkenler](variables-entity-sql.md), işleçler, [işlevler](functions-entity-sql.md), set işleçleri, vb.</span><span class="sxs-lookup"><span data-stu-id="3ac68-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="3ac68-105">Daha fazla bilgi için bkz. [Entity SQL başvurusu](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="3ac68-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="3ac68-106">Tümceler</span><span class="sxs-lookup"><span data-stu-id="3ac68-106">Clauses</span></span>  
 <span data-ttu-id="3ac68-107">Sorgu ifadesi bir nesne koleksiyonuna art arda işlemler uygulayan bir dizi yan tümcelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ac68-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="3ac68-108">Standart a SQL SELECT ifadesinde bulunan aynı yan tümceleri temel alır: [Select](select-entity-sql.md), [from](from-entity-sql.md), [WHERE](where-entity-sql.md), [Group By](group-by-entity-sql.md), [HAVING](having-entity-sql.md)ve [order by](order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3ac68-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="3ac68-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="3ac68-109">Scope</span></span>  
 <span data-ttu-id="3ac68-110">FROM yan tümcesinde tanımlanan adlar, KIMDEN kapsamında, soldan sağa doğru bir şekilde tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ac68-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="3ac68-111">JOIN listesinde, ifadeler listede daha önce tanımlanan adlara başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3ac68-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="3ac68-112">FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri FROM kapsamına eklenmez: Her zaman diğer ad-nitelenmiş ad aracılığıyla başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ac68-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="3ac68-113">Normal olarak, SELECT ifadesinin tüm parçaları FROM kapsamı içinde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3ac68-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac68-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ac68-114">See also</span></span>

- [<span data-ttu-id="3ac68-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3ac68-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
