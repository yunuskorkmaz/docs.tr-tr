---
title: SONRA (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 5f0bbb0cadd736d476077685e08ba1a03b9c4001
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762890"
---
# <a name="then-entity-sql"></a><span data-ttu-id="fb1c6-102">SONRA (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="fb1c6-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="fb1c6-103">Sonuç olarak değerlendirildiğinde WHEN yan tümcesinin `true`.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb1c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb1c6-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb1c6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fb1c6-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="fb1c6-106">Geçerli bir Boole ifadesi.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="fb1c6-107">Bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb1c6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb1c6-108">Remarks</span></span>  
 <span data-ttu-id="fb1c6-109">Varsa `when_expression` değeri değerlendiren `true`, karşılık gelen sonucudur `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="fb1c6-110">Yoksa ne zaman, koşul karşılanır, `else-expression` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="fb1c6-111">Ancak, yoksa hiçbir `else-expression`, sonuç NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="fb1c6-112">Bir örnek için bkz: [durumda](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fb1c6-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb1c6-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb1c6-113">Example</span></span>  
 <span data-ttu-id="fb1c6-114">Bir dizi değerlendirmek için büyük/küçük HARFE ifade aşağıdaki varlık SQL sorgusunu kullanır `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="fb1c6-115">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fb1c6-116">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fb1c6-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fb1c6-117">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fb1c6-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="fb1c6-118">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fb1c6-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="fb1c6-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb1c6-119">See Also</span></span>  
 [<span data-ttu-id="fb1c6-120">CASE</span><span class="sxs-lookup"><span data-stu-id="fb1c6-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="fb1c6-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fb1c6-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
