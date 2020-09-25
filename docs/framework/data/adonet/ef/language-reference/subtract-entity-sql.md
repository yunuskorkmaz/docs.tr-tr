---
title: '- Çıkarma (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181043"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="74858-102">-(Çıkart) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="74858-102">- (Subtract) (Entity SQL)</span></span>

<span data-ttu-id="74858-103">İki sayıyı çıkartır.</span><span class="sxs-lookup"><span data-stu-id="74858-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74858-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="74858-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="74858-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="74858-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="74858-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="74858-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="74858-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="74858-107">Result Types</span></span>  

 <span data-ttu-id="74858-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="74858-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="74858-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="74858-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74858-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="74858-110">Example</span></span>  

 <span data-ttu-id="74858-111">Aşağıdaki Entity SQL sorgusu iki sayıyı çıkarmak için-aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="74858-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="74858-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="74858-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="74858-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="74858-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="74858-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="74858-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="74858-115">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="74858-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="74858-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74858-116">See also</span></span>

- [<span data-ttu-id="74858-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="74858-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
