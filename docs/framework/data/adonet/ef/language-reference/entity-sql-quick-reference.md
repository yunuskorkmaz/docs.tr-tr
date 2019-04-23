---
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: b4e3eaf8abd82b63fa2663b47f878ecfa9584897
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207077"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="626fe-102">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="626fe-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="626fe-103">Bu konu, hızlı başvuru sağlar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular.</span><span class="sxs-lookup"><span data-stu-id="626fe-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="626fe-104">Sorgular, bu konuda, AdventureWorks satış modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="626fe-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="626fe-105">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="626fe-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="626fe-106">Dize</span><span class="sxs-lookup"><span data-stu-id="626fe-106">String</span></span>  
 <span data-ttu-id="626fe-107">Unicode ve Unicode olmayan karakter dize değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="626fe-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="626fe-108">Unicode dizelerini ile n tanımlandıkları Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="626fe-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="626fe-109">Unicode olmayan dize sabitinin bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="626fe-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="626fe-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-110">Output:</span></span>  
  
|<span data-ttu-id="626fe-111">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-112">Merhaba</span><span class="sxs-lookup"><span data-stu-id="626fe-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="626fe-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="626fe-113">DateTime</span></span>  
 <span data-ttu-id="626fe-114">DateTime değişmez değerlerine, tarih ve saat bölümleri zorunludur.</span><span class="sxs-lookup"><span data-stu-id="626fe-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="626fe-115">Varsayılan değerler yoktur.</span><span class="sxs-lookup"><span data-stu-id="626fe-115">There are no default values.</span></span>  
  
 <span data-ttu-id="626fe-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="626fe-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-117">Output:</span></span>  
  
|<span data-ttu-id="626fe-118">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-119">12/25/2006 01:01: 00'DA</span><span class="sxs-lookup"><span data-stu-id="626fe-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="626fe-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="626fe-120">Integer</span></span>  
 <span data-ttu-id="626fe-121">Tamsayı sabit değerlerinde Int32 türünü olabilir (123) UInt32 (123U), Int64 (123L) ve UInt64 (123UL).</span><span class="sxs-lookup"><span data-stu-id="626fe-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="626fe-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="626fe-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-123">Output:</span></span>  
  
|<span data-ttu-id="626fe-124">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-125">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-125">1</span></span>|  
|<span data-ttu-id="626fe-126">2</span><span class="sxs-lookup"><span data-stu-id="626fe-126">2</span></span>|  
|<span data-ttu-id="626fe-127">3</span><span class="sxs-lookup"><span data-stu-id="626fe-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="626fe-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="626fe-128">Other</span></span>  
 <span data-ttu-id="626fe-129">Tarafından desteklenen diğer sabitler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olan GUID, ikili, kayan nokta/Double, Decimal, ve `null`.</span><span class="sxs-lookup"><span data-stu-id="626fe-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="626fe-130">Null değişmez değerlerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeldeki diğer her tür ile uyumlu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="626fe-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="626fe-131">Türü oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="626fe-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="626fe-132">ROW</span><span class="sxs-lookup"><span data-stu-id="626fe-132">ROW</span></span>  
 <span data-ttu-id="626fe-133">[Satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) bir anonim, yapısal olarak yazılmış (kayıt) değeri olarak oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="626fe-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="626fe-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="626fe-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-135">Output:</span></span>  
  
|<span data-ttu-id="626fe-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="626fe-136">ProductID</span></span>|<span data-ttu-id="626fe-137">Ad</span><span class="sxs-lookup"><span data-stu-id="626fe-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="626fe-138">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-138">1</span></span>|<span data-ttu-id="626fe-139">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="626fe-139">Adjustable Race</span></span>|  
|<span data-ttu-id="626fe-140">879</span><span class="sxs-lookup"><span data-stu-id="626fe-140">879</span></span>|<span data-ttu-id="626fe-141">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="626fe-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="626fe-142">712</span><span class="sxs-lookup"><span data-stu-id="626fe-142">712</span></span>|<span data-ttu-id="626fe-143">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="626fe-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="626fe-144">...</span><span class="sxs-lookup"><span data-stu-id="626fe-144">...</span></span>|<span data-ttu-id="626fe-145">...</span><span class="sxs-lookup"><span data-stu-id="626fe-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="626fe-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="626fe-146">MULTISET</span></span>  
 <span data-ttu-id="626fe-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) koleksiyonları gibi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="626fe-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="626fe-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="626fe-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="626fe-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="626fe-150">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-150">Output:</span></span>  
  
|<span data-ttu-id="626fe-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="626fe-151">ProductID</span></span>|<span data-ttu-id="626fe-152">Ad</span><span class="sxs-lookup"><span data-stu-id="626fe-152">Name</span></span>|<span data-ttu-id="626fe-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="626fe-153">ProductNumber</span></span>|<span data-ttu-id="626fe-154">…</span><span class="sxs-lookup"><span data-stu-id="626fe-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="626fe-155">842</span><span class="sxs-lookup"><span data-stu-id="626fe-155">842</span></span>|<span data-ttu-id="626fe-156">Yarış Panniers, büyük</span><span class="sxs-lookup"><span data-stu-id="626fe-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="626fe-157">PA T100</span><span class="sxs-lookup"><span data-stu-id="626fe-157">PA-T100</span></span>|<span data-ttu-id="626fe-158">…</span><span class="sxs-lookup"><span data-stu-id="626fe-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="626fe-159">Nesne</span><span class="sxs-lookup"><span data-stu-id="626fe-159">Object</span></span>  
 <span data-ttu-id="626fe-160">[Konstruktor Typu adlı](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) gibi kullanıcı tanımlı nesneler (adlandırılmış), yapıları `person("abc", 12)`.</span><span class="sxs-lookup"><span data-stu-id="626fe-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="626fe-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="626fe-162">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-162">Output:</span></span>  
  
|<span data-ttu-id="626fe-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="626fe-163">SalesOrderDetailID</span></span>|<span data-ttu-id="626fe-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="626fe-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="626fe-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="626fe-165">OrderQty</span></span>|<span data-ttu-id="626fe-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="626fe-166">ProductID</span></span>|<span data-ttu-id="626fe-167">...</span><span class="sxs-lookup"><span data-stu-id="626fe-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="626fe-168">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-168">1</span></span>|<span data-ttu-id="626fe-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="626fe-169">4911-403C-98</span></span>|<span data-ttu-id="626fe-170">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-170">1</span></span>|<span data-ttu-id="626fe-171">776</span><span class="sxs-lookup"><span data-stu-id="626fe-171">776</span></span>|<span data-ttu-id="626fe-172">...</span><span class="sxs-lookup"><span data-stu-id="626fe-172">...</span></span>|  
|<span data-ttu-id="626fe-173">2</span><span class="sxs-lookup"><span data-stu-id="626fe-173">2</span></span>|<span data-ttu-id="626fe-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="626fe-174">4911-403C-98</span></span>|<span data-ttu-id="626fe-175">3</span><span class="sxs-lookup"><span data-stu-id="626fe-175">3</span></span>|<span data-ttu-id="626fe-176">777</span><span class="sxs-lookup"><span data-stu-id="626fe-176">777</span></span>|<span data-ttu-id="626fe-177">...</span><span class="sxs-lookup"><span data-stu-id="626fe-177">...</span></span>|  
|<span data-ttu-id="626fe-178">...</span><span class="sxs-lookup"><span data-stu-id="626fe-178">...</span></span>|<span data-ttu-id="626fe-179">...</span><span class="sxs-lookup"><span data-stu-id="626fe-179">...</span></span>|<span data-ttu-id="626fe-180">...</span><span class="sxs-lookup"><span data-stu-id="626fe-180">...</span></span>|<span data-ttu-id="626fe-181">...</span><span class="sxs-lookup"><span data-stu-id="626fe-181">...</span></span>|<span data-ttu-id="626fe-182">...</span><span class="sxs-lookup"><span data-stu-id="626fe-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="626fe-183">Referanslar</span><span class="sxs-lookup"><span data-stu-id="626fe-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="626fe-184">REF</span><span class="sxs-lookup"><span data-stu-id="626fe-184">REF</span></span>  
 <span data-ttu-id="626fe-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="626fe-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="626fe-186">Örneğin, aşağıdaki sorgu, siparişler varlık kümesinde her sipariş varlığı için başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="626fe-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="626fe-187">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-187">Output:</span></span>  
  
|<span data-ttu-id="626fe-188">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-189">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-189">1</span></span>|  
|<span data-ttu-id="626fe-190">2</span><span class="sxs-lookup"><span data-stu-id="626fe-190">2</span></span>|  
|<span data-ttu-id="626fe-191">3</span><span class="sxs-lookup"><span data-stu-id="626fe-191">3</span></span>|  
|<span data-ttu-id="626fe-192">...</span><span class="sxs-lookup"><span data-stu-id="626fe-192">...</span></span>|  
  
 <span data-ttu-id="626fe-193">Aşağıdaki örnek, bir varlığın bir özelliğe erişmek için özelliği çıkarma işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="626fe-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="626fe-194">Özelliği ayıklama işleci kullanılmadığında otomatik olarak başvurusu kaldırılmış bir başvurudur.</span><span class="sxs-lookup"><span data-stu-id="626fe-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="626fe-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="626fe-196">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-196">Output:</span></span>  
  
|<span data-ttu-id="626fe-197">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-198">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="626fe-198">Adjustable Race</span></span>|  
|<span data-ttu-id="626fe-199">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="626fe-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="626fe-200">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="626fe-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="626fe-201">...</span><span class="sxs-lookup"><span data-stu-id="626fe-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="626fe-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="626fe-202">DEREF</span></span>  
 <span data-ttu-id="626fe-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="626fe-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="626fe-204">Örneğin, aşağıdaki sorguyu siparişler varlık kümesindeki her sipariş için sipariş varlıklara üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...</span><span class="sxs-lookup"><span data-stu-id="626fe-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="626fe-205">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="626fe-206">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-206">Output:</span></span>  
  
|<span data-ttu-id="626fe-207">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-208">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="626fe-208">Adjustable Race</span></span>|  
|<span data-ttu-id="626fe-209">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="626fe-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="626fe-210">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="626fe-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="626fe-211">...</span><span class="sxs-lookup"><span data-stu-id="626fe-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="626fe-212">CREATEREF VE ANAHTARI</span><span class="sxs-lookup"><span data-stu-id="626fe-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="626fe-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) bir anahtarını geçirerek başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="626fe-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="626fe-214">[ANAHTAR](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) ifade türü referansı ile anahtar bölümünü ayıklar.</span><span class="sxs-lookup"><span data-stu-id="626fe-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="626fe-215">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="626fe-216">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-216">Output:</span></span>  
  
|<span data-ttu-id="626fe-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="626fe-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="626fe-218">980</span><span class="sxs-lookup"><span data-stu-id="626fe-218">980</span></span>|  
|<span data-ttu-id="626fe-219">365</span><span class="sxs-lookup"><span data-stu-id="626fe-219">365</span></span>|  
|<span data-ttu-id="626fe-220">771</span><span class="sxs-lookup"><span data-stu-id="626fe-220">771</span></span>|  
|<span data-ttu-id="626fe-221">...</span><span class="sxs-lookup"><span data-stu-id="626fe-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="626fe-222">İşlevler</span><span class="sxs-lookup"><span data-stu-id="626fe-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="626fe-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="626fe-223">Canonical</span></span>  
 <span data-ttu-id="626fe-224">Ad alanı için [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Edm, olarak olduğundan `Edm.Length("string")`.</span><span class="sxs-lookup"><span data-stu-id="626fe-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="626fe-225">Kurallı işlev ile aynı ada sahip bir işlev içeren başka bir ad alanı içe sürece ad alanını belirtmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="626fe-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="626fe-226">İki ad alanı aynı işlevi varsa, kullanıcı özel tam adı gerekir.</span><span class="sxs-lookup"><span data-stu-id="626fe-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="626fe-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="626fe-228">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-228">Output:</span></span>  
  
|<span data-ttu-id="626fe-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="626fe-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="626fe-230">6</span><span class="sxs-lookup"><span data-stu-id="626fe-230">6</span></span>|  
|<span data-ttu-id="626fe-231">6</span><span class="sxs-lookup"><span data-stu-id="626fe-231">6</span></span>|  
|<span data-ttu-id="626fe-232">5</span><span class="sxs-lookup"><span data-stu-id="626fe-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="626fe-233">Microsoft sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="626fe-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="626fe-234">[Microsoft sağlayıcısı özel işlevler](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) bulunan `SqlServer` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="626fe-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="626fe-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="626fe-236">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-236">Output:</span></span>  
  
|<span data-ttu-id="626fe-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="626fe-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="626fe-238">27</span><span class="sxs-lookup"><span data-stu-id="626fe-238">27</span></span>|  
|<span data-ttu-id="626fe-239">27</span><span class="sxs-lookup"><span data-stu-id="626fe-239">27</span></span>|  
|<span data-ttu-id="626fe-240">26</span><span class="sxs-lookup"><span data-stu-id="626fe-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="626fe-241">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="626fe-241">Namespaces</span></span>  
 <span data-ttu-id="626fe-242">[KULLANARAK](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="626fe-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="626fe-243">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="626fe-244">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-244">Output:</span></span>  
  
|<span data-ttu-id="626fe-245">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-246">aa</span><span class="sxs-lookup"><span data-stu-id="626fe-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="626fe-247">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="626fe-247">Paging</span></span>  
 <span data-ttu-id="626fe-248">Disk belleği bildirerek ifade edilen bir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) için alt yan tümceleri [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="626fe-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="626fe-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="626fe-250">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-250">Output:</span></span>  
  
|<span data-ttu-id="626fe-251">Kimlik</span><span class="sxs-lookup"><span data-stu-id="626fe-251">ID</span></span>|<span data-ttu-id="626fe-252">Ad</span><span class="sxs-lookup"><span data-stu-id="626fe-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="626fe-253">10</span><span class="sxs-lookup"><span data-stu-id="626fe-253">10</span></span>|<span data-ttu-id="626fe-254">Adina</span><span class="sxs-lookup"><span data-stu-id="626fe-254">Adina</span></span>|  
|<span data-ttu-id="626fe-255">11</span><span class="sxs-lookup"><span data-stu-id="626fe-255">11</span></span>|<span data-ttu-id="626fe-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="626fe-256">Agcaoili</span></span>|  
|<span data-ttu-id="626fe-257">12</span><span class="sxs-lookup"><span data-stu-id="626fe-257">12</span></span>|<span data-ttu-id="626fe-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="626fe-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="626fe-259">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="626fe-259">Grouping</span></span>  
 <span data-ttu-id="626fe-260">[GRUPLANDIRMA tarafından](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) bir sorgu tarafından döndürülen hangi nesnelere grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="626fe-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="626fe-261">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="626fe-262">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-262">Output:</span></span>  
  
|<span data-ttu-id="626fe-263">name</span><span class="sxs-lookup"><span data-stu-id="626fe-263">name</span></span>|  
|----------|  
|<span data-ttu-id="626fe-264">Tümünü Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="626fe-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="626fe-265">ML Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="626fe-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="626fe-266">HL Sıradağlar bilgisayar bütünleştirilmiş kod</span><span class="sxs-lookup"><span data-stu-id="626fe-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="626fe-267">...</span><span class="sxs-lookup"><span data-stu-id="626fe-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="626fe-268">Gezinti</span><span class="sxs-lookup"><span data-stu-id="626fe-268">Navigation</span></span>  
 <span data-ttu-id="626fe-269">İlişkinin gezinme işleci bir varlıktan (Bitiş) (sona erdirmek için) başka bir ilişkisi üzerinden gitmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="626fe-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="626fe-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ilişki türü tam olarak alır \<ad alanı >.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="626fe-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="626fe-271">Git başvuru dönüşleri\<T >, kardinalitesi sonlandırmak için 1'dir.</span><span class="sxs-lookup"><span data-stu-id="626fe-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="626fe-272">Varsa önem düzeyini sonlandırmak için n, koleksiyonu olan < Ref\<T >> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="626fe-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="626fe-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="626fe-274">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-274">Output:</span></span>  
  
|<span data-ttu-id="626fe-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="626fe-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="626fe-276">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-276">1</span></span>|  
|<span data-ttu-id="626fe-277">2</span><span class="sxs-lookup"><span data-stu-id="626fe-277">2</span></span>|  
|<span data-ttu-id="626fe-278">3</span><span class="sxs-lookup"><span data-stu-id="626fe-278">3</span></span>|  
|<span data-ttu-id="626fe-279">...</span><span class="sxs-lookup"><span data-stu-id="626fe-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="626fe-280">DEĞER VE SEÇ'İ SEÇİN</span><span class="sxs-lookup"><span data-stu-id="626fe-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="626fe-281">DEĞER SEÇİN</span><span class="sxs-lookup"><span data-stu-id="626fe-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="626fe-282">SELECT VALUE yan tümcesi, örtük satır oluşturma atlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="626fe-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="626fe-283">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="626fe-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="626fe-284">Böyle bir yan tümcesi kullanıldığında, öğelerin SELECT yan tümcesinde etrafında hiçbir satır sarmalayıcı oluşturulur ve istediğiniz şekle koleksiyonu, örneğin üretilebilir: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="626fe-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="626fe-285">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="626fe-286">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-286">Output:</span></span>  
  
|<span data-ttu-id="626fe-287">Ad</span><span class="sxs-lookup"><span data-stu-id="626fe-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="626fe-288">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="626fe-288">Adjustable Race</span></span>|  
|<span data-ttu-id="626fe-289">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="626fe-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="626fe-290">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="626fe-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="626fe-291">...</span><span class="sxs-lookup"><span data-stu-id="626fe-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="626fe-292">SEÇ</span><span class="sxs-lookup"><span data-stu-id="626fe-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="626fe-293">row oluşturucusunda rastgele satırları oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="626fe-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="626fe-294">SELECT yansıtma bir veya daha fazla öğeleri ve sonuçları bir veri kayıttaki alanları ile örneğin alır: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="626fe-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="626fe-295">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-295">Example:</span></span>  
  
 <span data-ttu-id="626fe-296">SELECT p.Name, p.ProductID AdventureWorksEntities.Product p çıktı olarak gelen:</span><span class="sxs-lookup"><span data-stu-id="626fe-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="626fe-297">Ad</span><span class="sxs-lookup"><span data-stu-id="626fe-297">Name</span></span>|<span data-ttu-id="626fe-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="626fe-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="626fe-299">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="626fe-299">Adjustable Race</span></span>|<span data-ttu-id="626fe-300">1.</span><span class="sxs-lookup"><span data-stu-id="626fe-300">1</span></span>|  
|<span data-ttu-id="626fe-301">Çok amaçlı bisiklet bağımsız</span><span class="sxs-lookup"><span data-stu-id="626fe-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="626fe-302">879</span><span class="sxs-lookup"><span data-stu-id="626fe-302">879</span></span>|  
|<span data-ttu-id="626fe-303">AWC logolu Kasket</span><span class="sxs-lookup"><span data-stu-id="626fe-303">AWC Logo Cap</span></span>|<span data-ttu-id="626fe-304">712</span><span class="sxs-lookup"><span data-stu-id="626fe-304">712</span></span>|  
|<span data-ttu-id="626fe-305">...</span><span class="sxs-lookup"><span data-stu-id="626fe-305">...</span></span>|<span data-ttu-id="626fe-306">...</span><span class="sxs-lookup"><span data-stu-id="626fe-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="626fe-307">CASE İFADESİ</span><span class="sxs-lookup"><span data-stu-id="626fe-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="626fe-308">[Case ifadesi](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) sonucu belirlemek için Boolean ifadeler bir dizi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="626fe-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="626fe-309">Örnek:</span><span class="sxs-lookup"><span data-stu-id="626fe-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="626fe-310">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="626fe-310">Output:</span></span>  
  
|<span data-ttu-id="626fe-311">Değer</span><span class="sxs-lookup"><span data-stu-id="626fe-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="626fe-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="626fe-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="626fe-313">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="626fe-313">See also</span></span>

- [<span data-ttu-id="626fe-314">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="626fe-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="626fe-315">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="626fe-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
