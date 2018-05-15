---
title: Birleşim (varlık SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 52a7a332166250e8fa8084986fd0d89da6fdf42d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="union-entity-sql"></a><span data-ttu-id="384e3-102">Birleşim (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="384e3-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="384e3-103">İki veya daha fazla sorguların sonuçlarını tek bir koleksiyona birleştirir.</span><span class="sxs-lookup"><span data-stu-id="384e3-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="384e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="384e3-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="384e3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="384e3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="384e3-106">Tüm ifadeler koleksiyonuyla birleştirmek için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.</span><span class="sxs-lookup"><span data-stu-id="384e3-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="384e3-107">UNION</span><span class="sxs-lookup"><span data-stu-id="384e3-107">UNION</span></span>  
 <span data-ttu-id="384e3-108">Birden çok koleksiyon birleştirilir ve tek bir koleksiyon olarak döndürülen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="384e3-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="384e3-109">TÜM</span><span class="sxs-lookup"><span data-stu-id="384e3-109">ALL</span></span>  
 <span data-ttu-id="384e3-110">Birden çok koleksiyon birleştirilir ve yinelenenleri de dahil olmak üzere tek bir koleksiyon döndürülen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="384e3-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="384e3-111">Belirtilmezse, yinelemeleri sonuç koleksiyonundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="384e3-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="384e3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="384e3-112">Return Value</span></span>  
 <span data-ttu-id="384e3-113">Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.</span><span class="sxs-lookup"><span data-stu-id="384e3-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="384e3-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="384e3-114">Remarks</span></span>  
 <span data-ttu-id="384e3-115">UNION biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="384e3-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="384e3-116">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="384e3-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="384e3-117">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="384e3-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="384e3-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="384e3-118">Example</span></span>  
 <span data-ttu-id="384e3-119">Aşağıdaki varlık SQL sorgusunu UNION ALL işleci iki sorguların sonuçlarını tek bir koleksiyona birleştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="384e3-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="384e3-120">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="384e3-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="384e3-121">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="384e3-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="384e3-122">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="384e3-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="384e3-123">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="384e3-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="384e3-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="384e3-124">See Also</span></span>  
 [<span data-ttu-id="384e3-125">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="384e3-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
