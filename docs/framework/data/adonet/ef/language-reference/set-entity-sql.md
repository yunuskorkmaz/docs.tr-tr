---
title: SET (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 3008939798af98d449ec14e4d774ebc1a6e0d89d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="set-entity-sql"></a><span data-ttu-id="06303-102">SET (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="06303-102">SET (Entity SQL)</span></span>
<span data-ttu-id="06303-103">SET ifadesinin kaldırılan tüm yinelenen öğeler ile yeni bir koleksiyon sağlayan tarafından bir kümesine nesneler koleksiyonunu dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06303-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06303-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06303-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="06303-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="06303-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="06303-106">Bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="06303-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06303-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06303-107">Remarks</span></span>  
 <span data-ttu-id="06303-108">Set ifadesinin `SET(c)` şu select deyimi mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="06303-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="06303-109">`SET` biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06303-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="06303-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="06303-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="06303-111">Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) için öncelik bilgi [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06303-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06303-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="06303-112">Example</span></span>  
 <span data-ttu-id="06303-113">Aşağıdaki varlık SQL sorgusunu küme ifadesi bir kümesine nesneler koleksiyonunu dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="06303-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="06303-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="06303-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="06303-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="06303-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="06303-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="06303-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="06303-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="06303-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="06303-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06303-118">See Also</span></span>  
 [<span data-ttu-id="06303-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="06303-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
