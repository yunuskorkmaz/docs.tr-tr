---
title: SET (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 4e2a387cf400a881dfd91c61b36ee3ce0f5a4431
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309439"
---
# <a name="set-entity-sql"></a><span data-ttu-id="d7050-102">SET (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="d7050-102">SET (Entity SQL)</span></span>
<span data-ttu-id="d7050-103">Küme ifadesinin, kaldırılan tüm yinelenen öğeleri ile yeni bir koleksiyon sonuçlanmıyor tarafından bir küme içine nesneler koleksiyonunu dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7050-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7050-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7050-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7050-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d7050-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d7050-106">Bir koleksiyon döndürür herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="d7050-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7050-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7050-107">Remarks</span></span>  
 <span data-ttu-id="d7050-108">Küme ifadesinin `SET(c)` aşağıdaki select deyimine mantıksal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="d7050-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` <span data-ttu-id="d7050-109">biri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d7050-109">is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="d7050-110">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleci soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d7050-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="d7050-111">Bkz: [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) öncelik bilgileri için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d7050-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7050-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7050-112">Example</span></span>  
 <span data-ttu-id="d7050-113">Aşağıdaki varlık SQL sorgusu, nesnelerin bir koleksiyonunu bir kümeyi dönüştürmek küme ifadesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d7050-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="d7050-114">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="d7050-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d7050-115">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d7050-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d7050-116">Verilen yordamı izleyin [nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d7050-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="d7050-117">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d7050-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="d7050-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7050-118">See also</span></span>

- [<span data-ttu-id="d7050-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d7050-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
