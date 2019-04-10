---
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207077"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="5341b-102">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5341b-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="5341b-103">Bu konu, hızlı başvuru sağlar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="5341b-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="5341b-104">Sorgular, bu konuda, AdventureWorks satış modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="5341b-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="5341b-105">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="5341b-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="5341b-106">Dize</span><span class="sxs-lookup"><span data-stu-id="5341b-106">String</span></span>  
 <span data-ttu-id="5341b-107">Unicode ve Unicode olmayan karakter dize değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5341b-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="5341b-108">Unicode dizelerini ile n tanımlandıkları Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="5341b-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="5341b-109">Unicode olmayan dize sabitinin bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5341b-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="5341b-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-110">Output:</span></span>  
  
|<span data-ttu-id="5341b-111">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-112">Merhaba</span><span class="sxs-lookup"><span data-stu-id="5341b-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="5341b-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="5341b-113">DateTime</span></span>  
 <span data-ttu-id="5341b-114">DateTime değişmez değerlerine, tarih ve saat bölümleri zorunludur.</span><span class="sxs-lookup"><span data-stu-id="5341b-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="5341b-115">Varsayılan değerler yoktur.</span><span class="sxs-lookup"><span data-stu-id="5341b-115">There are no default values.</span></span>  
  
 <span data-ttu-id="5341b-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="5341b-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-117">Output:</span></span>  
  
|<span data-ttu-id="5341b-118">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-119">12/25/2006 01:01: 00'DA</span><span class="sxs-lookup"><span data-stu-id="5341b-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="5341b-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="5341b-120">Integer</span></span>  
 <span data-ttu-id="5341b-121">Tamsayı sabit değerlerinde Int32 türünü olabilir (123) UInt32 (123U), Int64 (123L) ve UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="5341b-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="5341b-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="5341b-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-123">Output:</span></span>  
  
|<span data-ttu-id="5341b-124">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-125">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-125">1</span></span>|  
|<span data-ttu-id="5341b-126">2</span><span class="sxs-lookup"><span data-stu-id="5341b-126">2</span></span>|  
|<span data-ttu-id="5341b-127">3</span><span class="sxs-lookup"><span data-stu-id="5341b-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="5341b-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="5341b-128">Other</span></span>  
 <span data-ttu-id="5341b-129">Tarafından desteklenen diğer sabitler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olan GUID, ikili, kayan nokta/Double, Decimal, ve `null`.</span><span class="sxs-lookup"><span data-stu-id="5341b-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="5341b-130">Null değişmez değerlerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeldeki diğer her tür ile uyumlu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5341b-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="5341b-131">Türü oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="5341b-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="5341b-132">ROW</span><span class="sxs-lookup"><span data-stu-id="5341b-132">ROW</span></span>  
 <span data-ttu-id="5341b-133">[Satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) bir anonim, yapısal olarak yazılmış (kayıt) değeri olarak oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5341b-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in:</span></span> `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 <span data-ttu-id="5341b-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="5341b-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-135">Output:</span></span>  
  
|<span data-ttu-id="5341b-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="5341b-136">ProductID</span></span>|<span data-ttu-id="5341b-137">Ad</span><span class="sxs-lookup"><span data-stu-id="5341b-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="5341b-138">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-138">1</span></span>|<span data-ttu-id="5341b-139">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="5341b-139">Adjustable Race</span></span>|  
|<span data-ttu-id="5341b-140">879</span><span class="sxs-lookup"><span data-stu-id="5341b-140">879</span></span>|<span data-ttu-id="5341b-141">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="5341b-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5341b-142">712</span><span class="sxs-lookup"><span data-stu-id="5341b-142">712</span></span>|<span data-ttu-id="5341b-143">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="5341b-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5341b-144">...</span><span class="sxs-lookup"><span data-stu-id="5341b-144">...</span></span>|<span data-ttu-id="5341b-145">...</span><span class="sxs-lookup"><span data-stu-id="5341b-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="5341b-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="5341b-146">MULTISET</span></span>  
 <span data-ttu-id="5341b-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) koleksiyonları gibi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5341b-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 <span data-ttu-id="5341b-148">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-148">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="5341b-149">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-149">Output:</span></span>  
  
|<span data-ttu-id="5341b-150">ProductID</span><span class="sxs-lookup"><span data-stu-id="5341b-150">ProductID</span></span>|<span data-ttu-id="5341b-151">Ad</span><span class="sxs-lookup"><span data-stu-id="5341b-151">Name</span></span>|<span data-ttu-id="5341b-152">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="5341b-152">ProductNumber</span></span>|<span data-ttu-id="5341b-153">…</span><span class="sxs-lookup"><span data-stu-id="5341b-153">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="5341b-154">842</span><span class="sxs-lookup"><span data-stu-id="5341b-154">842</span></span>|<span data-ttu-id="5341b-155">Yarış Panniers, büyük</span><span class="sxs-lookup"><span data-stu-id="5341b-155">Touring-Panniers, Large</span></span>|<span data-ttu-id="5341b-156">PA T100</span><span class="sxs-lookup"><span data-stu-id="5341b-156">PA-T100</span></span>|<span data-ttu-id="5341b-157">…</span><span class="sxs-lookup"><span data-stu-id="5341b-157">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="5341b-158">Nesne</span><span class="sxs-lookup"><span data-stu-id="5341b-158">Object</span></span>  
 <span data-ttu-id="5341b-159">[Konstruktor Typu adlı](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) gibi kullanıcı tanımlı nesneler (adlandırılmış), yapıları `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="5341b-159">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="5341b-160">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-160">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="5341b-161">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-161">Output:</span></span>  
  
|<span data-ttu-id="5341b-162">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="5341b-162">SalesOrderDetailID</span></span>|<span data-ttu-id="5341b-163">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="5341b-163">CarrierTrackingNumber</span></span>|<span data-ttu-id="5341b-164">OrderQty</span><span class="sxs-lookup"><span data-stu-id="5341b-164">OrderQty</span></span>|<span data-ttu-id="5341b-165">ProductID</span><span class="sxs-lookup"><span data-stu-id="5341b-165">ProductID</span></span>|<span data-ttu-id="5341b-166">...</span><span class="sxs-lookup"><span data-stu-id="5341b-166">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="5341b-167">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-167">1</span></span>|<span data-ttu-id="5341b-168">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="5341b-168">4911-403C-98</span></span>|<span data-ttu-id="5341b-169">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-169">1</span></span>|<span data-ttu-id="5341b-170">776</span><span class="sxs-lookup"><span data-stu-id="5341b-170">776</span></span>|<span data-ttu-id="5341b-171">...</span><span class="sxs-lookup"><span data-stu-id="5341b-171">...</span></span>|  
|<span data-ttu-id="5341b-172">2</span><span class="sxs-lookup"><span data-stu-id="5341b-172">2</span></span>|<span data-ttu-id="5341b-173">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="5341b-173">4911-403C-98</span></span>|<span data-ttu-id="5341b-174">3</span><span class="sxs-lookup"><span data-stu-id="5341b-174">3</span></span>|<span data-ttu-id="5341b-175">777</span><span class="sxs-lookup"><span data-stu-id="5341b-175">777</span></span>|<span data-ttu-id="5341b-176">...</span><span class="sxs-lookup"><span data-stu-id="5341b-176">...</span></span>|  
|<span data-ttu-id="5341b-177">...</span><span class="sxs-lookup"><span data-stu-id="5341b-177">...</span></span>|<span data-ttu-id="5341b-178">...</span><span class="sxs-lookup"><span data-stu-id="5341b-178">...</span></span>|<span data-ttu-id="5341b-179">...</span><span class="sxs-lookup"><span data-stu-id="5341b-179">...</span></span>|<span data-ttu-id="5341b-180">...</span><span class="sxs-lookup"><span data-stu-id="5341b-180">...</span></span>|<span data-ttu-id="5341b-181">...</span><span class="sxs-lookup"><span data-stu-id="5341b-181">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="5341b-182">Referanslar</span><span class="sxs-lookup"><span data-stu-id="5341b-182">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="5341b-183">REF</span><span class="sxs-lookup"><span data-stu-id="5341b-183">REF</span></span>  
 <span data-ttu-id="5341b-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5341b-184">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="5341b-185">Örneğin, aşağıdaki sorgu, siparişler varlık kümesinde her sipariş varlığı için başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="5341b-185">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="5341b-186">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-186">Output:</span></span>  
  
|<span data-ttu-id="5341b-187">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-187">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-188">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-188">1</span></span>|  
|<span data-ttu-id="5341b-189">2</span><span class="sxs-lookup"><span data-stu-id="5341b-189">2</span></span>|  
|<span data-ttu-id="5341b-190">3</span><span class="sxs-lookup"><span data-stu-id="5341b-190">3</span></span>|  
|<span data-ttu-id="5341b-191">...</span><span class="sxs-lookup"><span data-stu-id="5341b-191">...</span></span>|  
  
 <span data-ttu-id="5341b-192">Aşağıdaki örnek, bir varlığın bir özelliğe erişmek için özelliği çıkarma işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5341b-192">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="5341b-193">Özelliği ayıklama işleci kullanılmadığında otomatik olarak başvurusu kaldırılmış bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="5341b-193">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="5341b-194">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-194">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5341b-195">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-195">Output:</span></span>  
  
|<span data-ttu-id="5341b-196">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-196">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-197">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="5341b-197">Adjustable Race</span></span>|  
|<span data-ttu-id="5341b-198">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="5341b-198">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5341b-199">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="5341b-199">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5341b-200">...</span><span class="sxs-lookup"><span data-stu-id="5341b-200">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="5341b-201">DEREF</span><span class="sxs-lookup"><span data-stu-id="5341b-201">DEREF</span></span>  
 <span data-ttu-id="5341b-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5341b-202">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="5341b-203">Örneğin, aşağıdaki sorguyu siparişler varlık kümesindeki her sipariş için sipariş varlıklara üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="5341b-203">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="5341b-204">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-204">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5341b-205">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-205">Output:</span></span>  
  
|<span data-ttu-id="5341b-206">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-206">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-207">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="5341b-207">Adjustable Race</span></span>|  
|<span data-ttu-id="5341b-208">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="5341b-208">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5341b-209">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="5341b-209">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5341b-210">...</span><span class="sxs-lookup"><span data-stu-id="5341b-210">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="5341b-211">CREATEREF VE ANAHTARI</span><span class="sxs-lookup"><span data-stu-id="5341b-211">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="5341b-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) bir anahtarını geçirerek başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5341b-212">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="5341b-213">[ANAHTAR](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) ifade türü referansı ile anahtar bölümünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="5341b-213">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="5341b-214">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-214">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5341b-215">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-215">Output:</span></span>  
  
|<span data-ttu-id="5341b-216">ProductID</span><span class="sxs-lookup"><span data-stu-id="5341b-216">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="5341b-217">980</span><span class="sxs-lookup"><span data-stu-id="5341b-217">980</span></span>|  
|<span data-ttu-id="5341b-218">365</span><span class="sxs-lookup"><span data-stu-id="5341b-218">365</span></span>|  
|<span data-ttu-id="5341b-219">771</span><span class="sxs-lookup"><span data-stu-id="5341b-219">771</span></span>|  
|<span data-ttu-id="5341b-220">...</span><span class="sxs-lookup"><span data-stu-id="5341b-220">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="5341b-221">İşlevler</span><span class="sxs-lookup"><span data-stu-id="5341b-221">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="5341b-222">Canonical</span><span class="sxs-lookup"><span data-stu-id="5341b-222">Canonical</span></span>  
 <span data-ttu-id="5341b-223">Ad alanı için [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Edm, olarak olduğundan `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="5341b-223">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="5341b-224">Kurallı işlev ile aynı ada sahip bir işlev içeren başka bir ad alanı içe sürece ad alanını belirtmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="5341b-224">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="5341b-225">İki ad alanı aynı işlevi varsa, kullanıcı özel tam adı gerekir.</span><span class="sxs-lookup"><span data-stu-id="5341b-225">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="5341b-226">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-226">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="5341b-227">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-227">Output:</span></span>  
  
|<span data-ttu-id="5341b-228">NameLen</span><span class="sxs-lookup"><span data-stu-id="5341b-228">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="5341b-229">6</span><span class="sxs-lookup"><span data-stu-id="5341b-229">6</span></span>|  
|<span data-ttu-id="5341b-230">6</span><span class="sxs-lookup"><span data-stu-id="5341b-230">6</span></span>|  
|<span data-ttu-id="5341b-231">5</span><span class="sxs-lookup"><span data-stu-id="5341b-231">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="5341b-232">Microsoft sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="5341b-232">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="5341b-233">[Microsoft sağlayıcısı özel işlevler](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) bulunan `SqlServer` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5341b-233">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="5341b-234">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-234">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="5341b-235">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-235">Output:</span></span>  
  
|<span data-ttu-id="5341b-236">EmailLen</span><span class="sxs-lookup"><span data-stu-id="5341b-236">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="5341b-237">27</span><span class="sxs-lookup"><span data-stu-id="5341b-237">27</span></span>|  
|<span data-ttu-id="5341b-238">27</span><span class="sxs-lookup"><span data-stu-id="5341b-238">27</span></span>|  
|<span data-ttu-id="5341b-239">26</span><span class="sxs-lookup"><span data-stu-id="5341b-239">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="5341b-240">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="5341b-240">Namespaces</span></span>  
 <span data-ttu-id="5341b-241">[KULLANARAK](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5341b-241">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="5341b-242">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-242">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="5341b-243">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-243">Output:</span></span>  
  
|<span data-ttu-id="5341b-244">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-244">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-245">aa</span><span class="sxs-lookup"><span data-stu-id="5341b-245">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="5341b-246">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="5341b-246">Paging</span></span>  
 <span data-ttu-id="5341b-247">Disk belleği bildirerek ifade edilen bir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) için alt yan tümceleri [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5341b-247">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="5341b-248">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-248">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="5341b-249">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-249">Output:</span></span>  
  
|<span data-ttu-id="5341b-250">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5341b-250">ID</span></span>|<span data-ttu-id="5341b-251">Ad</span><span class="sxs-lookup"><span data-stu-id="5341b-251">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="5341b-252">10</span><span class="sxs-lookup"><span data-stu-id="5341b-252">10</span></span>|<span data-ttu-id="5341b-253">Adina</span><span class="sxs-lookup"><span data-stu-id="5341b-253">Adina</span></span>|  
|<span data-ttu-id="5341b-254">11</span><span class="sxs-lookup"><span data-stu-id="5341b-254">11</span></span>|<span data-ttu-id="5341b-255">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="5341b-255">Agcaoili</span></span>|  
|<span data-ttu-id="5341b-256">12</span><span class="sxs-lookup"><span data-stu-id="5341b-256">12</span></span>|<span data-ttu-id="5341b-257">Aguilar</span><span class="sxs-lookup"><span data-stu-id="5341b-257">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="5341b-258">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="5341b-258">Grouping</span></span>  
 <span data-ttu-id="5341b-259">[GRUPLANDIRMA tarafından](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) bir sorgu tarafından döndürülen hangi nesnelere grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="5341b-259">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="5341b-260">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-260">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="5341b-261">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-261">Output:</span></span>  
  
|<span data-ttu-id="5341b-262">name</span><span class="sxs-lookup"><span data-stu-id="5341b-262">name</span></span>|  
|----------|  
|<span data-ttu-id="5341b-263">Tümünü Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="5341b-263">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5341b-264">ML Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="5341b-264">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5341b-265">HL Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="5341b-265">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="5341b-266">...</span><span class="sxs-lookup"><span data-stu-id="5341b-266">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="5341b-267">Gezinti</span><span class="sxs-lookup"><span data-stu-id="5341b-267">Navigation</span></span>  
 <span data-ttu-id="5341b-268">İlişkinin gezinme işleci bir varlıktan (Bitiş) (sona erdirmek için) başka bir ilişkisi üzerinden gitmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5341b-268">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="5341b-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ilişki türü tam olarak alır \<ad alanı >.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="5341b-269">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="5341b-270">Git başvuru dönüşleri\<T >, kardinalitesi sonlandırmak için 1'dir.</span><span class="sxs-lookup"><span data-stu-id="5341b-270">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="5341b-271">Varsa önem düzeyini sonlandırmak için n, koleksiyonu olan < Ref\<T >> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5341b-271">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="5341b-272">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-272">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="5341b-273">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-273">Output:</span></span>  
  
|<span data-ttu-id="5341b-274">AddressID</span><span class="sxs-lookup"><span data-stu-id="5341b-274">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="5341b-275">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-275">1</span></span>|  
|<span data-ttu-id="5341b-276">2</span><span class="sxs-lookup"><span data-stu-id="5341b-276">2</span></span>|  
|<span data-ttu-id="5341b-277">3</span><span class="sxs-lookup"><span data-stu-id="5341b-277">3</span></span>|  
|<span data-ttu-id="5341b-278">...</span><span class="sxs-lookup"><span data-stu-id="5341b-278">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="5341b-279">DEĞER VE SEÇ'İ SEÇİN</span><span class="sxs-lookup"><span data-stu-id="5341b-279">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="5341b-280">DEĞER SEÇİN</span><span class="sxs-lookup"><span data-stu-id="5341b-280">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5341b-281">SELECT VALUE yan tümcesi, örtük satır oluşturma atlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5341b-281">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="5341b-282">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="5341b-282">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="5341b-283">Böyle bir yan tümcesi kullanıldığında, öğelerin SELECT yan tümcesinde etrafında hiçbir satır sarmalayıcı oluşturulur ve istediğiniz şekle koleksiyonu, örneğin üretilebilir: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="5341b-283">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="5341b-284">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-284">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="5341b-285">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-285">Output:</span></span>  
  
|<span data-ttu-id="5341b-286">Ad</span><span class="sxs-lookup"><span data-stu-id="5341b-286">Name</span></span>|  
|----------|  
|<span data-ttu-id="5341b-287">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="5341b-287">Adjustable Race</span></span>|  
|<span data-ttu-id="5341b-288">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="5341b-288">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="5341b-289">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="5341b-289">AWC Logo Cap</span></span>|  
|<span data-ttu-id="5341b-290">...</span><span class="sxs-lookup"><span data-stu-id="5341b-290">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="5341b-291">SEÇ</span><span class="sxs-lookup"><span data-stu-id="5341b-291">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5341b-292">row oluşturucusunda rastgele satırları oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="5341b-292">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="5341b-293">SELECT yansıtma bir veya daha fazla öğeleri ve sonuçları bir veri kayıttaki alanları ile örneğin alır: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="5341b-293">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="5341b-294">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-294">Example:</span></span>  
  
 <span data-ttu-id="5341b-295">SELECT p.Name, p.ProductID AdventureWorksEntities.Product p çıktı olarak gelen:</span><span class="sxs-lookup"><span data-stu-id="5341b-295">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="5341b-296">Ad</span><span class="sxs-lookup"><span data-stu-id="5341b-296">Name</span></span>|<span data-ttu-id="5341b-297">ProductID</span><span class="sxs-lookup"><span data-stu-id="5341b-297">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="5341b-298">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="5341b-298">Adjustable Race</span></span>|<span data-ttu-id="5341b-299">1.</span><span class="sxs-lookup"><span data-stu-id="5341b-299">1</span></span>|  
|<span data-ttu-id="5341b-300">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="5341b-300">All-Purpose Bike Stand</span></span>|<span data-ttu-id="5341b-301">879</span><span class="sxs-lookup"><span data-stu-id="5341b-301">879</span></span>|  
|<span data-ttu-id="5341b-302">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="5341b-302">AWC Logo Cap</span></span>|<span data-ttu-id="5341b-303">712</span><span class="sxs-lookup"><span data-stu-id="5341b-303">712</span></span>|  
|<span data-ttu-id="5341b-304">...</span><span class="sxs-lookup"><span data-stu-id="5341b-304">...</span></span>|<span data-ttu-id="5341b-305">...</span><span class="sxs-lookup"><span data-stu-id="5341b-305">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="5341b-306">CASE İFADESİ</span><span class="sxs-lookup"><span data-stu-id="5341b-306">CASE EXPRESSION</span></span>  
 <span data-ttu-id="5341b-307">[Case ifadesi](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) sonucu belirlemek için Boolean ifadeler bir dizi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5341b-307">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="5341b-308">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5341b-308">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="5341b-309">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="5341b-309">Output:</span></span>  
  
|<span data-ttu-id="5341b-310">Değer</span><span class="sxs-lookup"><span data-stu-id="5341b-310">Value</span></span>|  
|-----------|  
|<span data-ttu-id="5341b-311">TRUE</span><span class="sxs-lookup"><span data-stu-id="5341b-311">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5341b-312">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5341b-312">See also</span></span>

- [<span data-ttu-id="5341b-313">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="5341b-313">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="5341b-314">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5341b-314">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
