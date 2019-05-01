---
title: SONRA (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 8d2d7f9a3a1d6ff9f25db3f19bf8f39781469f9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797650"
---
# <a name="then-entity-sql"></a><span data-ttu-id="6b69f-102">SONRA (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="6b69f-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="6b69f-103">Sonuç olarak değerlendirildiğinde WHEN yan tümcesinin `true`.</span><span class="sxs-lookup"><span data-stu-id="6b69f-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b69f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b69f-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b69f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6b69f-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="6b69f-106">Geçerli bir Boolean ifadesi.</span><span class="sxs-lookup"><span data-stu-id="6b69f-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="6b69f-107">Bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="6b69f-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b69f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b69f-108">Remarks</span></span>  
 <span data-ttu-id="6b69f-109">Varsa `when_expression` değere Değerlenen `true`, karşılık gelen sonucudur `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="6b69f-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="6b69f-110">Yoksa ne zaman koşullar sağlanırsa, `else-expression` değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6b69f-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="6b69f-111">Ancak, yoksa hiçbir `else-expression`, sonuç NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="6b69f-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="6b69f-112">Bir örnek için bkz. [çalışması](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6b69f-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b69f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b69f-113">Example</span></span>  
 <span data-ttu-id="6b69f-114">Aşağıdaki varlık SQL sorgusu, bir dizi değerlendirmek için CASE ifadesi kullanır. `Boolean` ifadeler.</span><span class="sxs-lookup"><span data-stu-id="6b69f-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="6b69f-115">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="6b69f-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6b69f-116">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6b69f-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6b69f-117">Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6b69f-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="6b69f-118">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="6b69f-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="6b69f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b69f-119">See also</span></span>

- [<span data-ttu-id="6b69f-120">CASE</span><span class="sxs-lookup"><span data-stu-id="6b69f-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)
- [<span data-ttu-id="6b69f-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6b69f-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
