---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c2a57116f56abf4db3caabcfe3acd0d8afbcf4eb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201063"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="bfb08-102">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bfb08-102">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="bfb08-103">Bir EntitySet 'teki bir varlığa başvurular başvurusu yapar.</span><span class="sxs-lookup"><span data-stu-id="bfb08-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb08-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bfb08-104">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="bfb08-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="bfb08-105">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="bfb08-106">Bir dize sabit değeri değil EntitySet tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="bfb08-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="bfb08-107">Varlık türünün temel özelliklerine karşılık gelen satır türü bir ifade.</span><span class="sxs-lookup"><span data-stu-id="bfb08-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfb08-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bfb08-108">Remarks</span></span>  

 <span data-ttu-id="bfb08-109">`row_typed_expression` varlık için anahtar türüne yapısal olarak eşdeğer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bfb08-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="bfb08-110">Yani, varlık anahtarlarıyla aynı sırada aynı sayıda ve türde alanlara sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfb08-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="bfb08-111">Aşağıdaki örnekte, Orders ve BadOrders öğelerinin her ikisi de sıralamayla ve kimliğin tek bir anahtar özelliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="bfb08-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="bfb08-112">Örnek, Rozetteki bir varlığa nasıl başvuru üretebiliriz gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfb08-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="bfb08-113">Başvurunun tehlike altında olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bfb08-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="bfb08-114">Diğer bir deyişle, başvuru gerçekten belirli bir varlığı tanımlamayabilir.</span><span class="sxs-lookup"><span data-stu-id="bfb08-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="bfb08-115">Bu durumlarda, `DEREF` Bu başvuru üzerindeki bir işlem null değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bfb08-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="bfb08-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="bfb08-116">Example</span></span>  

 <span data-ttu-id="bfb08-117">Aşağıdaki Entity SQL sorgusu, bir varlık kümesindeki bir varlığa başvuruları almak için CREATEREF işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="bfb08-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="bfb08-118">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="bfb08-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bfb08-119">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="bfb08-119">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bfb08-120">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="bfb08-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bfb08-121">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="bfb08-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="bfb08-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfb08-122">See also</span></span>

- [<span data-ttu-id="bfb08-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bfb08-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="bfb08-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="bfb08-124">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="bfb08-125">ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="bfb08-125">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="bfb08-126">REF</span><span class="sxs-lookup"><span data-stu-id="bfb08-126">REF</span></span>](ref-entity-sql.md)
