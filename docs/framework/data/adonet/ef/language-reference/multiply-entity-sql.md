---
title: "* (Çarp) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e2dca4be3d23d6cf9171eec960335ef57de1156c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="343b1-102">* ((Varlık SQL) çarpın)</span><span class="sxs-lookup"><span data-stu-id="343b1-102">* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="343b1-103">İki ifadeye çarpar.</span><span class="sxs-lookup"><span data-stu-id="343b1-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="343b1-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="343b1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="343b1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="343b1-106">Sayısal veri türleri herhangi birinin geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="343b1-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="343b1-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="343b1-107">Result Types</span></span>  
 <span data-ttu-id="343b1-108">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="343b1-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="343b1-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="343b1-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="343b1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="343b1-110">Example</span></span>  
 <span data-ttu-id="343b1-111">Aşağıdaki varlık SQL sorgusu kullanır * iki sayının çarpılacağı aritmetik işleç.</span><span class="sxs-lookup"><span data-stu-id="343b1-111">The following Entity SQL query uses the * arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="343b1-112">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="343b1-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="343b1-113">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="343b1-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="343b1-114">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="343b1-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="343b1-115">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="343b1-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="343b1-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="343b1-116">See Also</span></span>  
 [<span data-ttu-id="343b1-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="343b1-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
