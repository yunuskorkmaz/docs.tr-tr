---
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150356"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="0d01e-102">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0d01e-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="0d01e-103">Bu konu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgulara hızlı bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d01e-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="0d01e-104">Bu konudaki sorgular AdventureWorks Satış modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="0d01e-105">Sabit değerler</span><span class="sxs-lookup"><span data-stu-id="0d01e-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="0d01e-106">Dize</span><span class="sxs-lookup"><span data-stu-id="0d01e-106">String</span></span>  
 <span data-ttu-id="0d01e-107">Unicode ve unicode olmayan karakter dize literals vardır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="0d01e-108">Unicode dizeleri N ile hazırlanır. Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="0d01e-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="0d01e-109">Aşağıdaki bir Unicode olmayan dize literal bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="0d01e-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="0d01e-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-110">Output:</span></span>  
  
|<span data-ttu-id="0d01e-111">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-112">hello</span><span class="sxs-lookup"><span data-stu-id="0d01e-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="0d01e-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="0d01e-113">DateTime</span></span>  
 <span data-ttu-id="0d01e-114">DateTime literals'de hem tarih hem de saat bölümleri zorunludur.</span><span class="sxs-lookup"><span data-stu-id="0d01e-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="0d01e-115">Varsayılan değer yok.</span><span class="sxs-lookup"><span data-stu-id="0d01e-115">There are no default values.</span></span>  
  
 <span data-ttu-id="0d01e-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="0d01e-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-117">Output:</span></span>  
  
|<span data-ttu-id="0d01e-118">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-119">25.12.2006 01:01:00</span><span class="sxs-lookup"><span data-stu-id="0d01e-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="0d01e-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="0d01e-120">Integer</span></span>  
 <span data-ttu-id="0d01e-121">İnt32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="0d01e-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="0d01e-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-123">Output:</span></span>  
  
|<span data-ttu-id="0d01e-124">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-125">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-125">1</span></span>|  
|<span data-ttu-id="0d01e-126">2</span><span class="sxs-lookup"><span data-stu-id="0d01e-126">2</span></span>|  
|<span data-ttu-id="0d01e-127">3</span><span class="sxs-lookup"><span data-stu-id="0d01e-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="0d01e-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="0d01e-128">Other</span></span>  
 <span data-ttu-id="0d01e-129">Guid, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İkili, Float/Double, Ondalık ve `null`.</span><span class="sxs-lookup"><span data-stu-id="0d01e-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="0d01e-130">Null literals [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modelde her tür ile uyumlu olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="0d01e-131">Tip Yapıcılar</span><span class="sxs-lookup"><span data-stu-id="0d01e-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="0d01e-132">ROW</span><span class="sxs-lookup"><span data-stu-id="0d01e-132">ROW</span></span>  
 <span data-ttu-id="0d01e-133">[ROW,](row-entity-sql.md) anonim, yapısal olarak yazılan (kayıt) bir değer şunları yla inşa eder:`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="0d01e-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="0d01e-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="0d01e-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-135">Output:</span></span>  
  
|<span data-ttu-id="0d01e-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="0d01e-136">ProductID</span></span>|<span data-ttu-id="0d01e-137">Adı</span><span class="sxs-lookup"><span data-stu-id="0d01e-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="0d01e-138">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-138">1</span></span>|<span data-ttu-id="0d01e-139">Ayarlanabilir Yarış</span><span class="sxs-lookup"><span data-stu-id="0d01e-139">Adjustable Race</span></span>|  
|<span data-ttu-id="0d01e-140">879</span><span class="sxs-lookup"><span data-stu-id="0d01e-140">879</span></span>|<span data-ttu-id="0d01e-141">Çok Amaçlı Bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="0d01e-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="0d01e-142">712</span><span class="sxs-lookup"><span data-stu-id="0d01e-142">712</span></span>|<span data-ttu-id="0d01e-143">AWC Logo Kapağı</span><span class="sxs-lookup"><span data-stu-id="0d01e-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="0d01e-144">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-144">...</span></span>|<span data-ttu-id="0d01e-145">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="0d01e-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="0d01e-146">MULTISET</span></span>  
 <span data-ttu-id="0d01e-147">[MULTISET,](multiset-entity-sql.md) şu gibi koleksiyonlar inşa eder:</span><span class="sxs-lookup"><span data-stu-id="0d01e-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="0d01e-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="0d01e-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="0d01e-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="0d01e-150">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-150">Output:</span></span>  
  
|<span data-ttu-id="0d01e-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="0d01e-151">ProductID</span></span>|<span data-ttu-id="0d01e-152">Adı</span><span class="sxs-lookup"><span data-stu-id="0d01e-152">Name</span></span>|<span data-ttu-id="0d01e-153">Productnumber</span><span class="sxs-lookup"><span data-stu-id="0d01e-153">ProductNumber</span></span>|<span data-ttu-id="0d01e-154">…</span><span class="sxs-lookup"><span data-stu-id="0d01e-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="0d01e-155">842</span><span class="sxs-lookup"><span data-stu-id="0d01e-155">842</span></span>|<span data-ttu-id="0d01e-156">Touring-Panniers, Büyük</span><span class="sxs-lookup"><span data-stu-id="0d01e-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="0d01e-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="0d01e-157">PA-T100</span></span>|<span data-ttu-id="0d01e-158">…</span><span class="sxs-lookup"><span data-stu-id="0d01e-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="0d01e-159">Nesne</span><span class="sxs-lookup"><span data-stu-id="0d01e-159">Object</span></span>  
 <span data-ttu-id="0d01e-160">[Adlandırılmış Tür Oluşturucu](named-type-constructor-entity-sql.md) , kullanıcı tanımlı nesneler `person("abc", 12)`(adlandırılmış) yapıları gibi.</span><span class="sxs-lookup"><span data-stu-id="0d01e-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="0d01e-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="0d01e-162">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-162">Output:</span></span>  
  
|<span data-ttu-id="0d01e-163">Satış SiparişdetayID</span><span class="sxs-lookup"><span data-stu-id="0d01e-163">SalesOrderDetailID</span></span>|<span data-ttu-id="0d01e-164">TaşıyıcıTakip Numarası</span><span class="sxs-lookup"><span data-stu-id="0d01e-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="0d01e-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="0d01e-165">OrderQty</span></span>|<span data-ttu-id="0d01e-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="0d01e-166">ProductID</span></span>|<span data-ttu-id="0d01e-167">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="0d01e-168">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-168">1</span></span>|<span data-ttu-id="0d01e-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="0d01e-169">4911-403C-98</span></span>|<span data-ttu-id="0d01e-170">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-170">1</span></span>|<span data-ttu-id="0d01e-171">776</span><span class="sxs-lookup"><span data-stu-id="0d01e-171">776</span></span>|<span data-ttu-id="0d01e-172">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-172">...</span></span>|  
|<span data-ttu-id="0d01e-173">2</span><span class="sxs-lookup"><span data-stu-id="0d01e-173">2</span></span>|<span data-ttu-id="0d01e-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="0d01e-174">4911-403C-98</span></span>|<span data-ttu-id="0d01e-175">3</span><span class="sxs-lookup"><span data-stu-id="0d01e-175">3</span></span>|<span data-ttu-id="0d01e-176">777</span><span class="sxs-lookup"><span data-stu-id="0d01e-176">777</span></span>|<span data-ttu-id="0d01e-177">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-177">...</span></span>|  
|<span data-ttu-id="0d01e-178">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-178">...</span></span>|<span data-ttu-id="0d01e-179">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-179">...</span></span>|<span data-ttu-id="0d01e-180">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-180">...</span></span>|<span data-ttu-id="0d01e-181">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-181">...</span></span>|<span data-ttu-id="0d01e-182">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="0d01e-183">Başvurular</span><span class="sxs-lookup"><span data-stu-id="0d01e-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="0d01e-184">REF</span><span class="sxs-lookup"><span data-stu-id="0d01e-184">REF</span></span>  
 <span data-ttu-id="0d01e-185">[REF,](ref-entity-sql.md) varlık türü örneğine bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d01e-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="0d01e-186">Örneğin, aşağıdaki sorgu, Siparişler varlık kümesindeki her Sipariş varlığına başvuruları döndürür:</span><span class="sxs-lookup"><span data-stu-id="0d01e-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="0d01e-187">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-187">Output:</span></span>  
  
|<span data-ttu-id="0d01e-188">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-189">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-189">1</span></span>|  
|<span data-ttu-id="0d01e-190">2</span><span class="sxs-lookup"><span data-stu-id="0d01e-190">2</span></span>|  
|<span data-ttu-id="0d01e-191">3</span><span class="sxs-lookup"><span data-stu-id="0d01e-191">3</span></span>|  
|<span data-ttu-id="0d01e-192">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-192">...</span></span>|  
  
 <span data-ttu-id="0d01e-193">Aşağıdaki örnek, bir varlığın özelliğine erişmek için özellik ayıklama işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="0d01e-194">Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvurudan çıkarılatır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="0d01e-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="0d01e-196">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-196">Output:</span></span>  
  
|<span data-ttu-id="0d01e-197">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-198">Ayarlanabilir Yarış</span><span class="sxs-lookup"><span data-stu-id="0d01e-198">Adjustable Race</span></span>|  
|<span data-ttu-id="0d01e-199">Çok Amaçlı Bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="0d01e-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="0d01e-200">AWC Logo Kapağı</span><span class="sxs-lookup"><span data-stu-id="0d01e-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="0d01e-201">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="0d01e-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="0d01e-202">DEREF</span></span>  
 <span data-ttu-id="0d01e-203">[DEREF](deref-entity-sql.md) bir referans değerini dereferences ve bu dereference sonucu üretir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="0d01e-204">Örneğin, aşağıdaki sorgu, Siparişler varlık kümesindeki her Sipariş `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`için Sipariş varlıklarını üretir: ..</span><span class="sxs-lookup"><span data-stu-id="0d01e-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="0d01e-205">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="0d01e-206">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-206">Output:</span></span>  
  
|<span data-ttu-id="0d01e-207">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-208">Ayarlanabilir Yarış</span><span class="sxs-lookup"><span data-stu-id="0d01e-208">Adjustable Race</span></span>|  
|<span data-ttu-id="0d01e-209">Çok Amaçlı Bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="0d01e-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="0d01e-210">AWC Logo Kapağı</span><span class="sxs-lookup"><span data-stu-id="0d01e-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="0d01e-211">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="0d01e-212">CREATEREF VE ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="0d01e-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="0d01e-213">[CREATEREF](createref-entity-sql.md) bir anahtar geçen bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d01e-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="0d01e-214">[KEY,](key-entity-sql.md) bir ifadenin tür başvurusu yla anahtar kısmını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="0d01e-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="0d01e-215">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="0d01e-216">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-216">Output:</span></span>  
  
|<span data-ttu-id="0d01e-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="0d01e-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="0d01e-218">980</span><span class="sxs-lookup"><span data-stu-id="0d01e-218">980</span></span>|  
|<span data-ttu-id="0d01e-219">365</span><span class="sxs-lookup"><span data-stu-id="0d01e-219">365</span></span>|  
|<span data-ttu-id="0d01e-220">771</span><span class="sxs-lookup"><span data-stu-id="0d01e-220">771</span></span>|  
|<span data-ttu-id="0d01e-221">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="0d01e-222">İşlevler</span><span class="sxs-lookup"><span data-stu-id="0d01e-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="0d01e-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="0d01e-223">Canonical</span></span>  
 <span data-ttu-id="0d01e-224">[Kanonik işlevler](canonical-functions.md) için ad alanı Edm'dir. `Edm.Length("string")`</span><span class="sxs-lookup"><span data-stu-id="0d01e-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="0d01e-225">Kanonik bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içe aktarılmadığı sürece ad alanını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0d01e-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="0d01e-226">İki ad alanı aynı işleve sahipse, kullanıcı tam adı belirli yormalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="0d01e-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="0d01e-228">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-228">Output:</span></span>  
  
|<span data-ttu-id="0d01e-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="0d01e-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="0d01e-230">6</span><span class="sxs-lookup"><span data-stu-id="0d01e-230">6</span></span>|  
|<span data-ttu-id="0d01e-231">6</span><span class="sxs-lookup"><span data-stu-id="0d01e-231">6</span></span>|  
|<span data-ttu-id="0d01e-232">5</span><span class="sxs-lookup"><span data-stu-id="0d01e-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="0d01e-233">Microsoft Sağlayıcıya Özel</span><span class="sxs-lookup"><span data-stu-id="0d01e-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="0d01e-234">[Microsoft sağlayıcıya](../sqlclient-for-ef-functions.md) `SqlServer` özgü işlevler ad alanındadır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="0d01e-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="0d01e-236">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-236">Output:</span></span>  
  
|<span data-ttu-id="0d01e-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="0d01e-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="0d01e-238">27</span><span class="sxs-lookup"><span data-stu-id="0d01e-238">27</span></span>|  
|<span data-ttu-id="0d01e-239">27</span><span class="sxs-lookup"><span data-stu-id="0d01e-239">27</span></span>|  
|<span data-ttu-id="0d01e-240">26</span><span class="sxs-lookup"><span data-stu-id="0d01e-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="0d01e-241">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="0d01e-241">Namespaces</span></span>  
 <span data-ttu-id="0d01e-242">[USING,](using-entity-sql.md) sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="0d01e-243">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="0d01e-244">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-244">Output:</span></span>  
  
|<span data-ttu-id="0d01e-245">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-246">aa</span><span class="sxs-lookup"><span data-stu-id="0d01e-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="0d01e-247">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="0d01e-247">Paging</span></span>  
 <span data-ttu-id="0d01e-248">Sayfalama, [ORDER BY](order-by-entity-sql.md) yan tümcesine BIR [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt yan tümcesi belirtilerek ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="0d01e-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="0d01e-250">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-250">Output:</span></span>  
  
|<span data-ttu-id="0d01e-251">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0d01e-251">ID</span></span>|<span data-ttu-id="0d01e-252">Adı</span><span class="sxs-lookup"><span data-stu-id="0d01e-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="0d01e-253">10</span><span class="sxs-lookup"><span data-stu-id="0d01e-253">10</span></span>|<span data-ttu-id="0d01e-254">Adina</span><span class="sxs-lookup"><span data-stu-id="0d01e-254">Adina</span></span>|  
|<span data-ttu-id="0d01e-255">11</span><span class="sxs-lookup"><span data-stu-id="0d01e-255">11</span></span>|<span data-ttu-id="0d01e-256">Alkan</span><span class="sxs-lookup"><span data-stu-id="0d01e-256">Agcaoili</span></span>|  
|<span data-ttu-id="0d01e-257">12</span><span class="sxs-lookup"><span data-stu-id="0d01e-257">12</span></span>|<span data-ttu-id="0d01e-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="0d01e-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="0d01e-259">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="0d01e-259">Grouping</span></span>  
 <span data-ttu-id="0d01e-260">[GROUPING By,](group-by-entity-sql.md) sorgu[(SELECT](select-entity-sql.md)) ifadesi ile döndürülen nesnelerin yerleştirileceğini belirten gruplar dır.</span><span class="sxs-lookup"><span data-stu-id="0d01e-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="0d01e-261">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="0d01e-262">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-262">Output:</span></span>  
  
|<span data-ttu-id="0d01e-263">ad</span><span class="sxs-lookup"><span data-stu-id="0d01e-263">name</span></span>|  
|----------|  
|<span data-ttu-id="0d01e-264">LL Dağ Koltuk Montajı</span><span class="sxs-lookup"><span data-stu-id="0d01e-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="0d01e-265">ML Dağ Koltuk Montajı</span><span class="sxs-lookup"><span data-stu-id="0d01e-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="0d01e-266">HL Dağ Koltuk Montajı</span><span class="sxs-lookup"><span data-stu-id="0d01e-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="0d01e-267">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="0d01e-268">Gezinti</span><span class="sxs-lookup"><span data-stu-id="0d01e-268">Navigation</span></span>  
 <span data-ttu-id="0d01e-269">İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d01e-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="0d01e-270">[NAVIGATE,](navigate-entity-sql.md) ad alanı \<olarak nitelikli ilişki türünü> alır. \<ilişki türü adı>.</span><span class="sxs-lookup"><span data-stu-id="0d01e-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="0d01e-271">Gezinme,\<sonuna kadar olan ın kardinalliği 1 ise Ref T> döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d01e-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="0d01e-272">Sonuna kadar olan kardinallik n ise, Ref\<T>><Tahsilat ı iade edilir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="0d01e-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="0d01e-274">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-274">Output:</span></span>  
  
|<span data-ttu-id="0d01e-275">Addressıd</span><span class="sxs-lookup"><span data-stu-id="0d01e-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="0d01e-276">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-276">1</span></span>|  
|<span data-ttu-id="0d01e-277">2</span><span class="sxs-lookup"><span data-stu-id="0d01e-277">2</span></span>|  
|<span data-ttu-id="0d01e-278">3</span><span class="sxs-lookup"><span data-stu-id="0d01e-278">3</span></span>|  
|<span data-ttu-id="0d01e-279">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="0d01e-280">DEĞER SEÇIN VE SEÇIN</span><span class="sxs-lookup"><span data-stu-id="0d01e-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="0d01e-281">DEĞER SEÇ</span><span class="sxs-lookup"><span data-stu-id="0d01e-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="0d01e-282">örtülü satır yapımını atlamak için SELECT VALUE yan tümcesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d01e-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="0d01e-283">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="0d01e-284">Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin etrafına satır sarıcı oluşturulmaz `SELECT VALUE a`ve örneğin istenen şeklin bir koleksiyonu oluşturulabilir: .</span><span class="sxs-lookup"><span data-stu-id="0d01e-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="0d01e-285">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="0d01e-286">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-286">Output:</span></span>  
  
|<span data-ttu-id="0d01e-287">Adı</span><span class="sxs-lookup"><span data-stu-id="0d01e-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="0d01e-288">Ayarlanabilir Yarış</span><span class="sxs-lookup"><span data-stu-id="0d01e-288">Adjustable Race</span></span>|  
|<span data-ttu-id="0d01e-289">Çok Amaçlı Bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="0d01e-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="0d01e-290">AWC Logo Kapağı</span><span class="sxs-lookup"><span data-stu-id="0d01e-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="0d01e-291">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="0d01e-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="0d01e-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="0d01e-293">ayrıca satır oluşturucuya rasgele satırlar oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d01e-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="0d01e-294">SELECT projeksiyonda bir veya daha fazla öğe alır ve örneğin `SELECT a, b, c`alanları içeren bir veri kaydıyla sonuçlanır: .</span><span class="sxs-lookup"><span data-stu-id="0d01e-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="0d01e-295">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-295">Example:</span></span>  
  
 <span data-ttu-id="0d01e-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="0d01e-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="0d01e-297">Adı</span><span class="sxs-lookup"><span data-stu-id="0d01e-297">Name</span></span>|<span data-ttu-id="0d01e-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="0d01e-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="0d01e-299">Ayarlanabilir Yarış</span><span class="sxs-lookup"><span data-stu-id="0d01e-299">Adjustable Race</span></span>|<span data-ttu-id="0d01e-300">1</span><span class="sxs-lookup"><span data-stu-id="0d01e-300">1</span></span>|  
|<span data-ttu-id="0d01e-301">Çok Amaçlı Bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="0d01e-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="0d01e-302">879</span><span class="sxs-lookup"><span data-stu-id="0d01e-302">879</span></span>|  
|<span data-ttu-id="0d01e-303">AWC Logo Kapağı</span><span class="sxs-lookup"><span data-stu-id="0d01e-303">AWC Logo Cap</span></span>|<span data-ttu-id="0d01e-304">712</span><span class="sxs-lookup"><span data-stu-id="0d01e-304">712</span></span>|  
|<span data-ttu-id="0d01e-305">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-305">...</span></span>|<span data-ttu-id="0d01e-306">...</span><span class="sxs-lookup"><span data-stu-id="0d01e-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="0d01e-307">BÜYÜK/KÜÇÜK HARF İfadeSI</span><span class="sxs-lookup"><span data-stu-id="0d01e-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="0d01e-308">[Örnek durum ifadesi](case-entity-sql.md) sonucu belirlemek için Boolean ifadeler kümesini değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="0d01e-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="0d01e-309">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d01e-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="0d01e-310">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="0d01e-310">Output:</span></span>  
  
|<span data-ttu-id="0d01e-311">Değer</span><span class="sxs-lookup"><span data-stu-id="0d01e-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="0d01e-312">TRUE</span><span class="sxs-lookup"><span data-stu-id="0d01e-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d01e-313">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d01e-313">See also</span></span>

- [<span data-ttu-id="0d01e-314">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0d01e-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="0d01e-315">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d01e-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
