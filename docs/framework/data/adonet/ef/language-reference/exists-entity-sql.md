---
title: VAR (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 20e18bf536f2b89eca9515b3c5dca7ca7fbd6fe5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250984"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="06aa4-102">VAR (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="06aa4-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="06aa4-103">Bir koleksiyonun boş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="06aa4-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06aa4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06aa4-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="06aa4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="06aa4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="06aa4-106">Bir koleksiyon döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="06aa4-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="06aa4-107">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="06aa4-107">NOT</span></span>  
 <span data-ttu-id="06aa4-108">Sonucunun var olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="06aa4-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06aa4-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06aa4-109">Return Value</span></span>  
 <span data-ttu-id="06aa4-110">`true`koleksiyon boş değilse, Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="06aa4-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06aa4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06aa4-111">Remarks</span></span>  
 <span data-ttu-id="06aa4-112">EXISTS, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set işleçlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="06aa4-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="06aa4-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] küme işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="06aa4-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="06aa4-114">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Set işleçleri için öncelik bilgileri için bkz. [except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="06aa4-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06aa4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="06aa4-115">Example</span></span>  
 <span data-ttu-id="06aa4-116">Aşağıdaki Entity SQL sorgusu, koleksiyonun boş olup olmadığını anlamak için EXISTS işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="06aa4-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="06aa4-117">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="06aa4-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="06aa4-118">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="06aa4-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="06aa4-119">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="06aa4-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="06aa4-120">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="06aa4-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="06aa4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06aa4-121">See also</span></span>

- [<span data-ttu-id="06aa4-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="06aa4-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
