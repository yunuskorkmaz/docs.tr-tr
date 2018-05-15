---
title: '- (Bölme) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 506553de78ce9fbdf5f3710805906ee8cd5b8757
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="55ad7-102">/ (Bölme (varlık SQL))</span><span class="sxs-lookup"><span data-stu-id="55ad7-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="55ad7-103">Bir sayıyı bir başkası tarafından böler.</span><span class="sxs-lookup"><span data-stu-id="55ad7-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55ad7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55ad7-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="55ad7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="55ad7-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="55ad7-106">Bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="55ad7-106">The numeric expression to divide.</span></span> <span data-ttu-id="55ad7-107">`dividend` sayısal veri türleri herhangi birinin geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="55ad7-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="55ad7-108">Tarafından bölünen bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="55ad7-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="55ad7-109">`divisor` sayısal veri türleri herhangi birinin geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="55ad7-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="55ad7-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="55ad7-110">Result Types</span></span>  
 <span data-ttu-id="55ad7-111">İki bağımsız değişken örtük tür yükseltme sonuçları veri türü.</span><span class="sxs-lookup"><span data-stu-id="55ad7-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="55ad7-112">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="55ad7-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55ad7-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="55ad7-113">Example</span></span>  
 <span data-ttu-id="55ad7-114">Aşağıdaki varlık SQL sorgusu kullanır / aritmetik bir numarası bir başkası tarafından bölmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="55ad7-114">The following Entity SQL query uses the / arithmetic operator to divide one numer by another.</span></span> <span data-ttu-id="55ad7-115">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="55ad7-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="55ad7-116">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="55ad7-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="55ad7-117">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="55ad7-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="55ad7-118">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="55ad7-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="55ad7-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55ad7-119">See Also</span></span>  
 [<span data-ttu-id="55ad7-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="55ad7-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
