---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251110"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="8915d-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8915d-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="8915d-103">Bir EntitySet 'teki bir varlığa başvurular başvurusu yapar.</span><span class="sxs-lookup"><span data-stu-id="8915d-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8915d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8915d-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="8915d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8915d-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="8915d-106">Bir dize sabit değeri değil EntitySet tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8915d-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="8915d-107">Varlık türünün temel özelliklerine karşılık gelen satır türü bir ifade.</span><span class="sxs-lookup"><span data-stu-id="8915d-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8915d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8915d-108">Remarks</span></span>  
 <span data-ttu-id="8915d-109">`row_typed_expression`varlık için anahtar türüne yapısal olarak eşdeğer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8915d-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="8915d-110">Yani, varlık anahtarlarıyla aynı sırada aynı sayıda ve türde alanlara sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8915d-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="8915d-111">Aşağıdaki örnekte, Orders ve BadOrders öğelerinin her ikisi de sıralamayla ve kimliğin tek bir anahtar özelliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8915d-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="8915d-112">Örnek, Rozetteki bir varlığa nasıl başvuru üretebiliriz gösterir.</span><span class="sxs-lookup"><span data-stu-id="8915d-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="8915d-113">Başvurunun tehlike altında olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8915d-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="8915d-114">Diğer bir deyişle, başvuru gerçekten belirli bir varlığı tanımlamayabilir.</span><span class="sxs-lookup"><span data-stu-id="8915d-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="8915d-115">Bu durumlarda, bu başvuru `DEREF` üzerindeki bir işlem null değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8915d-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="8915d-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="8915d-116">Example</span></span>  
 <span data-ttu-id="8915d-117">Aşağıdaki Entity SQL sorgusu, bir varlık kümesindeki bir varlığa başvuruları almak için CREATEREF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8915d-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="8915d-118">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8915d-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8915d-119">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8915d-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8915d-120">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="8915d-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8915d-121">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="8915d-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="8915d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8915d-122">See also</span></span>

- [<span data-ttu-id="8915d-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8915d-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8915d-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="8915d-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="8915d-125">KEY</span><span class="sxs-lookup"><span data-stu-id="8915d-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="8915d-126">REF</span><span class="sxs-lookup"><span data-stu-id="8915d-126">REF</span></span>](ref-entity-sql.md)
