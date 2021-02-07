---
description: 'Hakkında daha fazla bilgi edinin: HAVING (Entity SQL)'
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 70ace20d67e93aa051873d2b32a49f560902e63d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696886"
---
# <a name="having-entity-sql"></a><span data-ttu-id="13428-103">HAVING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="13428-103">HAVING (Entity SQL)</span></span>

<span data-ttu-id="13428-104">Grup veya toplama için bir arama koşulu belirtir.</span><span class="sxs-lookup"><span data-stu-id="13428-104">Specifies a search condition for a group or an aggregate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13428-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13428-105">Syntax</span></span>  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="13428-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="13428-106">Arguments</span></span>  

 `search_condition`  
 <span data-ttu-id="13428-107">Grup veya toplanacak toplama için arama koşulunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="13428-107">Specifies the search condition for the group or the aggregate to meet.</span></span> <span data-ttu-id="13428-108">WITH GROUP for ALL kullanıldığında HAVING yan tümcesi tümünü geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="13428-108">When HAVING is used with GROUP BY ALL, the HAVING clause overrides ALL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13428-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13428-109">Remarks</span></span>  

 <span data-ttu-id="13428-110">HAVING yan tümcesi, bir gruplandırmanın sonucu üzerinde ek bir filtreleme koşulu belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13428-110">The HAVING clause is used to specify an additional filtering condition on the result of a grouping.</span></span> <span data-ttu-id="13428-111">Sorgu ifadesinde GROUP BY yan tümcesi belirtilmemişse, örtük bir tek küme grubu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="13428-111">If no GROUP BY clause is specified in the query expression, an implicit single-set group is assumed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13428-112">HAVING yalnızca [Select](select-entity-sql.md) ifadesiyle kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13428-112">HAVING can be used only with the [SELECT](select-entity-sql.md) statement.</span></span> <span data-ttu-id="13428-113">[Group By](group-by-entity-sql.md) kullanılmazsa WHERE yan tümcesi gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="13428-113">When [GROUP BY](group-by-entity-sql.md) is not used, HAVING behaves like a WHERE clause.</span></span>  
  
<span data-ttu-id="13428-114">HAVING yan tümcesi WHERE yan tümcesi gibi çalışarak GROUP BY işlemden sonra uygulanması hariç olur.</span><span class="sxs-lookup"><span data-stu-id="13428-114">The HAVING clause works like the WHERE clause except that it is applied after the GROUP BY operation.</span></span> <span data-ttu-id="13428-115">Bu, HAVING yan tümcesinin yalnızca diğer adları ve toplamaları gruplandırmak için aşağıdaki örnekte gösterildiği gibi başvuru yapabileceği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="13428-115">This means that the HAVING clause can only make references to grouping aliases and aggregates, as illustrated in the following example:</span></span>
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 <span data-ttu-id="13428-116">Önceki gruplar, grupları yalnızca birden fazla ürün içeren olanlarla kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="13428-116">The previous restricts the groups to only those that include more than one product.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13428-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="13428-117">Example</span></span>  

 <span data-ttu-id="13428-118">Aşağıdaki Entity SQL sorgusu, bir grup veya toplama için bir arama koşulu belirtmek üzere HAVING ve GROUP BY işleçlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="13428-118">The following Entity SQL query uses the HAVING and GROUP BY operators to specify a search condition for a group or an aggregate.</span></span> <span data-ttu-id="13428-119">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="13428-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="13428-120">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="13428-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="13428-121">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="13428-121">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="13428-122">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="13428-122">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a><span data-ttu-id="13428-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13428-123">See also</span></span>

- [<span data-ttu-id="13428-124">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="13428-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="13428-125">Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="13428-125">Query Expressions</span></span>](query-expressions-entity-sql.md)
