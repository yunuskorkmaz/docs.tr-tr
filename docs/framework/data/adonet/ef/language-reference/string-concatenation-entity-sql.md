---
title: + (Dize birleştirme) (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 8a1785d590c5f7fcc443856180d516bb40cfc28e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500886"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="e0e65-102">+ (Dize birleştirme) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="e0e65-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="e0e65-103">İki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="e0e65-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0e65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0e65-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e0e65-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e0e65-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e0e65-106">Herhangi bir geçerli ifade EDM. Veri türü dize.</span><span class="sxs-lookup"><span data-stu-id="e0e65-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="e0e65-107">Her iki ifade de aynı veri türünde olmalıdır veya bir ifade başka bir ifadenin veri türüne örtük dönüştürülmesi mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0e65-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e0e65-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="e0e65-108">Result Types</span></span>  
 <span data-ttu-id="e0e65-109">Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü.</span><span class="sxs-lookup"><span data-stu-id="e0e65-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="e0e65-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e0e65-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e65-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0e65-111">Example</span></span>  
 <span data-ttu-id="e0e65-112">Aşağıdaki varlık SQL sorgusu kullanır + işleci için iki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="e0e65-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="e0e65-113">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="e0e65-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e0e65-114">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="e0e65-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e0e65-115">Verilen yordamı izleyin [nasıl yapılır: Bu döndürür PrimitiveType sonuçları sorguyu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e0e65-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="e0e65-116">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="e0e65-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="e0e65-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0e65-117">See Also</span></span>  
 [<span data-ttu-id="e0e65-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0e65-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e0e65-119">Kavramsal Model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="e0e65-119">Conceptual Model Types (CSDL)</span></span>](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
