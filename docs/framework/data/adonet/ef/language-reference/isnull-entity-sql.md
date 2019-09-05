---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: d54c350196ad1ef7cfafa6d931d9d1ad8f267177
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250565"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="8b47d-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8b47d-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="8b47d-103">Sorgu ifadesinin null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8b47d-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b47d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b47d-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b47d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b47d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8b47d-106">Herhangi bir geçerli sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="8b47d-106">Any valid query expression.</span></span> <span data-ttu-id="8b47d-107">Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="8b47d-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="8b47d-108">DEĞİL</span><span class="sxs-lookup"><span data-stu-id="8b47d-108">NOT</span></span>  
 <span data-ttu-id="8b47d-109">EDM 'yi geçersiz kılar. Boolean sonucu NULL.</span><span class="sxs-lookup"><span data-stu-id="8b47d-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b47d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b47d-110">Return Value</span></span>  
 <span data-ttu-id="8b47d-111">`true`Eğer `expression` null döndürürse, `false`tersi durumda.</span><span class="sxs-lookup"><span data-stu-id="8b47d-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b47d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b47d-112">Remarks</span></span>  
 <span data-ttu-id="8b47d-113">Dış `IS NULL` birleştirmenin öğesinin null olup olmadığını anlamak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b47d-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="8b47d-114">Üyenin `IS NULL` gerçek bir değere sahip olup olmadığını anlamak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="8b47d-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="8b47d-115">Aşağıdaki tabloda bazı desenlerin `IS NULL` üzerinde davranış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b47d-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="8b47d-116">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="8b47d-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="8b47d-117">Desen</span><span class="sxs-lookup"><span data-stu-id="8b47d-117">Pattern</span></span>|<span data-ttu-id="8b47d-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="8b47d-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="8b47d-119">NULL NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-119">null IS NULL</span></span>|<span data-ttu-id="8b47d-120">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="8b47d-120">Returns `true`.</span></span>|  
|<span data-ttu-id="8b47d-121">DAVRAN (EntityType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="8b47d-122">Döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="8b47d-122">Returns `true`.</span></span>|  
|<span data-ttu-id="8b47d-123">DAVRAN (ComplexType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="8b47d-124">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b47d-124">Throws an error.</span></span>|  
|<span data-ttu-id="8b47d-125">DEĞERLENDIRIN (RowType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="8b47d-126">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b47d-126">Throws an error.</span></span>|  
|<span data-ttu-id="8b47d-127">EntityType NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-127">EntityType IS NULL</span></span>|<span data-ttu-id="8b47d-128">`true` Veya`false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b47d-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="8b47d-129">ComplexType NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-129">ComplexType IS NULL</span></span>|<span data-ttu-id="8b47d-130">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b47d-130">Throws an error.</span></span>|  
|<span data-ttu-id="8b47d-131">RowType NULL</span><span class="sxs-lookup"><span data-stu-id="8b47d-131">RowType IS NULL</span></span>|<span data-ttu-id="8b47d-132">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b47d-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8b47d-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b47d-133">Example</span></span>  
 <span data-ttu-id="8b47d-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin null olmadığını anlamak için null olmayan bir işleç kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b47d-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="8b47d-135">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="8b47d-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8b47d-136">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="8b47d-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="8b47d-137">[Aşağıdaki adımları uygulayın: StructuralType sonuçları](../how-to-execute-a-query-that-returns-structuraltype-results.md)döndüren bir sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="8b47d-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="8b47d-138">Aşağıdaki sorguyu `ExecuteStructuralTypeQuery` yöntemine bir bağımsız değişken olarak geçirin:</span><span class="sxs-lookup"><span data-stu-id="8b47d-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="8b47d-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b47d-139">See also</span></span>

- [<span data-ttu-id="8b47d-140">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b47d-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
