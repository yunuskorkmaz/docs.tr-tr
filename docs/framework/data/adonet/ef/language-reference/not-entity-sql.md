---
title: '! BAŞLATıLMADı (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 4055d56d878b817fe88bb0dacb53ea39061bc4b2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249856"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="bf613-103">!</span><span class="sxs-lookup"><span data-stu-id="bf613-103">!</span></span> <span data-ttu-id="bf613-104">BAŞLATıLMADı (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bf613-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="bf613-105">Bir `Boolean` ifadeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="bf613-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf613-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf613-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf613-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="bf613-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="bf613-108">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="bf613-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf613-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf613-109">Remarks</span></span>  
 <span data-ttu-id="bf613-110">Ünlem işareti (!), NOT işleci ile aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bf613-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf613-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf613-111">Example</span></span>  
 <span data-ttu-id="bf613-112">Aşağıdaki Entity SQL sorgusu, bir `Boolean` ifadeyi geçersiz hale getirir için Not işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf613-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="bf613-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bf613-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bf613-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bf613-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bf613-115">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="bf613-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bf613-116">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="bf613-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="bf613-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf613-117">See also</span></span>

- [<span data-ttu-id="bf613-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bf613-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
