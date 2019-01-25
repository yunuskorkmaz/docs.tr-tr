---
title: Entity SQL hızlı başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 20d8d1cb1e4b5cbf37dffcce6a7e79c2a4c265d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539409"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="bd21c-102">Entity SQL hızlı başvurusu</span><span class="sxs-lookup"><span data-stu-id="bd21c-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="bd21c-103">Bu konu, hızlı başvuru sağlar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="bd21c-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="bd21c-104">Sorgular, bu konuda, AdventureWorks satış modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="bd21c-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="bd21c-105">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="bd21c-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="bd21c-106">Dize</span><span class="sxs-lookup"><span data-stu-id="bd21c-106">String</span></span>  
 <span data-ttu-id="bd21c-107">Unicode ve Unicode olmayan karakter dize değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="bd21c-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="bd21c-108">Unicode dizelerini ile n tanımlandıkları Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="bd21c-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="bd21c-109">Unicode olmayan dize sabitinin bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bd21c-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="bd21c-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-110">Output:</span></span>  
  
|<span data-ttu-id="bd21c-111">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-112">Merhaba</span><span class="sxs-lookup"><span data-stu-id="bd21c-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="bd21c-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="bd21c-113">DateTime</span></span>  
 <span data-ttu-id="bd21c-114">DateTime değişmez değerlerine, tarih ve saat bölümleri zorunludur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="bd21c-115">Varsayılan değerler yoktur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-115">There are no default values.</span></span>  
  
 <span data-ttu-id="bd21c-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="bd21c-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-117">Output:</span></span>  
  
|<span data-ttu-id="bd21c-118">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-119">12/25/2006 01:01: 00'DA</span><span class="sxs-lookup"><span data-stu-id="bd21c-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="bd21c-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="bd21c-120">Integer</span></span>  
 <span data-ttu-id="bd21c-121">Tamsayı sabit değerlerinde Int32 türünü olabilir (123) UInt32 (123U), Int64 (123L) ve UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="bd21c-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="bd21c-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="bd21c-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-123">Output:</span></span>  
  
|<span data-ttu-id="bd21c-124">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-125">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-125">1</span></span>|  
|<span data-ttu-id="bd21c-126">2</span><span class="sxs-lookup"><span data-stu-id="bd21c-126">2</span></span>|  
|<span data-ttu-id="bd21c-127">3</span><span class="sxs-lookup"><span data-stu-id="bd21c-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="bd21c-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="bd21c-128">Other</span></span>  
 <span data-ttu-id="bd21c-129">Tarafından desteklenen diğer sabitler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olan GUID, ikili, kayan nokta/Double, Decimal, ve `null`.</span><span class="sxs-lookup"><span data-stu-id="bd21c-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="bd21c-130">Null değişmez değerlerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeldeki diğer her tür ile uyumlu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="bd21c-131">Türü oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="bd21c-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="bd21c-132">SATIR</span><span class="sxs-lookup"><span data-stu-id="bd21c-132">ROW</span></span>  
 <span data-ttu-id="bd21c-133">[Satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) bir anonim, yapısal olarak yazılmış (kayıt) değeri olarak oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="bd21c-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="bd21c-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="bd21c-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-135">Output:</span></span>  
  
|<span data-ttu-id="bd21c-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="bd21c-136">ProductID</span></span>|<span data-ttu-id="bd21c-137">Ad</span><span class="sxs-lookup"><span data-stu-id="bd21c-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="bd21c-138">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-138">1</span></span>|<span data-ttu-id="bd21c-139">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="bd21c-139">Adjustable Race</span></span>|  
|<span data-ttu-id="bd21c-140">879</span><span class="sxs-lookup"><span data-stu-id="bd21c-140">879</span></span>|<span data-ttu-id="bd21c-141">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="bd21c-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bd21c-142">712</span><span class="sxs-lookup"><span data-stu-id="bd21c-142">712</span></span>|<span data-ttu-id="bd21c-143">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="bd21c-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bd21c-144">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-144">...</span></span>|<span data-ttu-id="bd21c-145">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="bd21c-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="bd21c-146">MULTISET</span></span>  
 <span data-ttu-id="bd21c-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) koleksiyonları gibi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bd21c-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="bd21c-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="bd21c-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="bd21c-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="bd21c-150">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-150">Output:</span></span>  
  
|<span data-ttu-id="bd21c-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="bd21c-151">ProductID</span></span>|<span data-ttu-id="bd21c-152">Ad</span><span class="sxs-lookup"><span data-stu-id="bd21c-152">Name</span></span>|<span data-ttu-id="bd21c-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="bd21c-153">ProductNumber</span></span>|<span data-ttu-id="bd21c-154">…</span><span class="sxs-lookup"><span data-stu-id="bd21c-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="bd21c-155">842</span><span class="sxs-lookup"><span data-stu-id="bd21c-155">842</span></span>|<span data-ttu-id="bd21c-156">Yarış Panniers, büyük</span><span class="sxs-lookup"><span data-stu-id="bd21c-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="bd21c-157">PA T100</span><span class="sxs-lookup"><span data-stu-id="bd21c-157">PA-T100</span></span>|<span data-ttu-id="bd21c-158">…</span><span class="sxs-lookup"><span data-stu-id="bd21c-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="bd21c-159">Nesne</span><span class="sxs-lookup"><span data-stu-id="bd21c-159">Object</span></span>  
 <span data-ttu-id="bd21c-160">[Konstruktor Typu adlı](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) gibi kullanıcı tanımlı nesneler (adlandırılmış), yapıları `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="bd21c-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="bd21c-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="bd21c-162">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-162">Output:</span></span>  
  
|<span data-ttu-id="bd21c-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="bd21c-163">SalesOrderDetailID</span></span>|<span data-ttu-id="bd21c-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="bd21c-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="bd21c-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="bd21c-165">OrderQty</span></span>|<span data-ttu-id="bd21c-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="bd21c-166">ProductID</span></span>|<span data-ttu-id="bd21c-167">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="bd21c-168">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-168">1</span></span>|<span data-ttu-id="bd21c-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="bd21c-169">4911-403C-98</span></span>|<span data-ttu-id="bd21c-170">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-170">1</span></span>|<span data-ttu-id="bd21c-171">776</span><span class="sxs-lookup"><span data-stu-id="bd21c-171">776</span></span>|<span data-ttu-id="bd21c-172">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-172">...</span></span>|  
|<span data-ttu-id="bd21c-173">2</span><span class="sxs-lookup"><span data-stu-id="bd21c-173">2</span></span>|<span data-ttu-id="bd21c-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="bd21c-174">4911-403C-98</span></span>|<span data-ttu-id="bd21c-175">3</span><span class="sxs-lookup"><span data-stu-id="bd21c-175">3</span></span>|<span data-ttu-id="bd21c-176">777</span><span class="sxs-lookup"><span data-stu-id="bd21c-176">777</span></span>|<span data-ttu-id="bd21c-177">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-177">...</span></span>|  
|<span data-ttu-id="bd21c-178">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-178">...</span></span>|<span data-ttu-id="bd21c-179">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-179">...</span></span>|<span data-ttu-id="bd21c-180">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-180">...</span></span>|<span data-ttu-id="bd21c-181">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-181">...</span></span>|<span data-ttu-id="bd21c-182">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="bd21c-183">Referanslar</span><span class="sxs-lookup"><span data-stu-id="bd21c-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="bd21c-184">BAŞVURU</span><span class="sxs-lookup"><span data-stu-id="bd21c-184">REF</span></span>  
 <span data-ttu-id="bd21c-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="bd21c-186">Örneğin, aşağıdaki sorgu, siparişler varlık kümesinde her sipariş varlığı için başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="bd21c-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="bd21c-187">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-187">Output:</span></span>  
  
|<span data-ttu-id="bd21c-188">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-189">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-189">1</span></span>|  
|<span data-ttu-id="bd21c-190">2</span><span class="sxs-lookup"><span data-stu-id="bd21c-190">2</span></span>|  
|<span data-ttu-id="bd21c-191">3</span><span class="sxs-lookup"><span data-stu-id="bd21c-191">3</span></span>|  
|<span data-ttu-id="bd21c-192">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-192">...</span></span>|  
  
 <span data-ttu-id="bd21c-193">Aşağıdaki örnek, bir varlığın bir özelliğe erişmek için özelliği çıkarma işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bd21c-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="bd21c-194">Özelliği ayıklama işleci kullanılmadığında otomatik olarak başvurusu kaldırılmış bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="bd21c-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="bd21c-196">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-196">Output:</span></span>  
  
|<span data-ttu-id="bd21c-197">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-198">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="bd21c-198">Adjustable Race</span></span>|  
|<span data-ttu-id="bd21c-199">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="bd21c-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bd21c-200">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="bd21c-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bd21c-201">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="bd21c-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="bd21c-202">DEREF</span></span>  
 <span data-ttu-id="bd21c-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd21c-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="bd21c-204">Örneğin, aşağıdaki sorguyu siparişler varlık kümesindeki her sipariş için sipariş varlıklara üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="bd21c-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="bd21c-205">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="bd21c-206">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-206">Output:</span></span>  
  
|<span data-ttu-id="bd21c-207">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-208">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="bd21c-208">Adjustable Race</span></span>|  
|<span data-ttu-id="bd21c-209">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="bd21c-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bd21c-210">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="bd21c-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bd21c-211">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="bd21c-212">CREATEREF VE ANAHTARI</span><span class="sxs-lookup"><span data-stu-id="bd21c-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="bd21c-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) bir anahtarını geçirerek başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd21c-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="bd21c-214">[ANAHTAR](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) ifade türü referansı ile anahtar bölümünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="bd21c-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="bd21c-215">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="bd21c-216">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-216">Output:</span></span>  
  
|<span data-ttu-id="bd21c-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="bd21c-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="bd21c-218">980</span><span class="sxs-lookup"><span data-stu-id="bd21c-218">980</span></span>|  
|<span data-ttu-id="bd21c-219">365</span><span class="sxs-lookup"><span data-stu-id="bd21c-219">365</span></span>|  
|<span data-ttu-id="bd21c-220">771</span><span class="sxs-lookup"><span data-stu-id="bd21c-220">771</span></span>|  
|<span data-ttu-id="bd21c-221">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="bd21c-222">İşlevler</span><span class="sxs-lookup"><span data-stu-id="bd21c-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="bd21c-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="bd21c-223">Canonical</span></span>  
 <span data-ttu-id="bd21c-224">Ad alanı için [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Edm, olarak olduğundan `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="bd21c-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="bd21c-225">Kurallı işlev ile aynı ada sahip bir işlev içeren başka bir ad alanı içe sürece ad alanını belirtmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="bd21c-226">İki ad alanı aynı işlevi varsa, kullanıcı özel tam adı gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="bd21c-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="bd21c-228">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-228">Output:</span></span>  
  
|<span data-ttu-id="bd21c-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="bd21c-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="bd21c-230">6</span><span class="sxs-lookup"><span data-stu-id="bd21c-230">6</span></span>|  
|<span data-ttu-id="bd21c-231">6</span><span class="sxs-lookup"><span data-stu-id="bd21c-231">6</span></span>|  
|<span data-ttu-id="bd21c-232">5</span><span class="sxs-lookup"><span data-stu-id="bd21c-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="bd21c-233">Microsoft sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="bd21c-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="bd21c-234">[Microsoft sağlayıcısı özel işlevler](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) bulunan `SqlServer` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bd21c-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="bd21c-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="bd21c-236">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-236">Output:</span></span>  
  
|<span data-ttu-id="bd21c-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="bd21c-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="bd21c-238">27</span><span class="sxs-lookup"><span data-stu-id="bd21c-238">27</span></span>|  
|<span data-ttu-id="bd21c-239">27</span><span class="sxs-lookup"><span data-stu-id="bd21c-239">27</span></span>|  
|<span data-ttu-id="bd21c-240">26</span><span class="sxs-lookup"><span data-stu-id="bd21c-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="bd21c-241">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="bd21c-241">Namespaces</span></span>  
 <span data-ttu-id="bd21c-242">[KULLANARAK](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="bd21c-243">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="bd21c-244">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-244">Output:</span></span>  
  
|<span data-ttu-id="bd21c-245">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-246">aa</span><span class="sxs-lookup"><span data-stu-id="bd21c-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="bd21c-247">Disk belleği</span><span class="sxs-lookup"><span data-stu-id="bd21c-247">Paging</span></span>  
 <span data-ttu-id="bd21c-248">Disk belleği bildirerek ifade edilen bir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) için alt yan tümceleri [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="bd21c-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="bd21c-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="bd21c-250">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-250">Output:</span></span>  
  
|<span data-ttu-id="bd21c-251">Kimlik</span><span class="sxs-lookup"><span data-stu-id="bd21c-251">ID</span></span>|<span data-ttu-id="bd21c-252">Ad</span><span class="sxs-lookup"><span data-stu-id="bd21c-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="bd21c-253">10</span><span class="sxs-lookup"><span data-stu-id="bd21c-253">10</span></span>|<span data-ttu-id="bd21c-254">Adina</span><span class="sxs-lookup"><span data-stu-id="bd21c-254">Adina</span></span>|  
|<span data-ttu-id="bd21c-255">11</span><span class="sxs-lookup"><span data-stu-id="bd21c-255">11</span></span>|<span data-ttu-id="bd21c-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="bd21c-256">Agcaoili</span></span>|  
|<span data-ttu-id="bd21c-257">12</span><span class="sxs-lookup"><span data-stu-id="bd21c-257">12</span></span>|<span data-ttu-id="bd21c-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="bd21c-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="bd21c-259">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="bd21c-259">Grouping</span></span>  
 <span data-ttu-id="bd21c-260">[GRUPLANDIRMA tarafından](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) bir sorgu tarafından döndürülen hangi nesnelere grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="bd21c-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="bd21c-261">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="bd21c-262">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-262">Output:</span></span>  
  
|<span data-ttu-id="bd21c-263">name</span><span class="sxs-lookup"><span data-stu-id="bd21c-263">name</span></span>|  
|----------|  
|<span data-ttu-id="bd21c-264">Tümünü Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="bd21c-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="bd21c-265">ML Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="bd21c-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="bd21c-266">HL Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="bd21c-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="bd21c-267">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="bd21c-268">Gezinti</span><span class="sxs-lookup"><span data-stu-id="bd21c-268">Navigation</span></span>  
 <span data-ttu-id="bd21c-269">İlişkinin gezinme işleci bir varlıktan (Bitiş) (sona erdirmek için) başka bir ilişkisi üzerinden gitmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd21c-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="bd21c-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ilişki türü tam olarak alır \<ad alanı >.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="bd21c-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="bd21c-271">Git başvuru dönüşleri\<T >, kardinalitesi sonlandırmak için 1'dir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="bd21c-272">Varsa önem düzeyini sonlandırmak için n, koleksiyonu olan < Ref\<T >> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bd21c-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="bd21c-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="bd21c-274">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-274">Output:</span></span>  
  
|<span data-ttu-id="bd21c-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="bd21c-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="bd21c-276">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-276">1</span></span>|  
|<span data-ttu-id="bd21c-277">2</span><span class="sxs-lookup"><span data-stu-id="bd21c-277">2</span></span>|  
|<span data-ttu-id="bd21c-278">3</span><span class="sxs-lookup"><span data-stu-id="bd21c-278">3</span></span>|  
|<span data-ttu-id="bd21c-279">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="bd21c-280">DEĞER VE SEÇ'İ SEÇİN</span><span class="sxs-lookup"><span data-stu-id="bd21c-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="bd21c-281">DEĞER SEÇİN</span><span class="sxs-lookup"><span data-stu-id="bd21c-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="bd21c-282">SELECT VALUE yan tümcesi, örtük satır oluşturma atlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd21c-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="bd21c-283">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="bd21c-284">Böyle bir yan tümcesi kullanıldığında, öğelerin SELECT yan tümcesinde etrafında hiçbir satır sarmalayıcı oluşturulur ve istediğiniz şekle koleksiyonu, örneğin üretilebilir: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="bd21c-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="bd21c-285">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="bd21c-286">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-286">Output:</span></span>  
  
|<span data-ttu-id="bd21c-287">Ad</span><span class="sxs-lookup"><span data-stu-id="bd21c-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="bd21c-288">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="bd21c-288">Adjustable Race</span></span>|  
|<span data-ttu-id="bd21c-289">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="bd21c-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="bd21c-290">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="bd21c-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="bd21c-291">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="bd21c-292">SEÇ</span><span class="sxs-lookup"><span data-stu-id="bd21c-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="bd21c-293">row oluşturucusunda rastgele satırları oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd21c-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="bd21c-294">SELECT yansıtma bir veya daha fazla öğeleri ve sonuçları bir veri kayıttaki alanları ile örneğin alır: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="bd21c-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="bd21c-295">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-295">Example:</span></span>  
  
 <span data-ttu-id="bd21c-296">SELECT p.Name, p.ProductID AdventureWorksEntities.Product p çıktı olarak gelen:</span><span class="sxs-lookup"><span data-stu-id="bd21c-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="bd21c-297">Ad</span><span class="sxs-lookup"><span data-stu-id="bd21c-297">Name</span></span>|<span data-ttu-id="bd21c-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="bd21c-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="bd21c-299">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="bd21c-299">Adjustable Race</span></span>|<span data-ttu-id="bd21c-300">1.</span><span class="sxs-lookup"><span data-stu-id="bd21c-300">1</span></span>|  
|<span data-ttu-id="bd21c-301">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="bd21c-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="bd21c-302">879</span><span class="sxs-lookup"><span data-stu-id="bd21c-302">879</span></span>|  
|<span data-ttu-id="bd21c-303">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="bd21c-303">AWC Logo Cap</span></span>|<span data-ttu-id="bd21c-304">712</span><span class="sxs-lookup"><span data-stu-id="bd21c-304">712</span></span>|  
|<span data-ttu-id="bd21c-305">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-305">...</span></span>|<span data-ttu-id="bd21c-306">...</span><span class="sxs-lookup"><span data-stu-id="bd21c-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="bd21c-307">CASE İFADESİ</span><span class="sxs-lookup"><span data-stu-id="bd21c-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="bd21c-308">[Case ifadesi](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) sonucu belirlemek için Boolean ifadeler bir dizi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="bd21c-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="bd21c-309">Örnek:</span><span class="sxs-lookup"><span data-stu-id="bd21c-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="bd21c-310">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="bd21c-310">Output:</span></span>  
  
|<span data-ttu-id="bd21c-311">Değer</span><span class="sxs-lookup"><span data-stu-id="bd21c-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="bd21c-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="bd21c-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd21c-313">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd21c-313">See also</span></span>
- [<span data-ttu-id="bd21c-314">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bd21c-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="bd21c-315">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bd21c-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
