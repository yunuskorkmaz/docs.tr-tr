---
title: '- Çıkarma (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: fe9152100bddac86f3fb7fae1ab3c0b81ae58418
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319323"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="badbf-102">-(Çıkart) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="badbf-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="badbf-103">İki sayıyı çıkartır.</span><span class="sxs-lookup"><span data-stu-id="badbf-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="badbf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="badbf-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="badbf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="badbf-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="badbf-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="badbf-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="badbf-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="badbf-107">Result Types</span></span>  
 <span data-ttu-id="badbf-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="badbf-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="badbf-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="badbf-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="badbf-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="badbf-110">Example</span></span>  
 <span data-ttu-id="badbf-111">Aşağıdaki Entity SQL sorgusu iki sayıyı çıkarmak için-aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="badbf-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="badbf-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="badbf-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="badbf-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="badbf-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="badbf-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="badbf-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="badbf-115">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="badbf-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="badbf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="badbf-116">See also</span></span>

- [<span data-ttu-id="badbf-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="badbf-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
