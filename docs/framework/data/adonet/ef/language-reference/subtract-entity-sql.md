---
title: "- (Çıkart) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 07921151309486617312a76285eea7be54463d4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="40509-102">-(Çıkart) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="40509-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="40509-103">İki sayı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="40509-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40509-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40509-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="40509-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="40509-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="40509-106">Sayısal veri türleri herhangi birinin geçerli bir ifade.</span><span class="sxs-lookup"><span data-stu-id="40509-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="40509-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="40509-107">Result Types</span></span>  
 <span data-ttu-id="40509-108">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="40509-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="40509-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="40509-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40509-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="40509-110">Example</span></span>  
 <span data-ttu-id="40509-111">Aşağıdaki varlık SQL sorgusunu kullanan iki sayının çıkartılacak aritmetik işleç.</span><span class="sxs-lookup"><span data-stu-id="40509-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="40509-112">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="40509-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="40509-113">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="40509-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="40509-114">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="40509-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="40509-115">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="40509-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="40509-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40509-116">See Also</span></span>  
 [<span data-ttu-id="40509-117">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="40509-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
