---
description: Daha fazla bilgi edinin:/(Böl) (Entity SQL)
title: '- Sayısına (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 4ac487c636c460401eeb147dc7ce1a8d8ba7f7ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724641"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="fd689-103">/(Böl) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fd689-103">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="fd689-104">Bir sayıyı başka bir sayıya böler.</span><span class="sxs-lookup"><span data-stu-id="fd689-104">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd689-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd689-105">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd689-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="fd689-106">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="fd689-107">Bölünecek sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="fd689-107">The numeric expression to divide.</span></span> <span data-ttu-id="fd689-108">`dividend` , herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="fd689-108">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="fd689-109">Bölüneni bölmek için sayısal ifade.</span><span class="sxs-lookup"><span data-stu-id="fd689-109">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="fd689-110">`divisor` , herhangi bir sayısal veri türü için geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="fd689-110">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fd689-111">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="fd689-111">Result Types</span></span>  

 <span data-ttu-id="fd689-112">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="fd689-112">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fd689-113">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fd689-113">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd689-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd689-114">Example</span></span>  

 <span data-ttu-id="fd689-115">Aşağıdaki Entity SQL sorgusu, bir sayıyı başka bir sayıya bölmek için/aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd689-115">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="fd689-116">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="fd689-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fd689-117">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fd689-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fd689-118">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="fd689-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fd689-119">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="fd689-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="fd689-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd689-120">See also</span></span>

- [<span data-ttu-id="fd689-121">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fd689-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
