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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6019f6025b3a3996c9b86a6c9e61a3dd345c1b12
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="38d3f-102">+ (Dize birleştirmesi) (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="38d3f-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="38d3f-103">İki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="38d3f-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38d3f-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="38d3f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="38d3f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="38d3f-106">EDM geçerli bir ifade. Veri türleri dize.</span><span class="sxs-lookup"><span data-stu-id="38d3f-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="38d3f-107">Her iki ifadeler aynı veri türünde olmalıdır veya bir ifade diğer ifade veri türüne örtük olarak dönüştürülmesi mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="38d3f-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="38d3f-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="38d3f-108">Result Types</span></span>  
 <span data-ttu-id="38d3f-109">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="38d3f-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="38d3f-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="38d3f-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38d3f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="38d3f-111">Example</span></span>  
 <span data-ttu-id="38d3f-112">Aşağıdaki varlık SQL sorgusu kullanır + işleci, iki dizeyi art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="38d3f-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="38d3f-113">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="38d3f-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="38d3f-114">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="38d3f-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="38d3f-115">Yordamı izleyin [nasıl yapılır: Sorgu döndürür PrimitiveType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="38d3f-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="38d3f-116">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecutePrimitiveTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="38d3f-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="38d3f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38d3f-117">See Also</span></span>  
 [<span data-ttu-id="38d3f-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="38d3f-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="38d3f-119">Kavramsal Model türü (CSDL)</span><span class="sxs-lookup"><span data-stu-id="38d3f-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)
