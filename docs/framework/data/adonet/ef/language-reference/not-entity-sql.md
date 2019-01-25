---
title: '! (NOT) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 238c9a1e1f82ab635c6b23359d9237cc2b3ed574
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596728"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="cf8ce-103">!</span><span class="sxs-lookup"><span data-stu-id="cf8ce-103">!</span></span> <span data-ttu-id="cf8ce-104">(NOT) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="cf8ce-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="cf8ce-105">Verilerek bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="cf8ce-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf8ce-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf8ce-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="cf8ce-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="cf8ce-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="cf8ce-108">Bir Boole değeri döndüren herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="cf8ce-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf8ce-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf8ce-109">Remarks</span></span>  
 <span data-ttu-id="cf8ce-110">Ünlem işareti (!), NOT işleci ile aynı işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cf8ce-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8ce-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf8ce-111">Example</span></span>  
 <span data-ttu-id="cf8ce-112">Aşağıdaki varlık SQL sorgusu verilerek için değil işlecini kullanan bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="cf8ce-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="cf8ce-113">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="cf8ce-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cf8ce-114">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="cf8ce-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cf8ce-115">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="cf8ce-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="cf8ce-116">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="cf8ce-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="cf8ce-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf8ce-117">See also</span></span>
- [<span data-ttu-id="cf8ce-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cf8ce-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
