---
description: 'Hakkında daha fazla bilgi edinin: + (Ekle)'
title: + (Ekle)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b8ec9f50b349fe971513f399b7e9984e9044cf58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697315"
---
# <a name="-add"></a><span data-ttu-id="08a55-103">+ (Ekle)</span><span class="sxs-lookup"><span data-stu-id="08a55-103">+ (Add)</span></span>

<span data-ttu-id="08a55-104">İki sayı ekler.</span><span class="sxs-lookup"><span data-stu-id="08a55-104">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a55-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="08a55-105">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="08a55-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="08a55-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="08a55-107">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="08a55-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="08a55-108">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="08a55-108">Result Types</span></span>  

 <span data-ttu-id="08a55-109">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="08a55-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="08a55-110">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="08a55-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08a55-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08a55-111">Remarks</span></span>  

 <span data-ttu-id="08a55-112">EDM için. Dize türleri, ekleme birleştirme.</span><span class="sxs-lookup"><span data-stu-id="08a55-112">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08a55-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="08a55-113">Example</span></span>  

 <span data-ttu-id="08a55-114">Aşağıdaki Entity SQL sorgusu iki sayı eklemek için + aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="08a55-114">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="08a55-115">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="08a55-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="08a55-116">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="08a55-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="08a55-117">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="08a55-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="08a55-118">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="08a55-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="08a55-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08a55-119">See also</span></span>

- [<span data-ttu-id="08a55-120">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="08a55-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="08a55-121">Kavramsal model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="08a55-121">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
