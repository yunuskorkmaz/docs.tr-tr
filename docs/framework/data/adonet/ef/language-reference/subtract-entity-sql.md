---
description: Hakkında daha fazla bilgi edinin:-(Çıkart) (Entity SQL)
title: '- Çıkarma (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: cba23d998ad6beaf545118c69d806de46a1f6db0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791835"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="9a639-103">-(Çıkart) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a639-103">- (Subtract) (Entity SQL)</span></span>

<span data-ttu-id="9a639-104">İki sayıyı çıkartır.</span><span class="sxs-lookup"><span data-stu-id="9a639-104">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a639-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9a639-105">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a639-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="9a639-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="9a639-107">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="9a639-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9a639-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="9a639-108">Result Types</span></span>  

 <span data-ttu-id="9a639-109">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="9a639-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9a639-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9a639-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a639-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a639-111">Example</span></span>  

 <span data-ttu-id="9a639-112">Aşağıdaki Entity SQL sorgusu iki sayıyı çıkarmak için-aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a639-112">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="9a639-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="9a639-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9a639-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="9a639-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9a639-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="9a639-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9a639-116">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="9a639-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="9a639-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a639-117">See also</span></span>

- [<span data-ttu-id="9a639-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9a639-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
