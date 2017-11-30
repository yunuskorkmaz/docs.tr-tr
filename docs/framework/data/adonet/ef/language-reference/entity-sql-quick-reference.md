---
title: "Varlık SQL hızlı başvuru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 19be8e04f8bb0cb11c98d5361deb6deffe797fca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="6106e-102">Varlık SQL hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="6106e-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="6106e-103">Bu konu, hızlı başvuru sağlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="6106e-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="6106e-104">Bu konuda sorgularda AdventureWorks satış model üzerinde temel alır.</span><span class="sxs-lookup"><span data-stu-id="6106e-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="6106e-105">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="6106e-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="6106e-106">Dize</span><span class="sxs-lookup"><span data-stu-id="6106e-106">String</span></span>  
 <span data-ttu-id="6106e-107">Unicode ve Unicode olmayan karakter dize değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="6106e-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="6106e-108">Unicode dizelerini ile n $a Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="6106e-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="6106e-109">Unicode olmayan dize sabit değeri bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6106e-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="6106e-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-110">Output:</span></span>  
  
|<span data-ttu-id="6106e-111">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-112">Merhaba</span><span class="sxs-lookup"><span data-stu-id="6106e-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="6106e-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="6106e-113">DateTime</span></span>  
 <span data-ttu-id="6106e-114">DateTime değişmez değerlerine tarih ve saat bölümleri zorunludur.</span><span class="sxs-lookup"><span data-stu-id="6106e-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="6106e-115">Varsayılan değerler yoktur.</span><span class="sxs-lookup"><span data-stu-id="6106e-115">There are no default values.</span></span>  
  
 <span data-ttu-id="6106e-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="6106e-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-117">Output:</span></span>  
  
|<span data-ttu-id="6106e-118">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="6106e-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="6106e-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="6106e-120">Integer</span></span>  
 <span data-ttu-id="6106e-121">Tamsayı değişmez değerleri Int32 türünde olabilir (123) UInt32 (123U) Int64 (123L) ve UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="6106e-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="6106e-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="6106e-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-123">Output:</span></span>  
  
|<span data-ttu-id="6106e-124">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-125">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-125">1</span></span>|  
|<span data-ttu-id="6106e-126">2</span><span class="sxs-lookup"><span data-stu-id="6106e-126">2</span></span>|  
|<span data-ttu-id="6106e-127">3</span><span class="sxs-lookup"><span data-stu-id="6106e-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="6106e-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="6106e-128">Other</span></span>  
 <span data-ttu-id="6106e-129">Tarafından desteklenen diğer değişmez değerleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olan GUID, ikili, Float/Double, Decimal, ve `null`.</span><span class="sxs-lookup"><span data-stu-id="6106e-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="6106e-130">Null değişmez değerlerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeldeki her bir türü ile uyumlu olduğu kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="6106e-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="6106e-131">Türü oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="6106e-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="6106e-132">SATIR</span><span class="sxs-lookup"><span data-stu-id="6106e-132">ROW</span></span>  
 <span data-ttu-id="6106e-133">[Satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) gibi bir anonim, yapısal olarak yazılan (kayıt) değeri oluşturur:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="6106e-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="6106e-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="6106e-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-135">Output:</span></span>  
  
|<span data-ttu-id="6106e-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="6106e-136">ProductID</span></span>|<span data-ttu-id="6106e-137">Ad</span><span class="sxs-lookup"><span data-stu-id="6106e-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="6106e-138">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-138">1</span></span>|<span data-ttu-id="6106e-139">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="6106e-139">Adjustable Race</span></span>|  
|<span data-ttu-id="6106e-140">879</span><span class="sxs-lookup"><span data-stu-id="6106e-140">879</span></span>|<span data-ttu-id="6106e-141">Çok amaçlı bisiklet yedek</span><span class="sxs-lookup"><span data-stu-id="6106e-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6106e-142">712</span><span class="sxs-lookup"><span data-stu-id="6106e-142">712</span></span>|<span data-ttu-id="6106e-143">AWC logosu Cap</span><span class="sxs-lookup"><span data-stu-id="6106e-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6106e-144">...</span><span class="sxs-lookup"><span data-stu-id="6106e-144">...</span></span>|<span data-ttu-id="6106e-145">...</span><span class="sxs-lookup"><span data-stu-id="6106e-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="6106e-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="6106e-146">MULTISET</span></span>  
 <span data-ttu-id="6106e-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) koleksiyonları gibi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="6106e-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="6106e-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="6106e-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="6106e-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="6106e-150">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-150">Output:</span></span>  
  
|<span data-ttu-id="6106e-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="6106e-151">ProductID</span></span>|<span data-ttu-id="6106e-152">Ad</span><span class="sxs-lookup"><span data-stu-id="6106e-152">Name</span></span>|<span data-ttu-id="6106e-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="6106e-153">ProductNumber</span></span>|<span data-ttu-id="6106e-154">…</span><span class="sxs-lookup"><span data-stu-id="6106e-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="6106e-155">842</span><span class="sxs-lookup"><span data-stu-id="6106e-155">842</span></span>|<span data-ttu-id="6106e-156">Tur Panniers, büyük</span><span class="sxs-lookup"><span data-stu-id="6106e-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="6106e-157">PA T100</span><span class="sxs-lookup"><span data-stu-id="6106e-157">PA-T100</span></span>|<span data-ttu-id="6106e-158">…</span><span class="sxs-lookup"><span data-stu-id="6106e-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="6106e-159">Nesne</span><span class="sxs-lookup"><span data-stu-id="6106e-159">Object</span></span>  
 <span data-ttu-id="6106e-160">[Tür oluşturucu adlı](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) gibi kullanıcı tanımlı (adlandırılmış) nesneleri oluşturur `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="6106e-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="6106e-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="6106e-162">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-162">Output:</span></span>  
  
|<span data-ttu-id="6106e-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="6106e-163">SalesOrderDetailID</span></span>|<span data-ttu-id="6106e-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="6106e-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="6106e-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="6106e-165">OrderQty</span></span>|<span data-ttu-id="6106e-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="6106e-166">ProductID</span></span>|<span data-ttu-id="6106e-167">...</span><span class="sxs-lookup"><span data-stu-id="6106e-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="6106e-168">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-168">1</span></span>|<span data-ttu-id="6106e-169">4911 403C 98</span><span class="sxs-lookup"><span data-stu-id="6106e-169">4911-403C-98</span></span>|<span data-ttu-id="6106e-170">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-170">1</span></span>|<span data-ttu-id="6106e-171">776</span><span class="sxs-lookup"><span data-stu-id="6106e-171">776</span></span>|<span data-ttu-id="6106e-172">...</span><span class="sxs-lookup"><span data-stu-id="6106e-172">...</span></span>|  
|<span data-ttu-id="6106e-173">2</span><span class="sxs-lookup"><span data-stu-id="6106e-173">2</span></span>|<span data-ttu-id="6106e-174">4911 403C 98</span><span class="sxs-lookup"><span data-stu-id="6106e-174">4911-403C-98</span></span>|<span data-ttu-id="6106e-175">3</span><span class="sxs-lookup"><span data-stu-id="6106e-175">3</span></span>|<span data-ttu-id="6106e-176">777</span><span class="sxs-lookup"><span data-stu-id="6106e-176">777</span></span>|<span data-ttu-id="6106e-177">...</span><span class="sxs-lookup"><span data-stu-id="6106e-177">...</span></span>|  
|<span data-ttu-id="6106e-178">...</span><span class="sxs-lookup"><span data-stu-id="6106e-178">...</span></span>|<span data-ttu-id="6106e-179">...</span><span class="sxs-lookup"><span data-stu-id="6106e-179">...</span></span>|<span data-ttu-id="6106e-180">...</span><span class="sxs-lookup"><span data-stu-id="6106e-180">...</span></span>|<span data-ttu-id="6106e-181">...</span><span class="sxs-lookup"><span data-stu-id="6106e-181">...</span></span>|<span data-ttu-id="6106e-182">...</span><span class="sxs-lookup"><span data-stu-id="6106e-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="6106e-183">Referanslar</span><span class="sxs-lookup"><span data-stu-id="6106e-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="6106e-184">REF</span><span class="sxs-lookup"><span data-stu-id="6106e-184">REF</span></span>  
 <span data-ttu-id="6106e-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6106e-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="6106e-186">Örneğin, aşağıdaki sorguyu her sipariş varlık başvuruları siparişleri varlık kümesinde döndürür:</span><span class="sxs-lookup"><span data-stu-id="6106e-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="6106e-187">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-187">Output:</span></span>  
  
|<span data-ttu-id="6106e-188">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-189">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-189">1</span></span>|  
|<span data-ttu-id="6106e-190">2</span><span class="sxs-lookup"><span data-stu-id="6106e-190">2</span></span>|  
|<span data-ttu-id="6106e-191">3</span><span class="sxs-lookup"><span data-stu-id="6106e-191">3</span></span>|  
|<span data-ttu-id="6106e-192">...</span><span class="sxs-lookup"><span data-stu-id="6106e-192">...</span></span>|  
  
 <span data-ttu-id="6106e-193">Aşağıdaki örnek, bir varlığın bir özelliğe erişmek için özelliği ayıklama işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="6106e-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="6106e-194">Özellik ayıklama operatörü kullanıldığında, otomatik olarak dereferenced başvurudur.</span><span class="sxs-lookup"><span data-stu-id="6106e-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="6106e-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6106e-196">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-196">Output:</span></span>  
  
|<span data-ttu-id="6106e-197">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-198">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="6106e-198">Adjustable Race</span></span>|  
|<span data-ttu-id="6106e-199">Çok amaçlı bisiklet yedek</span><span class="sxs-lookup"><span data-stu-id="6106e-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6106e-200">AWC logosu Cap</span><span class="sxs-lookup"><span data-stu-id="6106e-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6106e-201">...</span><span class="sxs-lookup"><span data-stu-id="6106e-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="6106e-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="6106e-202">DEREF</span></span>  
 <span data-ttu-id="6106e-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences bir başvuru değer ve başvuru sonucu, üretir.</span><span class="sxs-lookup"><span data-stu-id="6106e-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="6106e-204">Örneğin, aşağıdaki sorguyu her siparişleri varlık kümesini sırayla için sipariş varlıklara üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="6106e-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="6106e-205">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6106e-206">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-206">Output:</span></span>  
  
|<span data-ttu-id="6106e-207">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-208">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="6106e-208">Adjustable Race</span></span>|  
|<span data-ttu-id="6106e-209">Çok amaçlı bisiklet yedek</span><span class="sxs-lookup"><span data-stu-id="6106e-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6106e-210">AWC logosu Cap</span><span class="sxs-lookup"><span data-stu-id="6106e-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6106e-211">...</span><span class="sxs-lookup"><span data-stu-id="6106e-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="6106e-212">CREATEREF VE ANAHTARI</span><span class="sxs-lookup"><span data-stu-id="6106e-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="6106e-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) bir anahtar geçirme bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6106e-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="6106e-214">[ANAHTAR](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) türü başvurusu olan bir ifade anahtar bölümünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="6106e-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="6106e-215">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6106e-216">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-216">Output:</span></span>  
  
|<span data-ttu-id="6106e-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="6106e-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="6106e-218">980</span><span class="sxs-lookup"><span data-stu-id="6106e-218">980</span></span>|  
|<span data-ttu-id="6106e-219">365</span><span class="sxs-lookup"><span data-stu-id="6106e-219">365</span></span>|  
|<span data-ttu-id="6106e-220">771</span><span class="sxs-lookup"><span data-stu-id="6106e-220">771</span></span>|  
|<span data-ttu-id="6106e-221">...</span><span class="sxs-lookup"><span data-stu-id="6106e-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="6106e-222">İşlevler</span><span class="sxs-lookup"><span data-stu-id="6106e-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="6106e-223">Kurallı</span><span class="sxs-lookup"><span data-stu-id="6106e-223">Canonical</span></span>  
 <span data-ttu-id="6106e-224">Ad alanı için [kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Edm, olarak yer `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="6106e-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="6106e-225">Kurallı işlevi olarak aynı ada sahip bir işlevi içeren başka bir ad alanı içe sürece ad belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6106e-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="6106e-226">İki ad alanı aynı işlevi varsa, kullanıcı özel tam adı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6106e-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="6106e-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="6106e-228">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-228">Output:</span></span>  
  
|<span data-ttu-id="6106e-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="6106e-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="6106e-230">6</span><span class="sxs-lookup"><span data-stu-id="6106e-230">6</span></span>|  
|<span data-ttu-id="6106e-231">6</span><span class="sxs-lookup"><span data-stu-id="6106e-231">6</span></span>|  
|<span data-ttu-id="6106e-232">5</span><span class="sxs-lookup"><span data-stu-id="6106e-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="6106e-233">Microsoft sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="6106e-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="6106e-234">[Microsoft sağlayıcıya özgü işlevleri](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) bulunan `SqlServer` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="6106e-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="6106e-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="6106e-236">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-236">Output:</span></span>  
  
|<span data-ttu-id="6106e-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="6106e-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="6106e-238">27</span><span class="sxs-lookup"><span data-stu-id="6106e-238">27</span></span>|  
|<span data-ttu-id="6106e-239">27</span><span class="sxs-lookup"><span data-stu-id="6106e-239">27</span></span>|  
|<span data-ttu-id="6106e-240">26</span><span class="sxs-lookup"><span data-stu-id="6106e-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="6106e-241">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="6106e-241">Namespaces</span></span>  
 <span data-ttu-id="6106e-242">[KULLANARAK](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) sorgu ifadesinde kullanılan ad belirtir.</span><span class="sxs-lookup"><span data-stu-id="6106e-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="6106e-243">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="6106e-244">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-244">Output:</span></span>  
  
|<span data-ttu-id="6106e-245">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-246">aa</span><span class="sxs-lookup"><span data-stu-id="6106e-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="6106e-247">Disk belleği</span><span class="sxs-lookup"><span data-stu-id="6106e-247">Paging</span></span>  
 <span data-ttu-id="6106e-248">Disk belleği bildirerek ifade edilen bir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6106e-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="6106e-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="6106e-250">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-250">Output:</span></span>  
  
|<span data-ttu-id="6106e-251">Kimlik</span><span class="sxs-lookup"><span data-stu-id="6106e-251">ID</span></span>|<span data-ttu-id="6106e-252">Ad</span><span class="sxs-lookup"><span data-stu-id="6106e-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="6106e-253">10</span><span class="sxs-lookup"><span data-stu-id="6106e-253">10</span></span>|<span data-ttu-id="6106e-254">Adina</span><span class="sxs-lookup"><span data-stu-id="6106e-254">Adina</span></span>|  
|<span data-ttu-id="6106e-255">11</span><span class="sxs-lookup"><span data-stu-id="6106e-255">11</span></span>|<span data-ttu-id="6106e-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="6106e-256">Agcaoili</span></span>|  
|<span data-ttu-id="6106e-257">12</span><span class="sxs-lookup"><span data-stu-id="6106e-257">12</span></span>|<span data-ttu-id="6106e-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="6106e-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="6106e-259">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="6106e-259">Grouping</span></span>  
 <span data-ttu-id="6106e-260">[GRUPLANDIRMA tarafından](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) bir sorgu tarafından döndürülen hangi nesneleri içine grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="6106e-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="6106e-261">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="6106e-262">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-262">Output:</span></span>  
  
|<span data-ttu-id="6106e-263">name</span><span class="sxs-lookup"><span data-stu-id="6106e-263">name</span></span>|  
|----------|  
|<span data-ttu-id="6106e-264">ÜM Sıradağlar bilgisayar başına derleme</span><span class="sxs-lookup"><span data-stu-id="6106e-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="6106e-265">ML Sıradağlar bilgisayar başına derleme</span><span class="sxs-lookup"><span data-stu-id="6106e-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="6106e-266">HL Sıradağlar bilgisayar başına derleme</span><span class="sxs-lookup"><span data-stu-id="6106e-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="6106e-267">...</span><span class="sxs-lookup"><span data-stu-id="6106e-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="6106e-268">Gezinme</span><span class="sxs-lookup"><span data-stu-id="6106e-268">Navigation</span></span>  
 <span data-ttu-id="6106e-269">İlişki Gezinti işleci bir varlıktan (Bitiş) (sona erdirmek için) başka bir ilişkiden üzerinden giderek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6106e-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="6106e-270">[Bul](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ilişki türü tam olarak sürer \<ad alanı >.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="6106e-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="6106e-271">Gidin başvuru dönüşleri\<T >, önemi sona erdirmek için 1'dir.</span><span class="sxs-lookup"><span data-stu-id="6106e-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="6106e-272">Varsa önemi sonuna n, toplama, < Ref\<T >> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6106e-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="6106e-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="6106e-274">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-274">Output:</span></span>  
  
|<span data-ttu-id="6106e-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="6106e-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="6106e-276">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-276">1</span></span>|  
|<span data-ttu-id="6106e-277">2</span><span class="sxs-lookup"><span data-stu-id="6106e-277">2</span></span>|  
|<span data-ttu-id="6106e-278">3</span><span class="sxs-lookup"><span data-stu-id="6106e-278">3</span></span>|  
|<span data-ttu-id="6106e-279">...</span><span class="sxs-lookup"><span data-stu-id="6106e-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="6106e-280">DEĞER SEÇİP SEÇİN</span><span class="sxs-lookup"><span data-stu-id="6106e-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="6106e-281">DEĞERİNİ SEÇİN</span><span class="sxs-lookup"><span data-stu-id="6106e-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="6106e-282">örtük satır yapım atlamak için SELECT VALUE yan tümcesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6106e-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="6106e-283">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="6106e-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="6106e-284">Bu tür bir yan tümcesi kullanıldığında, hiçbir satır sarmalayıcı SELECT yan tümcesinde öğelerin etrafında oluşturulur ve istediğiniz şekli koleksiyonu, örneğin üretilmiş olabilecek: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="6106e-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="6106e-285">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="6106e-286">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-286">Output:</span></span>  
  
|<span data-ttu-id="6106e-287">Ad</span><span class="sxs-lookup"><span data-stu-id="6106e-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="6106e-288">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="6106e-288">Adjustable Race</span></span>|  
|<span data-ttu-id="6106e-289">Çok amaçlı bisiklet yedek</span><span class="sxs-lookup"><span data-stu-id="6106e-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="6106e-290">AWC logosu Cap</span><span class="sxs-lookup"><span data-stu-id="6106e-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="6106e-291">...</span><span class="sxs-lookup"><span data-stu-id="6106e-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="6106e-292">SEÇ</span><span class="sxs-lookup"><span data-stu-id="6106e-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="6106e-293">row Oluşturucusu rasgele satırları oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="6106e-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="6106e-294">SELECT yansıtma bir veya daha fazla öğe ve bir veri kaydını alanları ile sonuçlanır örneğin alır: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="6106e-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="6106e-295">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-295">Example:</span></span>  
  
 <span data-ttu-id="6106e-296">SELECT p.Name, p.ProductID AdventureWorksEntities.Product p çıktı olarak gelen:</span><span class="sxs-lookup"><span data-stu-id="6106e-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="6106e-297">Ad</span><span class="sxs-lookup"><span data-stu-id="6106e-297">Name</span></span>|<span data-ttu-id="6106e-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="6106e-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="6106e-299">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="6106e-299">Adjustable Race</span></span>|<span data-ttu-id="6106e-300">1.</span><span class="sxs-lookup"><span data-stu-id="6106e-300">1</span></span>|  
|<span data-ttu-id="6106e-301">Çok amaçlı bisiklet yedek</span><span class="sxs-lookup"><span data-stu-id="6106e-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="6106e-302">879</span><span class="sxs-lookup"><span data-stu-id="6106e-302">879</span></span>|  
|<span data-ttu-id="6106e-303">AWC logosu Cap</span><span class="sxs-lookup"><span data-stu-id="6106e-303">AWC Logo Cap</span></span>|<span data-ttu-id="6106e-304">712</span><span class="sxs-lookup"><span data-stu-id="6106e-304">712</span></span>|  
|<span data-ttu-id="6106e-305">...</span><span class="sxs-lookup"><span data-stu-id="6106e-305">...</span></span>|<span data-ttu-id="6106e-306">...</span><span class="sxs-lookup"><span data-stu-id="6106e-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="6106e-307">CASE DEYİMİ</span><span class="sxs-lookup"><span data-stu-id="6106e-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="6106e-308">[Case deyimi](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) sonucu belirlemek için Boole ifadeleri birtakım değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="6106e-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="6106e-309">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6106e-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="6106e-310">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="6106e-310">Output:</span></span>  
  
|<span data-ttu-id="6106e-311">Değer</span><span class="sxs-lookup"><span data-stu-id="6106e-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="6106e-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="6106e-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6106e-313">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6106e-313">See Also</span></span>  
 [<span data-ttu-id="6106e-314">Varlık SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6106e-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="6106e-315">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="6106e-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
