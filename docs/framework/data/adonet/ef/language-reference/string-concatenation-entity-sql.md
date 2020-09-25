---
title: + (Dize birleştirme) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 92591448a3707ba11ad2462161050e48e0398728
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173633"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="2ffea-102">+ (Dize birleştirme) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2ffea-102">+ (String Concatenation) (Entity SQL)</span></span>

<span data-ttu-id="2ffea-103">İki dizeyi birleştirir.</span><span class="sxs-lookup"><span data-stu-id="2ffea-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ffea-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2ffea-104">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2ffea-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2ffea-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2ffea-106">EDM 'un geçerli herhangi bir ifadesi. Dize veri türleri.</span><span class="sxs-lookup"><span data-stu-id="2ffea-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="2ffea-107">Her iki ifade de aynı veri türünde olmalıdır veya bir ifadenin örtük olarak diğer ifadenin veri türüne dönüştürülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ffea-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2ffea-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="2ffea-108">Result Types</span></span>  

 <span data-ttu-id="2ffea-109">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="2ffea-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="2ffea-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2ffea-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ffea-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ffea-111">Example</span></span>  

 <span data-ttu-id="2ffea-112">Aşağıdaki Entity SQL sorgusu iki dizeyi birleştiren + işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ffea-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="2ffea-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2ffea-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2ffea-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2ffea-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2ffea-115">[Nasıl yapılır: PrimitiveType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-primitivetype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2ffea-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2ffea-116">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecutePrimitiveTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2ffea-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="2ffea-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ffea-117">See also</span></span>

- [<span data-ttu-id="2ffea-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ffea-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2ffea-119">Kavramsal model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="2ffea-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
