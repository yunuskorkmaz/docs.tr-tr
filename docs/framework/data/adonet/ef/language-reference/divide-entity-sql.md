---
title: '- Sayısına (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 79fdbebc648daac4f695387d52d2a915383f99ca
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833883"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="58487-102">/(Böl) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="58487-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="58487-103">Bir sayıyı başka bir sayıya böler.</span><span class="sxs-lookup"><span data-stu-id="58487-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58487-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58487-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="58487-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="58487-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="58487-106">Bölünecek sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="58487-106">The numeric expression to divide.</span></span> <span data-ttu-id="58487-107">`dividend`, herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="58487-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="58487-108">Bölüneni bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="58487-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="58487-109">`divisor`, herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="58487-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="58487-110">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="58487-110">Result Types</span></span>  
 <span data-ttu-id="58487-111">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="58487-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="58487-112">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="58487-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58487-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="58487-113">Example</span></span>  
 <span data-ttu-id="58487-114">Aşağıdaki Entity SQL sorgusu, bir sayıyı başka bir sayıya bölmek için/aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="58487-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="58487-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="58487-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="58487-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="58487-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="58487-117">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="58487-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="58487-118">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="58487-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="58487-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58487-119">See also</span></span>

- [<span data-ttu-id="58487-120">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="58487-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
