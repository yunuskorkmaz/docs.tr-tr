---
title: '! BAŞLATıLMADı (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319527"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="2480f-103">!</span><span class="sxs-lookup"><span data-stu-id="2480f-103">!</span></span> <span data-ttu-id="2480f-104">BAŞLATıLMADı (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2480f-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="2480f-105">@No__t-0 ifadesini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2480f-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2480f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2480f-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a><span data-ttu-id="2480f-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="2480f-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="2480f-108">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="2480f-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2480f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2480f-109">Remarks</span></span>  
 <span data-ttu-id="2480f-110">Ünlem işareti (!), NOT işleci ile aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2480f-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2480f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2480f-111">Example</span></span>  
 <span data-ttu-id="2480f-112">Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadesini geçersiz hale getirir için NOT işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2480f-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="2480f-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2480f-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2480f-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2480f-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2480f-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2480f-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2480f-116">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="2480f-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="2480f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2480f-117">See also</span></span>

- [<span data-ttu-id="2480f-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2480f-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
