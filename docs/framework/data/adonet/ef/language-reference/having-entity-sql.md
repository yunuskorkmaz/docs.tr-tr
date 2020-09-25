---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: a117f377b3f03b6a1a12e39426a24f3141aa40ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204469"
---
# <a name="having-entity-sql"></a><span data-ttu-id="73c24-102">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73c24-102">HAVING (Entity SQL)</span></span>

<span data-ttu-id="73c24-103">Grup veya toplama için bir arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c24-103">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c24-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="73c24-104">Syntax</span></span>  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="73c24-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="73c24-105">Arguments</span></span>  

 `search_condition`  
 <span data-ttu-id="73c24-106">Grup veya toplanacak toplama için arama koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="73c24-106">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="73c24-107">WITH GROUP for ALL kullanıldığında HAVING yan tümcesi tümünü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="73c24-107">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73c24-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73c24-108">Remarks</span></span>  

 <span data-ttu-id="73c24-109">HAVING yan tümcesi, bir gruplandırmanın sonucu üzerinde ek bir filtreleme koşulu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73c24-109">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="73c24-110">Sorgu ifadesinde GROUP BY yan tümcesi belirtilmemişse, örtük bir tek küme grubu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="73c24-110">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73c24-111">HAVING yalnızca [Select](select-entity-sql.md) ifadesiyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73c24-111">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="73c24-112">[Group By](group-by-entity-sql.md) kullanılmazsa WHERE yan tümcesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="73c24-112">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
<span data-ttu-id="73c24-113">HAVING yan tümcesi WHERE yan tümcesi gibi çalışarak GROUP BY işlemden sonra uygulanması hariç olur.</span><span class="sxs-lookup"><span data-stu-id="73c24-113">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="73c24-114">Bu, HAVING yan tümcesinin yalnızca diğer adları ve toplamaları gruplandırmak için aşağıdaki örnekte gösterildiği gibi başvuru yapabileceği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="73c24-114">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example:</span></span>
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="73c24-115">Önceki gruplar, grupları yalnızca birden fazla ürün içeren olanlarla kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="73c24-115">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c24-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="73c24-116">Example</span></span>  

 <span data-ttu-id="73c24-117">Aşağıdaki Entity SQL sorgusu, bir grup veya toplama için bir arama koşulu belirtmek üzere HAVING ve GROUP BY işleçlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="73c24-117">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="73c24-118">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="73c24-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73c24-119">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="73c24-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="73c24-120">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="73c24-120">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="73c24-121">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="73c24-121">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a><span data-ttu-id="73c24-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73c24-122">See also</span></span>

- [<span data-ttu-id="73c24-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="73c24-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="73c24-124">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="73c24-124">Query Expressions</span></span>](query-expressions-entity-sql.md)
