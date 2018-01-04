---
title: "(Varlık SQL) var."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0807be69419465a3d79f162e9738361a6ce8051a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exists-entity-sql"></a><span data-ttu-id="1381a-102">(Varlık SQL) var.</span><span class="sxs-lookup"><span data-stu-id="1381a-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="1381a-103">Bir koleksiyonu boş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1381a-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1381a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1381a-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1381a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1381a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1381a-106">Bir koleksiyonu döndüren herhangi geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="1381a-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="1381a-107">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="1381a-107">NOT</span></span>  
 <span data-ttu-id="1381a-108">EXISTS sonucunu tasarruflarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1381a-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1381a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1381a-109">Return Value</span></span>  
 <span data-ttu-id="1381a-110">`true`koleksiyon boş değilse; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="1381a-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1381a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1381a-111">Remarks</span></span>  
 <span data-ttu-id="1381a-112">EXISTS biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1381a-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1381a-113">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="1381a-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1381a-114">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1381a-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1381a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="1381a-115">Example</span></span>  
 <span data-ttu-id="1381a-116">Aşağıdaki varlık SQL sorgu EXISTS işlecini koleksiyonu boş olup olmadığını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="1381a-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="1381a-117">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1381a-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1381a-118">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1381a-118">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1381a-119">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1381a-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1381a-120">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1381a-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="1381a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1381a-121">See Also</span></span>  
 [<span data-ttu-id="1381a-122">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1381a-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
