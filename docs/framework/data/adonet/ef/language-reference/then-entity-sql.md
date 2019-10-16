---
title: SONRA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319291"
---
# <a name="then-entity-sql"></a><span data-ttu-id="1eb69-102">SONRA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1eb69-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="1eb69-103">@No__t-0 olarak değerlendirildiğinde bir where yan tümcesinin sonucu.</span><span class="sxs-lookup"><span data-stu-id="1eb69-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eb69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1eb69-104">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1eb69-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1eb69-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="1eb69-106">Herhangi bir geçerli Boole ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1eb69-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="1eb69-107">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1eb69-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1eb69-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1eb69-108">Remarks</span></span>  
 <span data-ttu-id="1eb69-109">@No__t-0 `true` değerini verirse, sonuç karşılık gelen `then-expression` ' dir.</span><span class="sxs-lookup"><span data-stu-id="1eb69-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="1eb69-110">NE zaman koşullarından hiçbiri karşılanmıyorsa `else-expression` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1eb69-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="1eb69-111">Ancak, `else-expression` yoksa sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="1eb69-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="1eb69-112">Bir örnek için bkz. [Case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1eb69-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eb69-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1eb69-113">Example</span></span>  
 <span data-ttu-id="1eb69-114">Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadesi kümesini değerlendirmek için CASE ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1eb69-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="1eb69-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1eb69-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1eb69-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1eb69-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1eb69-117">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1eb69-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="1eb69-118">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="1eb69-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="1eb69-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1eb69-119">See also</span></span>

- [<span data-ttu-id="1eb69-120">CASE</span><span class="sxs-lookup"><span data-stu-id="1eb69-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="1eb69-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1eb69-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
