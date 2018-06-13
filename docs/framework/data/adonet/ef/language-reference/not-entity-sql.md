---
title: '! (YOK) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 17bc89e6e97b037db035a6f65cd0ec82b840c308
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762068"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="b19cf-103">!</span><span class="sxs-lookup"><span data-stu-id="b19cf-103">!</span></span> <span data-ttu-id="b19cf-104">(YOK) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="b19cf-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="b19cf-105">Üzerindeki geçersiz kılar bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="b19cf-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b19cf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b19cf-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b19cf-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="b19cf-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="b19cf-108">Tüm geçerli ifade bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b19cf-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b19cf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b19cf-109">Remarks</span></span>  
 <span data-ttu-id="b19cf-110">Ünlem işareti (!) NOT işleci aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b19cf-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b19cf-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b19cf-111">Example</span></span>  
 <span data-ttu-id="b19cf-112">Aşağıdaki varlık SQL sorgusunu üzerindeki geçersiz kılar için değil işlecini kullanan bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="b19cf-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="b19cf-113">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b19cf-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b19cf-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="b19cf-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b19cf-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b19cf-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b19cf-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="b19cf-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="b19cf-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b19cf-117">See Also</span></span>  
 [<span data-ttu-id="b19cf-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b19cf-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
