---
title: '* Bilirsiniz (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 19fb73d327f91303de938a5f49866339413b9698
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250055"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="78052-102">\* (Çarp) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="78052-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="78052-103">İki ifadeyi çarpar.</span><span class="sxs-lookup"><span data-stu-id="78052-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78052-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78052-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="78052-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="78052-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="78052-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="78052-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="78052-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="78052-107">Result Types</span></span>  
 <span data-ttu-id="78052-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="78052-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="78052-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="78052-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78052-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="78052-110">Example</span></span>  
 <span data-ttu-id="78052-111">Aşağıdaki Entity SQL sorgusu iki sayıyı çarpmak için \* aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="78052-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="78052-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="78052-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="78052-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="78052-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="78052-114">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="78052-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="78052-115">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="78052-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="78052-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78052-116">See also</span></span>

- [<span data-ttu-id="78052-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="78052-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
