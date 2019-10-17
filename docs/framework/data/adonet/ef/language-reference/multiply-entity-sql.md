---
title: '* Bilirsiniz (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 7006f5143e8cc18156f748ae7664f3787c9ff5c9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319608"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="36776-102">\* (Çarp) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="36776-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="36776-103">İki ifadeyi çarpar.</span><span class="sxs-lookup"><span data-stu-id="36776-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36776-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36776-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="36776-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="36776-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="36776-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="36776-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="36776-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="36776-107">Result Types</span></span>  
 <span data-ttu-id="36776-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="36776-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="36776-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="36776-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36776-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="36776-110">Example</span></span>  
 <span data-ttu-id="36776-111">Aşağıdaki Entity SQL sorgusu iki sayıyı çarpmak için \* aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36776-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="36776-112">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="36776-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="36776-113">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="36776-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="36776-114">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="36776-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="36776-115">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="36776-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="36776-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36776-116">See also</span></span>

- [<span data-ttu-id="36776-117">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="36776-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
