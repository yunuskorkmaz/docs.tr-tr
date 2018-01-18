---
title: "! (YOK) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f3786724280cc077574f37e4d373c85faf5340f3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="-not-entity-sql"></a><span data-ttu-id="8090d-103">!</span><span class="sxs-lookup"><span data-stu-id="8090d-103">!</span></span> <span data-ttu-id="8090d-104">(YOK) (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="8090d-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="8090d-105">Üzerindeki geçersiz kılar bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="8090d-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8090d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8090d-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8090d-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="8090d-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="8090d-108">Tüm geçerli ifade bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8090d-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8090d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8090d-109">Remarks</span></span>  
 <span data-ttu-id="8090d-110">Ünlem işareti (!) NOT işleci aynı işlevselliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8090d-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8090d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8090d-111">Example</span></span>  
 <span data-ttu-id="8090d-112">Aşağıdaki varlık SQL sorgusunu üzerindeki geçersiz kılar için değil işlecini kullanan bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="8090d-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="8090d-113">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8090d-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8090d-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8090d-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8090d-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8090d-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8090d-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8090d-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="8090d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8090d-117">See Also</span></span>  
 [<span data-ttu-id="8090d-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8090d-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
