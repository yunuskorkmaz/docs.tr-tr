---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936078"
---
# <a name="having-entity-sql"></a><span data-ttu-id="9f8b0-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9f8b0-102">HAVING (Entity SQL)</span></span>
<span data-ttu-id="9f8b0-103">Grup veya toplama için bir arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f8b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f8b0-104">Syntax</span></span>  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9f8b0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9f8b0-105">Arguments</span></span>  
 `search_condition`  
 <span data-ttu-id="9f8b0-106">Grup veya toplanacak toplama için arama koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="9f8b0-107">WITH GROUP for ALL kullanıldığında HAVING yan tümcesi tümünü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f8b0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f8b0-108">Remarks</span></span>  
 <span data-ttu-id="9f8b0-109">HAVING yan tümcesi, bir gruplandırmanın sonucu üzerinde ek bir filtreleme koşulu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="9f8b0-110">Sorgu ifadesinde GROUP BY yan tümcesi belirtilmemişse, örtük bir tek küme grubu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f8b0-111">HAVING yalnızca [Select](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) ifadesiyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-111">HAVING can be used only with the [SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) statement.</span></span> <span data-ttu-id="9f8b0-112">[Group By](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) kullanılmazsa WHERE yan tümcesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-112">When [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
 <span data-ttu-id="9f8b0-113">HAVING yan tümcesi WHERE yan tümcesi gibi çalışarak GROUP BY işlemden sonra uygulanması hariç olur.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="9f8b0-114">Bu, HAVING yan tümcesinin yalnızca diğer adları ve toplamaları gruplandırmak için aşağıdaki örnekte gösterildiği gibi başvuru yapabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example.</span></span>  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="9f8b0-115">Önceki gruplar, grupları yalnızca birden fazla ürün içeren olanlarla kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f8b0-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f8b0-116">Example</span></span>  
 <span data-ttu-id="9f8b0-117">Aşağıdaki Entity SQL sorgusu, bir grup veya toplama için bir arama koşulu belirtmek üzere HAVING ve GROUP BY işleçlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="9f8b0-118">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9f8b0-119">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9f8b0-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9f8b0-120">[Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="9f8b0-121">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="9f8b0-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a><span data-ttu-id="9f8b0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f8b0-122">See also</span></span>

- [<span data-ttu-id="9f8b0-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9f8b0-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="9f8b0-124">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9f8b0-124">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
