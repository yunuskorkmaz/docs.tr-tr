---
description: 'Hakkında daha fazla bilgi edinin: + (dize birleştirme) (Entity SQL)'
title: + (Dize birleştirme) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 7b6aac5b865e2127bb23446248e20d83ea3c7ea3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791848"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="fb2bf-103">+ (Dize birleştirme) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fb2bf-103">+ (String Concatenation) (Entity SQL)</span></span>

<span data-ttu-id="fb2bf-104">İki dizeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-104">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2bf-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fb2bf-105">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb2bf-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="fb2bf-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="fb2bf-107">EDM 'un geçerli herhangi bir ifadesi. Dize veri türleri.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-107">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="fb2bf-108">Her iki ifade de aynı veri türünde olmalıdır veya bir ifadenin örtük olarak diğer ifadenin veri türüne dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-108">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fb2bf-109">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="fb2bf-109">Result Types</span></span>  

 <span data-ttu-id="fb2bf-110">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-110">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fb2bf-111">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fb2bf-111">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb2bf-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="fb2bf-112">Example</span></span>  

 <span data-ttu-id="fb2bf-113">Aşağıdaki Entity SQL sorgusu iki dizeyi birleştiren + işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-113">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="fb2bf-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fb2bf-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fb2bf-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fb2bf-116">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="fb2bf-117">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="fb2bf-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="fb2bf-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb2bf-118">See also</span></span>

- [<span data-ttu-id="fb2bf-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fb2bf-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fb2bf-120">Kavramsal model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="fb2bf-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
