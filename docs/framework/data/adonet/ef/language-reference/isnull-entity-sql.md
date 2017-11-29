---
title: "IsNull (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31e0b77e397bd4f190119a01719da185211f7715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="45de1-102">IsNull (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="45de1-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="45de1-103">Bir sorgu ifadesi null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="45de1-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45de1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45de1-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="45de1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="45de1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="45de1-106">Herhangi bir geçerli sorgu ifade.</span><span class="sxs-lookup"><span data-stu-id="45de1-106">Any valid query expression.</span></span> <span data-ttu-id="45de1-107">Gönderilemiyor koleksiyonu, koleksiyon üyeleri veya bir kayıt türü ile toplama türü özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="45de1-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="45de1-108">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="45de1-108">NOT</span></span>  
 <span data-ttu-id="45de1-109">EDM üzerindeki geçersiz kılar. Boolean sonucu IS NULL.</span><span class="sxs-lookup"><span data-stu-id="45de1-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45de1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45de1-110">Return Value</span></span>  
 <span data-ttu-id="45de1-111">`true`varsa `expression` döndürür; tersi durumda, `false`.</span><span class="sxs-lookup"><span data-stu-id="45de1-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45de1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45de1-112">Remarks</span></span>  
 <span data-ttu-id="45de1-113">Kullanım `IS NULL` dış birleşim öğesi boş olup olmadığını belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="45de1-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="45de1-114">Kullanım `IS NULL` üyesi gerçek bir değer olup olmadığını belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="45de1-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="45de1-115">Aşağıdaki tabloda davranışını gösterilmektedir `IS NULL` bazı desenleri üzerinden.</span><span class="sxs-lookup"><span data-stu-id="45de1-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="45de1-116">Sağlayıcı çağrılır önce tüm istemci tarafındaki özel durumlar:</span><span class="sxs-lookup"><span data-stu-id="45de1-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="45de1-117">Desen</span><span class="sxs-lookup"><span data-stu-id="45de1-117">Pattern</span></span>|<span data-ttu-id="45de1-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="45de1-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="45de1-119">Is Null NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-119">null IS NULL</span></span>|<span data-ttu-id="45de1-120">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="45de1-120">Returns `true`.</span></span>|  
|<span data-ttu-id="45de1-121">KABUL (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="45de1-122">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="45de1-122">Returns `true`.</span></span>|  
|<span data-ttu-id="45de1-123">KABUL (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="45de1-124">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45de1-124">Throws an error.</span></span>|  
|<span data-ttu-id="45de1-125">KABUL (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="45de1-126">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45de1-126">Throws an error.</span></span>|  
|<span data-ttu-id="45de1-127">EntityType NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-127">EntityType IS NULL</span></span>|<span data-ttu-id="45de1-128">Döndürür `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="45de1-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="45de1-129">ComplexType NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-129">ComplexType IS NULL</span></span>|<span data-ttu-id="45de1-130">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45de1-130">Throws an error.</span></span>|  
|<span data-ttu-id="45de1-131">RowType NULL</span><span class="sxs-lookup"><span data-stu-id="45de1-131">RowType IS NULL</span></span>|<span data-ttu-id="45de1-132">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="45de1-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="45de1-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="45de1-133">Example</span></span>  
 <span data-ttu-id="45de1-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu IS NOT NULL işleci bir sorgu ifadesi null olup olmadığını belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="45de1-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="45de1-135">Sorgu AdventureWorks satış modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="45de1-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="45de1-136">Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="45de1-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="45de1-137">Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="45de1-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="45de1-138">Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="45de1-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="45de1-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45de1-139">See Also</span></span>  
 [<span data-ttu-id="45de1-140">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="45de1-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
