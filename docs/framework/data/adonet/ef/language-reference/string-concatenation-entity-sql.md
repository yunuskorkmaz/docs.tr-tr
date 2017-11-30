---
title: "+ (Dize birleştirme) (Varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 60661a592e23e230c32b1fd7093f5dfd8e6ed87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="d684d-102">+ (Dize birleştirmesi) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="d684d-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="d684d-103">İki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="d684d-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d684d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d684d-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d684d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d684d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d684d-106">EDM geçerli bir ifade. Veri türleri dize.</span><span class="sxs-lookup"><span data-stu-id="d684d-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="d684d-107">Her iki ifadeler aynı veri türünde olmalıdır veya bir ifade diğer ifade veri türüne örtük olarak dönüştürülmesi mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d684d-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d684d-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="d684d-108">Result Types</span></span>  
 <span data-ttu-id="d684d-109">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="d684d-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d684d-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d684d-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d684d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d684d-111">Example</span></span>  
 <span data-ttu-id="d684d-112">Aşağıdaki varlık SQL sorgusu kullanır + işleci, iki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="d684d-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="d684d-113">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="d684d-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d684d-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="d684d-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d684d-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d684d-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="d684d-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d684d-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="d684d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d684d-117">See Also</span></span>  
 [<span data-ttu-id="d684d-118">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="d684d-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d684d-119">Kavramsal Model türü (CSDL)</span><span class="sxs-lookup"><span data-stu-id="d684d-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)
