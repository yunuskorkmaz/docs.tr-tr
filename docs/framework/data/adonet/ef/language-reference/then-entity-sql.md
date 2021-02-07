---
description: 'Daha fazla bilgi edinin: (Entity SQL)'
title: SONRA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: e1f0657cfef3786832f489434fd8fc0342e8687b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673472"
---
# <a name="then-entity-sql"></a><span data-ttu-id="acb3e-103">SONRA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="acb3e-103">THEN (Entity SQL)</span></span>

<span data-ttu-id="acb3e-104">Olarak değerlendirildiğinde bir where yan tümcesinin sonucu `true` .</span><span class="sxs-lookup"><span data-stu-id="acb3e-104">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acb3e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="acb3e-105">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="acb3e-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="acb3e-106">Arguments</span></span>  

 `when_expression`  
 <span data-ttu-id="acb3e-107">Herhangi bir geçerli Boole ifadesi.</span><span class="sxs-lookup"><span data-stu-id="acb3e-107">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="acb3e-108">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="acb3e-108">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acb3e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acb3e-109">Remarks</span></span>  

 <span data-ttu-id="acb3e-110">`when_expression`Değer değerlendirilirse `true` , sonuç karşılık gelir `then-expression` .</span><span class="sxs-lookup"><span data-stu-id="acb3e-110">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="acb3e-111">NE zaman koşullarından hiçbiri karşılanmıyorsa, olarak `else-expression` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="acb3e-111">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="acb3e-112">Ancak, hayır ise `else-expression` sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="acb3e-112">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="acb3e-113">Bir örnek için bkz. [Case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="acb3e-113">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="acb3e-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="acb3e-114">Example</span></span>  

 <span data-ttu-id="acb3e-115">Aşağıdaki Entity SQL sorgusu, bir ifade kümesini değerlendirmek için CASE ifadesini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="acb3e-115">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="acb3e-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="acb3e-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="acb3e-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="acb3e-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="acb3e-118">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="acb3e-118">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="acb3e-119">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="acb3e-119">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="acb3e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb3e-120">See also</span></span>

- [<span data-ttu-id="acb3e-121">HARFLERINI</span><span class="sxs-lookup"><span data-stu-id="acb3e-121">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="acb3e-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="acb3e-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
