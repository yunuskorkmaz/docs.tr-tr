---
description: 'Hakkında daha fazla bilgi edinin: ıSNULL (Entity SQL)'
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 1dbaf964facf089ab6714ebd58baf8b040288cff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748498"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="63542-103">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="63542-103">ISNULL (Entity SQL)</span></span>

<span data-ttu-id="63542-104">Sorgu ifadesinin null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="63542-104">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63542-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="63542-105">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="63542-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="63542-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="63542-107">Herhangi bir geçerli sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="63542-107">Any valid query expression.</span></span> <span data-ttu-id="63542-108">Koleksiyon, koleksiyon üyeleri veya koleksiyon türü özellikleri olan bir kayıt türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="63542-108">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="63542-109">NOT</span><span class="sxs-lookup"><span data-stu-id="63542-109">NOT</span></span>  
 <span data-ttu-id="63542-110">EDM 'yi geçersiz kılar. Boolean sonucu NULL.</span><span class="sxs-lookup"><span data-stu-id="63542-110">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63542-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63542-111">Return Value</span></span>  

 <span data-ttu-id="63542-112">`true` Eğer `expression` null döndürürse, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="63542-112">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63542-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63542-113">Remarks</span></span>  

 <span data-ttu-id="63542-114">`IS NULL`Dış birleştirmenin öğesinin null olup olmadığını anlamak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="63542-114">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="63542-115">`IS NULL`Üyenin gerçek bir değere sahip olup olmadığını anlamak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="63542-115">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="63542-116">Aşağıdaki tabloda `IS NULL` bazı desenlerin üzerinde davranış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63542-116">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="63542-117">Sağlayıcı çağrılmadan önce istemci tarafında tüm özel durumlar atılır:</span><span class="sxs-lookup"><span data-stu-id="63542-117">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="63542-118">Desen</span><span class="sxs-lookup"><span data-stu-id="63542-118">Pattern</span></span>|<span data-ttu-id="63542-119">Davranış</span><span class="sxs-lookup"><span data-stu-id="63542-119">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="63542-120">NULL NULL</span><span class="sxs-lookup"><span data-stu-id="63542-120">null IS NULL</span></span>|<span data-ttu-id="63542-121">`true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="63542-121">Returns `true`.</span></span>|  
|<span data-ttu-id="63542-122">DAVRAN (EntityType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="63542-122">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="63542-123">`true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="63542-123">Returns `true`.</span></span>|  
|<span data-ttu-id="63542-124">DAVRAN (ComplexType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="63542-124">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="63542-125">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63542-125">Throws an error.</span></span>|  
|<span data-ttu-id="63542-126">DEĞERLENDIRIN (RowType olarak null) NULL</span><span class="sxs-lookup"><span data-stu-id="63542-126">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="63542-127">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63542-127">Throws an error.</span></span>|  
|<span data-ttu-id="63542-128">EntityType NULL</span><span class="sxs-lookup"><span data-stu-id="63542-128">EntityType IS NULL</span></span>|<span data-ttu-id="63542-129">`true`Veya döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="63542-129">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="63542-130">ComplexType NULL</span><span class="sxs-lookup"><span data-stu-id="63542-130">ComplexType IS NULL</span></span>|<span data-ttu-id="63542-131">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63542-131">Throws an error.</span></span>|  
|<span data-ttu-id="63542-132">RowType NULL</span><span class="sxs-lookup"><span data-stu-id="63542-132">RowType IS NULL</span></span>|<span data-ttu-id="63542-133">Bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="63542-133">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="63542-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="63542-134">Example</span></span>  

 <span data-ttu-id="63542-135">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, bir sorgu ifadesinin null olmadığını anlamak IÇIN null olmayan bir işleç kullanır.</span><span class="sxs-lookup"><span data-stu-id="63542-135">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="63542-136">Sorgu AdventureWorks Sales modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="63542-136">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="63542-137">Bu sorguyu derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="63542-137">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="63542-138">[Nasıl yapılır: StructuralType sonuçları döndüren bir sorgu yürütme](../how-to-execute-a-query-that-returns-structuraltype-results.md)bölümündeki yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="63542-138">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="63542-139">Aşağıdaki sorguyu yöntemine bir bağımsız değişken olarak geçirin `ExecuteStructuralTypeQuery` :</span><span class="sxs-lookup"><span data-stu-id="63542-139">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="63542-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63542-140">See also</span></span>

- [<span data-ttu-id="63542-141">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="63542-141">Entity SQL Reference</span></span>](entity-sql-reference.md)
