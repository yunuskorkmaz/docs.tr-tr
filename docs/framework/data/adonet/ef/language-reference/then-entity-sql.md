---
title: SONRA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: c64e440e8cd8f86706db69d923ba7085d0cb3b3a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248986"
---
# <a name="then-entity-sql"></a><span data-ttu-id="5436b-102">SONRA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5436b-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="5436b-103">Olarak `true`değerlendirildiğinde bir where yan tümcesinin sonucu.</span><span class="sxs-lookup"><span data-stu-id="5436b-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5436b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5436b-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5436b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5436b-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="5436b-106">Herhangi bir geçerli Boole ifadesi.</span><span class="sxs-lookup"><span data-stu-id="5436b-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="5436b-107">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="5436b-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5436b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5436b-108">Remarks</span></span>  
 <span data-ttu-id="5436b-109">`then-expression`Değer `when_expression` değerlendirilirse,`true`sonuç karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="5436b-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="5436b-110">Ne zaman koşullarından hiçbiri karşılanmıyorsa, olarak `else-expression` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5436b-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="5436b-111">Ancak, Hayır `else-expression`ise sonuç null olur.</span><span class="sxs-lookup"><span data-stu-id="5436b-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="5436b-112">Bir örnek için bkz. [Case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5436b-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5436b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="5436b-113">Example</span></span>  
 <span data-ttu-id="5436b-114">Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifade kümesini değerlendirmek için Case ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5436b-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="5436b-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="5436b-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5436b-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5436b-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5436b-117">[Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="5436b-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="5436b-118">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="5436b-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="5436b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5436b-119">See also</span></span>

- [<span data-ttu-id="5436b-120">CASE</span><span class="sxs-lookup"><span data-stu-id="5436b-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="5436b-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5436b-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
