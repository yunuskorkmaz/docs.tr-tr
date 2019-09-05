---
title: + (Dize birleştirme) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: ef482a1206dea98cfb5a0ba5071acc130ef0cd18
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249025"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="497e2-102">+ (Dize birleştirme) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="497e2-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="497e2-103">İki dizeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="497e2-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="497e2-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="497e2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="497e2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="497e2-106">EDM 'un geçerli herhangi bir ifadesi. Dize veri türleri.</span><span class="sxs-lookup"><span data-stu-id="497e2-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="497e2-107">Her iki ifade de aynı veri türünde olmalıdır veya bir ifadenin örtük olarak diğer ifadenin veri türüne dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="497e2-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="497e2-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="497e2-108">Result Types</span></span>  
 <span data-ttu-id="497e2-109">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="497e2-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="497e2-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="497e2-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="497e2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="497e2-111">Example</span></span>  
 <span data-ttu-id="497e2-112">Aşağıdaki Entity SQL sorgusu iki dizeyi birleştiren + işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="497e2-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="497e2-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="497e2-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="497e2-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="497e2-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="497e2-115">[Aşağıdaki adımları uygulayın: PrimitiveType sonuçları](../how-to-execute-a-query-that-returns-primitivetype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="497e2-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="497e2-116">Aşağıdaki sorguyu `ExecutePrimitiveTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="497e2-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="497e2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="497e2-117">See also</span></span>

- [<span data-ttu-id="497e2-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="497e2-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="497e2-119">Kavramsal model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="497e2-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
