---
description: 'Hakkında daha fazla bilgi edinin: * (çarpma) (Entity SQL)'
title: '* Bilirsiniz (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 92606e5f9e4646ab651d0e07095e6f419401188f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696626"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="2f68e-103">\* (Çarp) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2f68e-103">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="2f68e-104">İki ifadeyi çarpar.</span><span class="sxs-lookup"><span data-stu-id="2f68e-104">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f68e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2f68e-105">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f68e-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2f68e-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="2f68e-107">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="2f68e-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2f68e-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="2f68e-108">Result Types</span></span>  

 <span data-ttu-id="2f68e-109">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="2f68e-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="2f68e-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2f68e-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f68e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f68e-111">Example</span></span>  

 <span data-ttu-id="2f68e-112">Aşağıdaki Entity SQL sorgusu iki sayıyı çarpmak için \* aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f68e-112">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="2f68e-113">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="2f68e-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2f68e-114">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="2f68e-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2f68e-115">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="2f68e-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2f68e-116">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="2f68e-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="2f68e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f68e-117">See also</span></span>

- [<span data-ttu-id="2f68e-118">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2f68e-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
