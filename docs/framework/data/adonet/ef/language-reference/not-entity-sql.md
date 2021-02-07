---
description: Hakkında daha fazla bilgi edinin:! BAŞLATıLMADı (Entity SQL)
title: '! BAŞLATıLMADı (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 648cc4ff73769ae280570b2d42934b2001fa5182
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696457"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="41f98-105">!</span><span class="sxs-lookup"><span data-stu-id="41f98-105">!</span></span> <span data-ttu-id="41f98-106">BAŞLATıLMADı (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="41f98-106">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="41f98-107">Bir ifadeyi geçersiz kılar `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="41f98-107">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f98-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="41f98-108">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="41f98-109">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="41f98-109">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="41f98-110">Boolean döndüren geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="41f98-110">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41f98-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41f98-111">Remarks</span></span>  

 <span data-ttu-id="41f98-112">Ünlem işareti (!), NOT işleci ile aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="41f98-112">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f98-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="41f98-113">Example</span></span>  

 <span data-ttu-id="41f98-114">Aşağıdaki Entity SQL sorgusu, bir ifadeyi geçersiz hale getirir için NOT işlecini kullanır `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="41f98-114">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="41f98-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="41f98-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="41f98-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="41f98-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="41f98-117">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="41f98-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="41f98-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="41f98-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="41f98-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41f98-119">See also</span></span>

- [<span data-ttu-id="41f98-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="41f98-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
