---
title: "(Modül) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a04b2972c80aff654331aeb319390b6f817374bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="79ac9-102">(Modül) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="79ac9-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="79ac9-103">Bir başkası tarafından ayrılmış bir ifade kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="79ac9-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79ac9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79ac9-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="79ac9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="79ac9-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="79ac9-106">Bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="79ac9-106">The numeric expression to divide.</span></span> <span data-ttu-id="79ac9-107">`dividend`sayısal veri türleri herhangi birinin geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="79ac9-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="79ac9-108">Tarafından bölünen bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="79ac9-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="79ac9-109">`divisor`sayısal veri türleri herhangi birinin geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="79ac9-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="79ac9-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="79ac9-110">Result Types</span></span>  
 <span data-ttu-id="79ac9-111">EDM.Int32</span><span class="sxs-lookup"><span data-stu-id="79ac9-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="79ac9-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="79ac9-112">Example</span></span>  
 <span data-ttu-id="79ac9-113">Aşağıdaki varlık SQL sorgusunu % aritmetik işleç başkası tarafından ayrılmış bir ifade kalanı döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="79ac9-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="79ac9-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="79ac9-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="79ac9-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="79ac9-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="79ac9-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="79ac9-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="79ac9-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="79ac9-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="79ac9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79ac9-118">See Also</span></span>  
 [<span data-ttu-id="79ac9-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="79ac9-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
