---
title: CREATEREF (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 6ae4712fb280418ad8cf17cd68a7bbcd9cf3b8a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785287"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="277d8-102">CREATEREF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="277d8-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="277d8-103">Bir entityset varlık başvuruları fabricates.</span><span class="sxs-lookup"><span data-stu-id="277d8-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="277d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="277d8-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="277d8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="277d8-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="277d8-106">Entityset tanımlayıcısı olmayan bir dize sabit değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="277d8-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="277d8-107">Varlık türünün temel özelliklerine karşılık gelen bir satır yazılmış bir ifade.</span><span class="sxs-lookup"><span data-stu-id="277d8-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="277d8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="277d8-108">Remarks</span></span>  
 <span data-ttu-id="277d8-109">`row_typed_expression` varlık için anahtar türü yapısal olarak eşdeğer olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="277d8-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="277d8-110">Diğer bir deyişle, aynı sayısını ve türlerini alanların varlık anahtarları aynı sırada olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="277d8-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="277d8-111">Aşağıdaki örnekte, siparişler ve BadOrders sipariş türünde iki entityset'i olan ve kimliği siparişinin tek anahtar özellik olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="277d8-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="277d8-112">Örnek bir varlıkta BadOrders başvuru hazırladığımız nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="277d8-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="277d8-113">Başvuru sarkan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="277d8-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="277d8-114">Diğer bir deyişle, başvuru, belirli bir varlığa gerçekten tanımlayamayabilir.</span><span class="sxs-lookup"><span data-stu-id="277d8-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="277d8-115">Bu durumlarda, bir `DEREF` bu başvuru üzerinde işlem, bir null döndürür.</span><span class="sxs-lookup"><span data-stu-id="277d8-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="277d8-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="277d8-116">Example</span></span>  
 <span data-ttu-id="277d8-117">Aşağıdaki varlık SQL sorgusu CREATEREF işlecindeki bir varlık kümesinin varlık başvuruları imal için kullanır.</span><span class="sxs-lookup"><span data-stu-id="277d8-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="277d8-118">Sorgu, AdventureWorks satış modelini temel alıyor.</span><span class="sxs-lookup"><span data-stu-id="277d8-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="277d8-119">Derleme ve bu sorguyu çalıştırmak için bu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="277d8-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="277d8-120">Verilen yordamı izleyin [nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="277d8-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="277d8-121">Aşağıdaki sorguda bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="277d8-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="277d8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="277d8-122">See also</span></span>

- [<span data-ttu-id="277d8-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="277d8-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="277d8-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="277d8-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
- [<span data-ttu-id="277d8-125">KEY</span><span class="sxs-lookup"><span data-stu-id="277d8-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="277d8-126">REF</span><span class="sxs-lookup"><span data-stu-id="277d8-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
