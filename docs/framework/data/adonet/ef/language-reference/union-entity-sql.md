---
title: "Birleşim (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b62d874a9885ed864282c765cf428f3c2a445745
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="union-entity-sql"></a><span data-ttu-id="ae4a0-102">Birleşim (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ae4a0-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="ae4a0-103">İki veya daha fazla sorguların sonuçlarını tek bir koleksiyona birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae4a0-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ae4a0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ae4a0-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ae4a0-106">Tüm ifadeler koleksiyonuyla birleştirmek için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="ae4a0-107">UNION</span><span class="sxs-lookup"><span data-stu-id="ae4a0-107">UNION</span></span>  
 <span data-ttu-id="ae4a0-108">Birden çok koleksiyon birleştirilir ve tek bir koleksiyon olarak döndürülen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="ae4a0-109">TÜM</span><span class="sxs-lookup"><span data-stu-id="ae4a0-109">ALL</span></span>  
 <span data-ttu-id="ae4a0-110">Birden çok koleksiyon birleştirilir ve yinelenenleri de dahil olmak üzere tek bir koleksiyon döndürülen olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="ae4a0-111">Belirtilmezse, yinelemeleri sonuç koleksiyonundan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae4a0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae4a0-112">Return Value</span></span>  
 <span data-ttu-id="ae4a0-113">Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae4a0-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae4a0-114">Remarks</span></span>  
 <span data-ttu-id="ae4a0-115">UNION biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ae4a0-116">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ae4a0-117">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="ae4a0-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae4a0-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae4a0-118">Example</span></span>  
 <span data-ttu-id="ae4a0-119">Aşağıdaki varlık SQL sorgusunu UNION ALL işleci iki sorguların sonuçlarını tek bir koleksiyona birleştirmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="ae4a0-120">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ae4a0-121">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="ae4a0-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ae4a0-122">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ae4a0-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ae4a0-123">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="ae4a0-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="ae4a0-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae4a0-124">See Also</span></span>  
 [<span data-ttu-id="ae4a0-125">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ae4a0-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
