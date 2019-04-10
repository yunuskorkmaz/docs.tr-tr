---
title: '- (Bölme) (Varlık SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: c3b477a63adf3c3d51f28449e94c2b716422296c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330863"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="8008d-102">/ (Bölme (varlık SQL))</span><span class="sxs-lookup"><span data-stu-id="8008d-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="8008d-103">Bir sayıyı bir başkası tarafından böler.</span><span class="sxs-lookup"><span data-stu-id="8008d-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8008d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8008d-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="8008d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8008d-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="8008d-106">Bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="8008d-106">The numeric expression to divide.</span></span> `dividend` <span data-ttu-id="8008d-107">sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="8008d-107">is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="8008d-108">Bölünenin bölüneceği sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="8008d-108">The numeric expression to divide the dividend by.</span></span> `divisor` <span data-ttu-id="8008d-109">sayısal veri türleri herhangi birinin herhangi bir geçerli ifade var.</span><span class="sxs-lookup"><span data-stu-id="8008d-109">is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8008d-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="8008d-110">Result Types</span></span>  
 <span data-ttu-id="8008d-111">Bu iki bağımsız değişken örtük tür yükseltme sonuçlarından veri türü.</span><span class="sxs-lookup"><span data-stu-id="8008d-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="8008d-112">Örtük tür yükseltme hakkında daha fazla bilgi için bkz: [tür sistemi](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="8008d-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8008d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8008d-113">Example</span></span>  
 <span data-ttu-id="8008d-114">Aşağıdaki varlık SQL sorgusu kullanır / aritmetik bir başkası tarafından bölme işleci.</span><span class="sxs-lookup"><span data-stu-id="8008d-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="8008d-115">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="8008d-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8008d-116">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8008d-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8008d-117">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8008d-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8008d-118">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8008d-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="8008d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8008d-119">See also</span></span>

- [<span data-ttu-id="8008d-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8008d-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
