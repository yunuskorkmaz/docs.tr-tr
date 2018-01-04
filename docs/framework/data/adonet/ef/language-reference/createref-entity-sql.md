---
title: "CREATEREF (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ad5329e50a5bea933e8fdfdfd473b2d4b9e0b211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="createref-entity-sql"></a><span data-ttu-id="fad05-102">CREATEREF (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="fad05-102">CREATEREF (Entity SQL)</span></span>
<span data-ttu-id="fad05-103">Bir entityset varlık başvuruları fabricates.</span><span class="sxs-lookup"><span data-stu-id="fad05-103">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fad05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fad05-104">Syntax</span></span>  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="fad05-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fad05-105">Arguments</span></span>  
 `entityset_identifier`  
 <span data-ttu-id="fad05-106">Entityset tanımlayıcısı, olmayan bir değişmez dize değeri.</span><span class="sxs-lookup"><span data-stu-id="fad05-106">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="fad05-107">Varlık türünün temel özelliklerine karşılık gelen bir satır yazılan bir ifade.</span><span class="sxs-lookup"><span data-stu-id="fad05-107">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fad05-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fad05-108">Remarks</span></span>  
 <span data-ttu-id="fad05-109">`row_typed_expression`varlık için anahtar türü yapısal olarak eşdeğer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fad05-109">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="fad05-110">Diğer bir deyişle, aynı sayısı ve türleri alanları varlık anahtarları aynı sırada olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fad05-110">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="fad05-111">Aşağıdaki örnekte, siparişler ve BadOrders her iki entityset'i sipariş türünde olan ve kimliği sipariş tek anahtar özelliği olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fad05-111">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="fad05-112">Örnek nasıl biz BadOrders içinde bir varlığa bir başvuru üretebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="fad05-112">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="fad05-113">Başvuru sarkan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fad05-113">Note that the reference may be dangling.</span></span>  <span data-ttu-id="fad05-114">Diğer bir deyişle, başvuru gerçekte belirli bir varlık tanımlayabilir değil.</span><span class="sxs-lookup"><span data-stu-id="fad05-114">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="fad05-115">Bu durumlarda, bir `DEREF` bu başvuruyu işlemi null döndürür.</span><span class="sxs-lookup"><span data-stu-id="fad05-115">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a><span data-ttu-id="fad05-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="fad05-116">Example</span></span>  
 <span data-ttu-id="fad05-117">Aşağıdaki varlık SQL sorgusunu CREATEREF işlecindeki bir varlık kümesinin varlık başvuruları imal için kullanır.</span><span class="sxs-lookup"><span data-stu-id="fad05-117">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="fad05-118">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="fad05-118">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fad05-119">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="fad05-119">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fad05-120">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fad05-120">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fad05-121">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="fad05-121">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="fad05-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fad05-122">See Also</span></span>  
 [<span data-ttu-id="fad05-123">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fad05-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="fad05-124">DEREF</span><span class="sxs-lookup"><span data-stu-id="fad05-124">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [<span data-ttu-id="fad05-125">KEY</span><span class="sxs-lookup"><span data-stu-id="fad05-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="fad05-126">REF</span><span class="sxs-lookup"><span data-stu-id="fad05-126">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
