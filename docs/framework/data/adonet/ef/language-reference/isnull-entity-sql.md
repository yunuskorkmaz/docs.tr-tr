---
title: ISNULL (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150206"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="1712a-102">ISNULL (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="1712a-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="1712a-103">Sorgu ifadesinin null olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="1712a-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1712a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1712a-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="1712a-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="1712a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1712a-106">Geçerli bir sorgu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="1712a-106">Any valid query expression.</span></span> <span data-ttu-id="1712a-107">Koleksiyon olamaz, koleksiyon üyeleri veya koleksiyon türü özelliklerine sahip bir kayıt türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="1712a-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="1712a-108">NOT</span><span class="sxs-lookup"><span data-stu-id="1712a-108">NOT</span></span>  
 <span data-ttu-id="1712a-109">EDM'i etkisiz erdirdi. IS NULL boolean sonucu.</span><span class="sxs-lookup"><span data-stu-id="1712a-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1712a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1712a-110">Return Value</span></span>  
 <span data-ttu-id="1712a-111">`true`null `expression` dönerse; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="1712a-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1712a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1712a-112">Remarks</span></span>  
 <span data-ttu-id="1712a-113">Dış `IS NULL` birleştirme öğesinin null olup olmadığını belirlemek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="1712a-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="1712a-114">Bir `IS NULL` üyenin gerçek bir değeri olup olmadığını belirlemek için kullanın:</span><span class="sxs-lookup"><span data-stu-id="1712a-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="1712a-115">Aşağıdaki tablo, bazı `IS NULL` desenler üzerinde davranışgösterir.</span><span class="sxs-lookup"><span data-stu-id="1712a-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="1712a-116">Sağlayıcı çağrılmadan önce tüm özel durumlar istemci tarafından atılır:</span><span class="sxs-lookup"><span data-stu-id="1712a-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="1712a-117">Desen</span><span class="sxs-lookup"><span data-stu-id="1712a-117">Pattern</span></span>|<span data-ttu-id="1712a-118">Davranış</span><span class="sxs-lookup"><span data-stu-id="1712a-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="1712a-119">null NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-119">null IS NULL</span></span>|<span data-ttu-id="1712a-120">`true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1712a-120">Returns `true`.</span></span>|  
|<span data-ttu-id="1712a-121">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="1712a-122">`true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1712a-122">Returns `true`.</span></span>|  
|<span data-ttu-id="1712a-123">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="1712a-124">Bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="1712a-124">Throws an error.</span></span>|  
|<span data-ttu-id="1712a-125">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="1712a-126">Bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="1712a-126">Throws an error.</span></span>|  
|<span data-ttu-id="1712a-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-127">EntityType IS NULL</span></span>|<span data-ttu-id="1712a-128">İade `true` `false`veya .</span><span class="sxs-lookup"><span data-stu-id="1712a-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="1712a-129">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-129">ComplexType IS NULL</span></span>|<span data-ttu-id="1712a-130">Bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="1712a-130">Throws an error.</span></span>|  
|<span data-ttu-id="1712a-131">Satır Tipi NULL</span><span class="sxs-lookup"><span data-stu-id="1712a-131">RowType IS NULL</span></span>|<span data-ttu-id="1712a-132">Bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="1712a-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1712a-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="1712a-133">Example</span></span>  
 <span data-ttu-id="1712a-134">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu, sorgu ifadesinin null olup olmadığını belirlemek için NULL işleci Değİl'i kullanır.</span><span class="sxs-lookup"><span data-stu-id="1712a-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="1712a-135">Sorgu AdventureWorks Satış Modeli dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1712a-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1712a-136">Bu sorguyı derlemek ve çalıştırmak için aşağıdaki adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="1712a-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1712a-137">[YapısalTürü Sonuçları Döndüren Bir Sorguyu Yürütme: Nasıl Yapılır'daki](../how-to-execute-a-query-that-returns-structuraltype-results.md)yordamı izleyin.</span><span class="sxs-lookup"><span data-stu-id="1712a-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1712a-138">Aşağıdaki sorguyu bağımsız değişken `ExecuteStructuralTypeQuery` olarak yönteme geçirin:</span><span class="sxs-lookup"><span data-stu-id="1712a-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="1712a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1712a-139">See also</span></span>

- [<span data-ttu-id="1712a-140">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1712a-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
