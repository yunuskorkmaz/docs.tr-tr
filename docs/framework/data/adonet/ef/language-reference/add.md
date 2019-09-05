---
title: + (Ekle)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 8c9a6b2c8168e4677c37cfdb0b401a93ee0040cf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251364"
---
# <a name="-add"></a><span data-ttu-id="5bd79-102">+ (Ekle)</span><span class="sxs-lookup"><span data-stu-id="5bd79-102">+ (Add)</span></span>
<span data-ttu-id="5bd79-103">İki sayı ekler.</span><span class="sxs-lookup"><span data-stu-id="5bd79-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bd79-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5bd79-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5bd79-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5bd79-106">Sayısal veri türlerinden herhangi birinin geçerli bir ifadesi.</span><span class="sxs-lookup"><span data-stu-id="5bd79-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5bd79-107">Sonuç türleri</span><span class="sxs-lookup"><span data-stu-id="5bd79-107">Result Types</span></span>  
 <span data-ttu-id="5bd79-108">İki bağımsız değişkenin örtük tür promosyonu sonucunda elde edilen veri türü.</span><span class="sxs-lookup"><span data-stu-id="5bd79-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="5bd79-109">Örtük tür yükseltme hakkında daha fazla bilgi için bkz. [System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5bd79-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bd79-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bd79-110">Remarks</span></span>  
 <span data-ttu-id="5bd79-111">EDM için. Dize türleri, ekleme birleştirme.</span><span class="sxs-lookup"><span data-stu-id="5bd79-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bd79-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5bd79-112">Example</span></span>  
 <span data-ttu-id="5bd79-113">Aşağıdaki Entity SQL sorgusu iki sayı eklemek için + aritmetik işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5bd79-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="5bd79-114">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="5bd79-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5bd79-115">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="5bd79-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5bd79-116">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="5bd79-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5bd79-117">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="5bd79-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="5bd79-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bd79-118">See also</span></span>

- [<span data-ttu-id="5bd79-119">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5bd79-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5bd79-120">Kavramsal model türleri (CSDL)</span><span class="sxs-lookup"><span data-stu-id="5bd79-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
