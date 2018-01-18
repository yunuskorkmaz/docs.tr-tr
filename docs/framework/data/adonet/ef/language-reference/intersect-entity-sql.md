---
title: "INTERSECT (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 38814d3f4e8bca6a3a20d14c41d7674a205e30d2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="4b9fc-102">INTERSECT (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="4b9fc-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="4b9fc-103">Her iki sorgu ifadeleri sol tarafından döndürülen tüm farklı değerler koleksiyonu ve INTERSECT işleneni sağ tarafında döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="4b9fc-104">Tüm ifadeler aynı türde veya ortak bir temel veya türetilmiş türünde olması gerekir `expression`.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b9fc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b9fc-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b9fc-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4b9fc-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4b9fc-107">Başka bir sorgu ifadesinden döndürülen koleksiyonu ile karşılaştırmak için bir koleksiyon döndürür herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b9fc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4b9fc-108">Return Value</span></span>  
 <span data-ttu-id="4b9fc-109">Aynı türde veya ortak bir temel veya türetilmiş türde bir koleksiyonu `expression`.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b9fc-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b9fc-110">Remarks</span></span>  
 <span data-ttu-id="4b9fc-111">INTERSECT biridir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="4b9fc-112">Tüm [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kümesi işleçleri soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="4b9fc-113">Öncelik bilgilerini [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri, bakın [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="4b9fc-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b9fc-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b9fc-114">Example</span></span>  
 <span data-ttu-id="4b9fc-115">Aşağıdaki varlık SQL sorgusunu INTERSECT işlecini hem sorgu ifadeleri sol tarafından döndürülen tüm farklı değerler koleksiyonu ve INTERSECT işleneni sağ tarafında döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="4b9fc-116">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4b9fc-117">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="4b9fc-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4b9fc-118">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4b9fc-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4b9fc-119">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="4b9fc-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="4b9fc-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b9fc-120">See Also</span></span>  
 [<span data-ttu-id="4b9fc-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4b9fc-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
