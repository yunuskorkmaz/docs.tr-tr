---
title: AYARLA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 76999bcbbb3b63fd945d2048734c58d97de8baea
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249234"
---
# <a name="set-entity-sql"></a><span data-ttu-id="93bb0-102">AYARLA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="93bb0-102">SET (Entity SQL)</span></span>
<span data-ttu-id="93bb0-103">KÜME ifadesi, tüm yinelenen öğelerle kaldırılan yeni bir koleksiyon sunarak bir nesne koleksiyonunu bir kümesine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93bb0-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93bb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93bb0-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="93bb0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="93bb0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="93bb0-106">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="93bb0-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93bb0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93bb0-107">Remarks</span></span>  
 <span data-ttu-id="93bb0-108">Küme ifadesi `SET(c)` aşağıdaki SELECT deyimine mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="93bb0-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="93bb0-109">`SET`, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="93bb0-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="93bb0-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="93bb0-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="93bb0-111">Bkz [](except-entity-sql.md) . [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçleri için öncelik bilgileri hariç.</span><span class="sxs-lookup"><span data-stu-id="93bb0-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93bb0-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="93bb0-112">Example</span></span>  
 <span data-ttu-id="93bb0-113">Aşağıdaki Entity SQL sorgu bir nesne koleksiyonunu bir kümesine dönüştürmek için SET ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="93bb0-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="93bb0-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="93bb0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="93bb0-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="93bb0-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="93bb0-116">[Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="93bb0-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="93bb0-117">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="93bb0-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="93bb0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93bb0-118">See also</span></span>

- [<span data-ttu-id="93bb0-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="93bb0-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
