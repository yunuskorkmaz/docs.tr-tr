---
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251023"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="281e0-102">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="281e0-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="281e0-103">Bu konu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgulara hızlı bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="281e0-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="281e0-104">Bu konudaki sorgular AdventureWorks Sales Model ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="281e0-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="281e0-105">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="281e0-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="281e0-106">Dize</span><span class="sxs-lookup"><span data-stu-id="281e0-106">String</span></span>  
 <span data-ttu-id="281e0-107">Unicode ve Unicode olmayan karakter dizesi değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="281e0-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="281e0-108">Unicode dizeleri, N ile sona erer. Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="281e0-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="281e0-109">Aşağıda Unicode olmayan bir dize sabit değeri örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="281e0-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="281e0-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-110">Output:</span></span>  
  
|<span data-ttu-id="281e0-111">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-112">herkese</span><span class="sxs-lookup"><span data-stu-id="281e0-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="281e0-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="281e0-113">DateTime</span></span>  
 <span data-ttu-id="281e0-114">DateTime değişmez değerlerinde hem tarih hem de saat kısımları zorunludur.</span><span class="sxs-lookup"><span data-stu-id="281e0-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="281e0-115">Varsayılan değer yok.</span><span class="sxs-lookup"><span data-stu-id="281e0-115">There are no default values.</span></span>  
  
 <span data-ttu-id="281e0-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="281e0-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-117">Output:</span></span>  
  
|<span data-ttu-id="281e0-118">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-119">12/25/2006 1:01:00</span><span class="sxs-lookup"><span data-stu-id="281e0-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="281e0-120">Integer</span><span class="sxs-lookup"><span data-stu-id="281e0-120">Integer</span></span>  
 <span data-ttu-id="281e0-121">Tamsayı sabit değerleri Int32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="281e0-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="281e0-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="281e0-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-123">Output:</span></span>  
  
|<span data-ttu-id="281e0-124">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-125">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-125">1</span></span>|  
|<span data-ttu-id="281e0-126">2</span><span class="sxs-lookup"><span data-stu-id="281e0-126">2</span></span>|  
|<span data-ttu-id="281e0-127">3</span><span class="sxs-lookup"><span data-stu-id="281e0-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="281e0-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="281e0-128">Other</span></span>  
 <span data-ttu-id="281e0-129">Tarafından [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenen diğer sabit değerler GUID, ikili, float/double, Decimal ve `null`' dir.</span><span class="sxs-lookup"><span data-stu-id="281e0-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="281e0-130">İçindeki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] null sabit değerler, kavramsal modeldeki diğer her türle uyumlu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="281e0-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="281e0-131">Tür oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="281e0-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="281e0-132">ROW</span><span class="sxs-lookup"><span data-stu-id="281e0-132">ROW</span></span>  
 <span data-ttu-id="281e0-133">[Satır](row-entity-sql.md) , içinde olduğu gibi anonim, yapısal olarak yazılmış bir (kayıt) değeri oluşturur:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="281e0-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="281e0-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="281e0-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-135">Output:</span></span>  
  
|<span data-ttu-id="281e0-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="281e0-136">ProductID</span></span>|<span data-ttu-id="281e0-137">Ad</span><span class="sxs-lookup"><span data-stu-id="281e0-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="281e0-138">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-138">1</span></span>|<span data-ttu-id="281e0-139">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="281e0-139">Adjustable Race</span></span>|  
|<span data-ttu-id="281e0-140">879</span><span class="sxs-lookup"><span data-stu-id="281e0-140">879</span></span>|<span data-ttu-id="281e0-141">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="281e0-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="281e0-142">712</span><span class="sxs-lookup"><span data-stu-id="281e0-142">712</span></span>|<span data-ttu-id="281e0-143">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="281e0-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="281e0-144">...</span><span class="sxs-lookup"><span data-stu-id="281e0-144">...</span></span>|<span data-ttu-id="281e0-145">...</span><span class="sxs-lookup"><span data-stu-id="281e0-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="281e0-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="281e0-146">MULTISET</span></span>  
 <span data-ttu-id="281e0-147">[Çoklu küme](multiset-entity-sql.md) yapıları, örneğin:</span><span class="sxs-lookup"><span data-stu-id="281e0-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="281e0-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="281e0-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="281e0-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="281e0-150">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-150">Output:</span></span>  
  
|<span data-ttu-id="281e0-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="281e0-151">ProductID</span></span>|<span data-ttu-id="281e0-152">Ad</span><span class="sxs-lookup"><span data-stu-id="281e0-152">Name</span></span>|<span data-ttu-id="281e0-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="281e0-153">ProductNumber</span></span>|<span data-ttu-id="281e0-154">…</span><span class="sxs-lookup"><span data-stu-id="281e0-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="281e0-155">842</span><span class="sxs-lookup"><span data-stu-id="281e0-155">842</span></span>|<span data-ttu-id="281e0-156">Touring-Panniler, büyük</span><span class="sxs-lookup"><span data-stu-id="281e0-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="281e0-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="281e0-157">PA-T100</span></span>|<span data-ttu-id="281e0-158">…</span><span class="sxs-lookup"><span data-stu-id="281e0-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="281e0-159">Nesne</span><span class="sxs-lookup"><span data-stu-id="281e0-159">Object</span></span>  
 <span data-ttu-id="281e0-160">[Adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md) (adlandırılmış), `person("abc", 12)`gibi Kullanıcı tanımlı nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="281e0-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="281e0-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="281e0-162">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-162">Output:</span></span>  
  
|<span data-ttu-id="281e0-163">Salesorderdetailıd</span><span class="sxs-lookup"><span data-stu-id="281e0-163">SalesOrderDetailID</span></span>|<span data-ttu-id="281e0-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="281e0-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="281e0-165">Ordermik</span><span class="sxs-lookup"><span data-stu-id="281e0-165">OrderQty</span></span>|<span data-ttu-id="281e0-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="281e0-166">ProductID</span></span>|<span data-ttu-id="281e0-167">...</span><span class="sxs-lookup"><span data-stu-id="281e0-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="281e0-168">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-168">1</span></span>|<span data-ttu-id="281e0-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="281e0-169">4911-403C-98</span></span>|<span data-ttu-id="281e0-170">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-170">1</span></span>|<span data-ttu-id="281e0-171">776</span><span class="sxs-lookup"><span data-stu-id="281e0-171">776</span></span>|<span data-ttu-id="281e0-172">...</span><span class="sxs-lookup"><span data-stu-id="281e0-172">...</span></span>|  
|<span data-ttu-id="281e0-173">2</span><span class="sxs-lookup"><span data-stu-id="281e0-173">2</span></span>|<span data-ttu-id="281e0-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="281e0-174">4911-403C-98</span></span>|<span data-ttu-id="281e0-175">3</span><span class="sxs-lookup"><span data-stu-id="281e0-175">3</span></span>|<span data-ttu-id="281e0-176">777</span><span class="sxs-lookup"><span data-stu-id="281e0-176">777</span></span>|<span data-ttu-id="281e0-177">...</span><span class="sxs-lookup"><span data-stu-id="281e0-177">...</span></span>|  
|<span data-ttu-id="281e0-178">...</span><span class="sxs-lookup"><span data-stu-id="281e0-178">...</span></span>|<span data-ttu-id="281e0-179">...</span><span class="sxs-lookup"><span data-stu-id="281e0-179">...</span></span>|<span data-ttu-id="281e0-180">...</span><span class="sxs-lookup"><span data-stu-id="281e0-180">...</span></span>|<span data-ttu-id="281e0-181">...</span><span class="sxs-lookup"><span data-stu-id="281e0-181">...</span></span>|<span data-ttu-id="281e0-182">...</span><span class="sxs-lookup"><span data-stu-id="281e0-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="281e0-183">Referanslar</span><span class="sxs-lookup"><span data-stu-id="281e0-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="281e0-184">REF</span><span class="sxs-lookup"><span data-stu-id="281e0-184">REF</span></span>  
 <span data-ttu-id="281e0-185">[Ref](ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="281e0-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="281e0-186">Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir order varlığına başvuruları döndürür:</span><span class="sxs-lookup"><span data-stu-id="281e0-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="281e0-187">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-187">Output:</span></span>  
  
|<span data-ttu-id="281e0-188">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-189">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-189">1</span></span>|  
|<span data-ttu-id="281e0-190">2</span><span class="sxs-lookup"><span data-stu-id="281e0-190">2</span></span>|  
|<span data-ttu-id="281e0-191">3</span><span class="sxs-lookup"><span data-stu-id="281e0-191">3</span></span>|  
|<span data-ttu-id="281e0-192">...</span><span class="sxs-lookup"><span data-stu-id="281e0-192">...</span></span>|  
  
 <span data-ttu-id="281e0-193">Aşağıdaki örnek, bir varlığın bir özelliğine erişmek için özellik ayıklama işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="281e0-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="281e0-194">Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="281e0-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="281e0-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="281e0-196">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-196">Output:</span></span>  
  
|<span data-ttu-id="281e0-197">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-198">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="281e0-198">Adjustable Race</span></span>|  
|<span data-ttu-id="281e0-199">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="281e0-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="281e0-200">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="281e0-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="281e0-201">...</span><span class="sxs-lookup"><span data-stu-id="281e0-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="281e0-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="281e0-202">DEREF</span></span>  
 <span data-ttu-id="281e0-203">[Deref](deref-entity-sql.md) bir başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="281e0-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="281e0-204">Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir sıra için sıra varlıklarını üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span><span class="sxs-lookup"><span data-stu-id="281e0-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="281e0-205">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="281e0-206">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-206">Output:</span></span>  
  
|<span data-ttu-id="281e0-207">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-208">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="281e0-208">Adjustable Race</span></span>|  
|<span data-ttu-id="281e0-209">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="281e0-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="281e0-210">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="281e0-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="281e0-211">...</span><span class="sxs-lookup"><span data-stu-id="281e0-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="281e0-212">CREATEREF VE ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="281e0-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="281e0-213">[CreateRef](createref-entity-sql.md) anahtar geçirerek bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="281e0-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="281e0-214">[Anahtar](key-entity-sql.md) , tür başvurusu olan bir ifadenin anahtar kısmını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="281e0-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="281e0-215">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="281e0-216">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-216">Output:</span></span>  
  
|<span data-ttu-id="281e0-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="281e0-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="281e0-218">980</span><span class="sxs-lookup"><span data-stu-id="281e0-218">980</span></span>|  
|<span data-ttu-id="281e0-219">365</span><span class="sxs-lookup"><span data-stu-id="281e0-219">365</span></span>|  
|<span data-ttu-id="281e0-220">771</span><span class="sxs-lookup"><span data-stu-id="281e0-220">771</span></span>|  
|<span data-ttu-id="281e0-221">...</span><span class="sxs-lookup"><span data-stu-id="281e0-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="281e0-222">İşlevler</span><span class="sxs-lookup"><span data-stu-id="281e0-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="281e0-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="281e0-223">Canonical</span></span>  
 <span data-ttu-id="281e0-224">[Kurallı işlevler](canonical-functions.md) için ad alanı, içinde `Edm.Length("string")`olduğu gibi EDM 'dir.</span><span class="sxs-lookup"><span data-stu-id="281e0-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="281e0-225">Kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmadığı sürece, ad alanını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="281e0-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="281e0-226">İki ad alanı aynı işleve sahip ise, Kullanıcı tam adı özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="281e0-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="281e0-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="281e0-228">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-228">Output:</span></span>  
  
|<span data-ttu-id="281e0-229">Ad uzunluğu</span><span class="sxs-lookup"><span data-stu-id="281e0-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="281e0-230">6</span><span class="sxs-lookup"><span data-stu-id="281e0-230">6</span></span>|  
|<span data-ttu-id="281e0-231">6</span><span class="sxs-lookup"><span data-stu-id="281e0-231">6</span></span>|  
|<span data-ttu-id="281e0-232">5</span><span class="sxs-lookup"><span data-stu-id="281e0-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="281e0-233">Microsoft sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="281e0-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="281e0-234">[Microsoft sağlayıcıya özgü işlevler](../sqlclient-for-ef-functions.md) `SqlServer` ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="281e0-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="281e0-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="281e0-236">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-236">Output:</span></span>  
  
|<span data-ttu-id="281e0-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="281e0-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="281e0-238">27</span><span class="sxs-lookup"><span data-stu-id="281e0-238">27</span></span>|  
|<span data-ttu-id="281e0-239">27</span><span class="sxs-lookup"><span data-stu-id="281e0-239">27</span></span>|  
|<span data-ttu-id="281e0-240">26</span><span class="sxs-lookup"><span data-stu-id="281e0-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="281e0-241">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="281e0-241">Namespaces</span></span>  
 <span data-ttu-id="281e0-242">[USING](using-entity-sql.md) , bir sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="281e0-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="281e0-243">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="281e0-244">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-244">Output:</span></span>  
  
|<span data-ttu-id="281e0-245">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-246">aa</span><span class="sxs-lookup"><span data-stu-id="281e0-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="281e0-247">Disk Belleği</span><span class="sxs-lookup"><span data-stu-id="281e0-247">Paging</span></span>  
 <span data-ttu-id="281e0-248">Sayfalama, bir [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümceleri [order by](order-by-entity-sql.md) yan tümcesine bildirerek ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="281e0-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="281e0-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="281e0-250">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-250">Output:</span></span>  
  
|<span data-ttu-id="281e0-251">ID</span><span class="sxs-lookup"><span data-stu-id="281e0-251">ID</span></span>|<span data-ttu-id="281e0-252">Ad</span><span class="sxs-lookup"><span data-stu-id="281e0-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="281e0-253">10</span><span class="sxs-lookup"><span data-stu-id="281e0-253">10</span></span>|<span data-ttu-id="281e0-254">Adina</span><span class="sxs-lookup"><span data-stu-id="281e0-254">Adina</span></span>|  
|<span data-ttu-id="281e0-255">11</span><span class="sxs-lookup"><span data-stu-id="281e0-255">11</span></span>|<span data-ttu-id="281e0-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="281e0-256">Agcaoili</span></span>|  
|<span data-ttu-id="281e0-257">12</span><span class="sxs-lookup"><span data-stu-id="281e0-257">12</span></span>|<span data-ttu-id="281e0-258">Agular</span><span class="sxs-lookup"><span data-stu-id="281e0-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="281e0-259">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="281e0-259">Grouping</span></span>  
 <span data-ttu-id="281e0-260">[Gruplandırma ölçütü](group-by-entity-sql.md) , sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirler.</span><span class="sxs-lookup"><span data-stu-id="281e0-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="281e0-261">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="281e0-262">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-262">Output:</span></span>  
  
|<span data-ttu-id="281e0-263">name</span><span class="sxs-lookup"><span data-stu-id="281e0-263">name</span></span>|  
|----------|  
|<span data-ttu-id="281e0-264">LL Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="281e0-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="281e0-265">ML Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="281e0-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="281e0-266">HL Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="281e0-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="281e0-267">...</span><span class="sxs-lookup"><span data-stu-id="281e0-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="281e0-268">Gezinti</span><span class="sxs-lookup"><span data-stu-id="281e0-268">Navigation</span></span>  
 <span data-ttu-id="281e0-269">İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="281e0-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="281e0-270">[Git](navigate-entity-sql.md) > ad alanı olarak \<nitelenmiş ilişki türünü alır.\< ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="281e0-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="281e0-271">To end 'in\<kardinalite değeri 1 ise, git, ref T > döndürür.</span><span class="sxs-lookup"><span data-stu-id="281e0-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="281e0-272">To end 'in kardinalitei n ise, < ref\<T > > koleksiyonu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="281e0-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="281e0-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="281e0-274">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-274">Output:</span></span>  
  
|<span data-ttu-id="281e0-275">Adres SID 'si</span><span class="sxs-lookup"><span data-stu-id="281e0-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="281e0-276">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-276">1</span></span>|  
|<span data-ttu-id="281e0-277">2</span><span class="sxs-lookup"><span data-stu-id="281e0-277">2</span></span>|  
|<span data-ttu-id="281e0-278">3</span><span class="sxs-lookup"><span data-stu-id="281e0-278">3</span></span>|  
|<span data-ttu-id="281e0-279">...</span><span class="sxs-lookup"><span data-stu-id="281e0-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="281e0-280">DEĞER ' I SEÇIN VE</span><span class="sxs-lookup"><span data-stu-id="281e0-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="281e0-281">DEĞER SEÇIN</span><span class="sxs-lookup"><span data-stu-id="281e0-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="281e0-282">örtük satır oluşturmayı atlamak için değer Seç yan tümcesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="281e0-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="281e0-283">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="281e0-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="281e0-284">Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin çevresinde bir satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretilebilinir, örneğin: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="281e0-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="281e0-285">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="281e0-286">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-286">Output:</span></span>  
  
|<span data-ttu-id="281e0-287">Ad</span><span class="sxs-lookup"><span data-stu-id="281e0-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="281e0-288">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="281e0-288">Adjustable Race</span></span>|  
|<span data-ttu-id="281e0-289">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="281e0-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="281e0-290">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="281e0-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="281e0-291">...</span><span class="sxs-lookup"><span data-stu-id="281e0-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="281e0-292">SEÇ</span><span class="sxs-lookup"><span data-stu-id="281e0-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="281e0-293">Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="281e0-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="281e0-294">Projeksiyde bir veya daha fazla öğe alır ve alanlar içeren bir veri kaydıyla sonuçlanır, örneğin: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="281e0-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="281e0-295">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-295">Example:</span></span>  
  
 <span data-ttu-id="281e0-296">AdventureWorksEntities. Product öğesinden p çıkışı olarak p.Name, p. ProductID 'yi SEÇIN:</span><span class="sxs-lookup"><span data-stu-id="281e0-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="281e0-297">Ad</span><span class="sxs-lookup"><span data-stu-id="281e0-297">Name</span></span>|<span data-ttu-id="281e0-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="281e0-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="281e0-299">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="281e0-299">Adjustable Race</span></span>|<span data-ttu-id="281e0-300">1\.</span><span class="sxs-lookup"><span data-stu-id="281e0-300">1</span></span>|  
|<span data-ttu-id="281e0-301">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="281e0-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="281e0-302">879</span><span class="sxs-lookup"><span data-stu-id="281e0-302">879</span></span>|  
|<span data-ttu-id="281e0-303">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="281e0-303">AWC Logo Cap</span></span>|<span data-ttu-id="281e0-304">712</span><span class="sxs-lookup"><span data-stu-id="281e0-304">712</span></span>|  
|<span data-ttu-id="281e0-305">...</span><span class="sxs-lookup"><span data-stu-id="281e0-305">...</span></span>|<span data-ttu-id="281e0-306">...</span><span class="sxs-lookup"><span data-stu-id="281e0-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="281e0-307">CASE IFADESI</span><span class="sxs-lookup"><span data-stu-id="281e0-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="281e0-308">[Case ifadesi](case-entity-sql.md) sonucu belirleyecek bir dizi Boole ifadesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="281e0-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="281e0-309">Örnek:</span><span class="sxs-lookup"><span data-stu-id="281e0-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="281e0-310">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="281e0-310">Output:</span></span>  
  
|<span data-ttu-id="281e0-311">Değer</span><span class="sxs-lookup"><span data-stu-id="281e0-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="281e0-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="281e0-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="281e0-313">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="281e0-313">See also</span></span>

- [<span data-ttu-id="281e0-314">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="281e0-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="281e0-315">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="281e0-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
