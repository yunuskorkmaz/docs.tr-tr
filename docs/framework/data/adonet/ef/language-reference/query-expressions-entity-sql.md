---
title: "Sorgu ifadeleri (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ad130797be55b33b319ca4e85de09ec3e00a554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="5736b-102">Sorgu ifadeleri (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="5736b-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="5736b-103">Bir sorgu ifadesi tek bir sözdizimi birçok farklı sorgu işleçleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="5736b-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5736b-104">ifadeler, aşağıdakiler dahil çeşitli sağlar: [değişmez değerleri](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametreleri](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [değişkenleri](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), işleçler, [işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)ayarlamak işleçler ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="5736b-104"> provides various kinds of expressions, including the following: [literals](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parameters](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [variables](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operators, [functions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="5736b-105">Daha fazla bilgi için bkz: [varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5736b-105">For more information, see [Entity SQL Reference](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="5736b-106">Tümceler</span><span class="sxs-lookup"><span data-stu-id="5736b-106">Clauses</span></span>  
 <span data-ttu-id="5736b-107">Bir sorgu ifadesi art arda işlemleri için nesneler koleksiyonunu uygulamak yan tümceleri bir dizi oluşur.</span><span class="sxs-lookup"><span data-stu-id="5736b-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="5736b-108">Standart bir SQL select deyimi bulunan aynı yan tümceleri üzerinde temel alır: [seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [nerede](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [Sahip](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), ve [sıralama ölçütü](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5736b-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [WHERE](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), and [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="5736b-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5736b-109">Scope</span></span>  
 <span data-ttu-id="5736b-110">FROM yan tümcesinde tanımlanan adları soldan sağa görünümünü FROM kapsamı içine sunulur.</span><span class="sxs-lookup"><span data-stu-id="5736b-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="5736b-111">BİRLEŞİM listesinde ifadeleri listede daha önce tanımlanan adlarını başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="5736b-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="5736b-112">FROM yan tümcesinde tanımlanan öğelerin ortak özellikleri FROM kapsama eklenmedi: diğer tam adının her zaman başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5736b-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="5736b-113">Normalde, select ifadesi tüm parçalarını FROM kapsamında olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5736b-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5736b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5736b-114">See Also</span></span>  
 [<span data-ttu-id="5736b-115">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5736b-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
