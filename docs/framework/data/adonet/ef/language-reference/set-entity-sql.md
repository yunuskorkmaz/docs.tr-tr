---
description: 'Daha fazla bilgi edinin: SET (Entity SQL)'
title: AYARLA (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 80be5b76e654c39776d97413c4ece5a8f3df8d2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768031"
---
# <a name="set-entity-sql"></a><span data-ttu-id="172e5-103">AYARLA (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="172e5-103">SET (Entity SQL)</span></span>

<span data-ttu-id="172e5-104">KÜME ifadesi, tüm yinelenen öğelerle kaldırılan yeni bir koleksiyon sunarak bir nesne koleksiyonunu bir kümesine dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="172e5-104">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="172e5-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="172e5-105">Syntax</span></span>  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="172e5-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="172e5-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="172e5-107">Bir koleksiyon döndüren geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="172e5-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="172e5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="172e5-108">Remarks</span></span>  

 <span data-ttu-id="172e5-109">Küme ifadesi `SET(c)` aşağıdaki SELECT deyimine mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="172e5-109">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="172e5-110">`SET` , [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ayarlanan işleçlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="172e5-110">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="172e5-111">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="172e5-111">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="172e5-112">Bkz. set işleçleri için öncelik bilgileri [hariç](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="172e5-112">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="172e5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="172e5-113">Example</span></span>  

 <span data-ttu-id="172e5-114">Aşağıdaki Entity SQL sorgu bir nesne koleksiyonunu bir kümesine dönüştürmek için SET ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="172e5-114">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="172e5-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="172e5-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="172e5-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="172e5-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="172e5-117">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="172e5-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="172e5-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="172e5-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a><span data-ttu-id="172e5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="172e5-119">See also</span></span>

- [<span data-ttu-id="172e5-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="172e5-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
