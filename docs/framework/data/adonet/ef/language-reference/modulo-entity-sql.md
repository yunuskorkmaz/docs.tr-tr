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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e204612904aa55b4a0ae9aa65f2bbfd644bbc396
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="28079-102">(Modül) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="28079-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="28079-103">Bir başkası tarafından ayrılmış bir ifade kalanı döndürür.</span><span class="sxs-lookup"><span data-stu-id="28079-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28079-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28079-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="28079-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="28079-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="28079-106">Bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="28079-106">The numeric expression to divide.</span></span> <span data-ttu-id="28079-107">`dividend`sayısal veri türleri herhangi birinin geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="28079-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="28079-108">Tarafından bölünen bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="28079-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="28079-109">`divisor`sayısal veri türleri herhangi birinin geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="28079-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="28079-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="28079-110">Result Types</span></span>  
 <span data-ttu-id="28079-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="28079-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="28079-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="28079-112">Example</span></span>  
 <span data-ttu-id="28079-113">Aşağıdaki varlık SQL sorgusunu % aritmetik işleç başkası tarafından ayrılmış bir ifade kalanı döndürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="28079-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="28079-114">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="28079-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="28079-115">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="28079-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="28079-116">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="28079-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="28079-117">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="28079-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="28079-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28079-118">See Also</span></span>  
 [<span data-ttu-id="28079-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="28079-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
