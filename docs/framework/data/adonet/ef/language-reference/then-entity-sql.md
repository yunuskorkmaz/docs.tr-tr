---
title: SONRA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: f038f242bc0873df3d72700aa05fca2f76f777ff
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161678"
---
# <a name="then-entity-sql"></a><span data-ttu-id="8c40c-102">SONRA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8c40c-102">THEN (Entity SQL)</span></span>

<span data-ttu-id="8c40c-103">Olarak değerlendirildiğinde bir where yan tümcesinin sonucu `true` .</span><span class="sxs-lookup"><span data-stu-id="8c40c-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c40c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8c40c-104">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c40c-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8c40c-105">Arguments</span></span>  

 `when_expression`  
 <span data-ttu-id="8c40c-106">Herhangi bir geçerli Boole ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8c40c-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="8c40c-107">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8c40c-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c40c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8c40c-108">Remarks</span></span>  

 <span data-ttu-id="8c40c-109">`when_expression`Değer değerlendirilirse `true` , sonuç karşılık gelir `then-expression` .</span><span class="sxs-lookup"><span data-stu-id="8c40c-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="8c40c-110">NE zaman koşullarından hiçbiri karşılanmıyorsa, olarak `else-expression` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="8c40c-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="8c40c-111">Ancak, hayır ise `else-expression` sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="8c40c-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="8c40c-112">Bir örnek için bkz. [Case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8c40c-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c40c-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c40c-113">Example</span></span>  

 <span data-ttu-id="8c40c-114">Aşağıdaki Entity SQL sorgusu, bir ifade kümesini değerlendirmek için CASE ifadesini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8c40c-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="8c40c-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8c40c-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8c40c-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8c40c-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8c40c-117">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="8c40c-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="8c40c-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="8c40c-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="8c40c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c40c-119">See also</span></span>

- [<span data-ttu-id="8c40c-120">HARFLERINI</span><span class="sxs-lookup"><span data-stu-id="8c40c-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="8c40c-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8c40c-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
