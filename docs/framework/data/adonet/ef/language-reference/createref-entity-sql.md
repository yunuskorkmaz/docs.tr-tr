---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: 3659f2c0690b00e728630c6e77308ba9d424bb1b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833932"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="6edc5-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6edc5-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="6edc5-103">Bir EntitySet 'teki bir varlığa başvurular başvurusu yapar.</span><span class="sxs-lookup"><span data-stu-id="6edc5-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6edc5-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="6edc5-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="6edc5-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="6edc5-106">Bir dize sabit değeri değil EntitySet tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6edc5-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="6edc5-107">Varlık türünün temel özelliklerine karşılık gelen satır türü bir ifade.</span><span class="sxs-lookup"><span data-stu-id="6edc5-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6edc5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6edc5-108">Remarks</span></span>  
 <span data-ttu-id="6edc5-109">`row_typed_expression` ' ın varlık için anahtar türüne yapısal olarak eşit olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6edc5-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="6edc5-110">Yani, varlık anahtarlarıyla aynı sırada aynı sayıda ve türde alanlara sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6edc5-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="6edc5-111">Aşağıdaki örnekte, Orders ve BadOrders öğelerinin her ikisi de sıralamayla ve kimliğin tek bir anahtar özelliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6edc5-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="6edc5-112">Örnek, Rozetteki bir varlığa nasıl başvuru üretebiliriz gösterir.</span><span class="sxs-lookup"><span data-stu-id="6edc5-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="6edc5-113">Başvurunun tehlike altında olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6edc5-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="6edc5-114">Diğer bir deyişle, başvuru gerçekten belirli bir varlığı tanımlamayabilir.</span><span class="sxs-lookup"><span data-stu-id="6edc5-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="6edc5-115">Bu durumlarda, bu başvuru üzerindeki `DEREF` işlemi null döndürür.</span><span class="sxs-lookup"><span data-stu-id="6edc5-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="6edc5-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6edc5-116">Example</span></span>  
 <span data-ttu-id="6edc5-117">Aşağıdaki Entity SQL sorgusu, bir varlık kümesindeki bir varlığa başvuruları almak için CREATEREF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6edc5-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="6edc5-118">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="6edc5-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6edc5-119">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="6edc5-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6edc5-120">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="6edc5-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6edc5-121">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="6edc5-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="6edc5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6edc5-122">See also</span></span>

- [<span data-ttu-id="6edc5-123">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="6edc5-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6edc5-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="6edc5-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="6edc5-125">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="6edc5-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="6edc5-126">REF</span><span class="sxs-lookup"><span data-stu-id="6edc5-126">REF</span></span>](ref-entity-sql.md)
