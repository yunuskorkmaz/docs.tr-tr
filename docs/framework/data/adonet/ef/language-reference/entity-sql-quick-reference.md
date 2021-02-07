---
description: 'Daha fazla bilgi edinin: Entity SQL hızlı başvuru'
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: ddac48bece1f0e9df737db295d4d028529ea290f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724563"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="29879-103">Entity SQL Hızlı Başvurusu</span><span class="sxs-lookup"><span data-stu-id="29879-103">Entity SQL Quick Reference</span></span>

<span data-ttu-id="29879-104">Bu konu, sorgulara hızlı bir başvuru sağlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="29879-104">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="29879-105">Bu konudaki sorgular AdventureWorks Sales Model ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="29879-105">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="29879-106">Değişmez Değerler</span><span class="sxs-lookup"><span data-stu-id="29879-106">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="29879-107">Dize</span><span class="sxs-lookup"><span data-stu-id="29879-107">String</span></span>  

 <span data-ttu-id="29879-108">Unicode ve Unicode olmayan karakter dizesi değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="29879-108">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="29879-109">Unicode dizeleri, N ile sona erer. Örneğin, `N'hello'` .</span><span class="sxs-lookup"><span data-stu-id="29879-109">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="29879-110">Aşağıda Unicode olmayan bir dize sabit değeri örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29879-110">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="29879-111">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-111">Output:</span></span>  
  
|<span data-ttu-id="29879-112">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-112">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-113">hello</span><span class="sxs-lookup"><span data-stu-id="29879-113">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="29879-114">DateTime</span><span class="sxs-lookup"><span data-stu-id="29879-114">DateTime</span></span>  

 <span data-ttu-id="29879-115">DateTime değişmez değerlerinde hem tarih hem de saat kısımları zorunludur.</span><span class="sxs-lookup"><span data-stu-id="29879-115">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="29879-116">Varsayılan değer yok.</span><span class="sxs-lookup"><span data-stu-id="29879-116">There are no default values.</span></span>  
  
 <span data-ttu-id="29879-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-117">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="29879-118">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-118">Output:</span></span>  
  
|<span data-ttu-id="29879-119">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-119">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-120">12/25/2006 1:01:00</span><span class="sxs-lookup"><span data-stu-id="29879-120">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="29879-121">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="29879-121">Integer</span></span>  

 <span data-ttu-id="29879-122">Tamsayı sabit değerleri Int32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="29879-122">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="29879-123">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-123">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="29879-124">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-124">Output:</span></span>  
  
|<span data-ttu-id="29879-125">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-125">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-126">1</span><span class="sxs-lookup"><span data-stu-id="29879-126">1</span></span>|  
|<span data-ttu-id="29879-127">2</span><span class="sxs-lookup"><span data-stu-id="29879-127">2</span></span>|  
|<span data-ttu-id="29879-128">3</span><span class="sxs-lookup"><span data-stu-id="29879-128">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="29879-129">Diğer</span><span class="sxs-lookup"><span data-stu-id="29879-129">Other</span></span>  

 <span data-ttu-id="29879-130">Tarafından desteklenen diğer sabit değerler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] GUID, ikili, float/double, Decimal ve ' dir `null` .</span><span class="sxs-lookup"><span data-stu-id="29879-130">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="29879-131">İçindeki null sabit değerler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , kavramsal modeldeki diğer her türle uyumlu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="29879-131">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="29879-132">Tür oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="29879-132">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="29879-133">ROW</span><span class="sxs-lookup"><span data-stu-id="29879-133">ROW</span></span>  

 <span data-ttu-id="29879-134">[Satır](row-entity-sql.md) , içinde olduğu gibi anonim, yapısal olarak yazılmış bir (kayıt) değeri oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="29879-134">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="29879-135">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-135">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="29879-136">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-136">Output:</span></span>  
  
|<span data-ttu-id="29879-137">ProductID</span><span class="sxs-lookup"><span data-stu-id="29879-137">ProductID</span></span>|<span data-ttu-id="29879-138">Name</span><span class="sxs-lookup"><span data-stu-id="29879-138">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="29879-139">1</span><span class="sxs-lookup"><span data-stu-id="29879-139">1</span></span>|<span data-ttu-id="29879-140">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="29879-140">Adjustable Race</span></span>|  
|<span data-ttu-id="29879-141">879</span><span class="sxs-lookup"><span data-stu-id="29879-141">879</span></span>|<span data-ttu-id="29879-142">All-Purpose bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="29879-142">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="29879-143">712</span><span class="sxs-lookup"><span data-stu-id="29879-143">712</span></span>|<span data-ttu-id="29879-144">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="29879-144">AWC Logo Cap</span></span>|  
|<span data-ttu-id="29879-145">...</span><span class="sxs-lookup"><span data-stu-id="29879-145">...</span></span>|<span data-ttu-id="29879-146">...</span><span class="sxs-lookup"><span data-stu-id="29879-146">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="29879-147">MULTISET</span><span class="sxs-lookup"><span data-stu-id="29879-147">MULTISET</span></span>  

 <span data-ttu-id="29879-148">[Çoklu küme](multiset-entity-sql.md) yapıları, örneğin:</span><span class="sxs-lookup"><span data-stu-id="29879-148">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="29879-149">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="29879-149">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="29879-150">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-150">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="29879-151">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-151">Output:</span></span>  
  
|<span data-ttu-id="29879-152">ProductID</span><span class="sxs-lookup"><span data-stu-id="29879-152">ProductID</span></span>|<span data-ttu-id="29879-153">Name</span><span class="sxs-lookup"><span data-stu-id="29879-153">Name</span></span>|<span data-ttu-id="29879-154">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="29879-154">ProductNumber</span></span>|<span data-ttu-id="29879-155">…</span><span class="sxs-lookup"><span data-stu-id="29879-155">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="29879-156">842</span><span class="sxs-lookup"><span data-stu-id="29879-156">842</span></span>|<span data-ttu-id="29879-157">Touring-Panniler, büyük</span><span class="sxs-lookup"><span data-stu-id="29879-157">Touring-Panniers, Large</span></span>|<span data-ttu-id="29879-158">PA-T100</span><span class="sxs-lookup"><span data-stu-id="29879-158">PA-T100</span></span>|<span data-ttu-id="29879-159">…</span><span class="sxs-lookup"><span data-stu-id="29879-159">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="29879-160">Nesne</span><span class="sxs-lookup"><span data-stu-id="29879-160">Object</span></span>  

 <span data-ttu-id="29879-161">[Adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md) (adlandırılmış), gibi Kullanıcı tanımlı nesneler oluşturur `person("abc", 12)` .</span><span class="sxs-lookup"><span data-stu-id="29879-161">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="29879-162">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-162">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 <span data-ttu-id="29879-163">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-163">Output:</span></span>  
  
|<span data-ttu-id="29879-164">Salesorderdetailıd</span><span class="sxs-lookup"><span data-stu-id="29879-164">SalesOrderDetailID</span></span>|<span data-ttu-id="29879-165">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="29879-165">CarrierTrackingNumber</span></span>|<span data-ttu-id="29879-166">OrderQty</span><span class="sxs-lookup"><span data-stu-id="29879-166">OrderQty</span></span>|<span data-ttu-id="29879-167">ProductID</span><span class="sxs-lookup"><span data-stu-id="29879-167">ProductID</span></span>|<span data-ttu-id="29879-168">...</span><span class="sxs-lookup"><span data-stu-id="29879-168">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="29879-169">1</span><span class="sxs-lookup"><span data-stu-id="29879-169">1</span></span>|<span data-ttu-id="29879-170">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="29879-170">4911-403C-98</span></span>|<span data-ttu-id="29879-171">1</span><span class="sxs-lookup"><span data-stu-id="29879-171">1</span></span>|<span data-ttu-id="29879-172">776</span><span class="sxs-lookup"><span data-stu-id="29879-172">776</span></span>|<span data-ttu-id="29879-173">...</span><span class="sxs-lookup"><span data-stu-id="29879-173">...</span></span>|  
|<span data-ttu-id="29879-174">2</span><span class="sxs-lookup"><span data-stu-id="29879-174">2</span></span>|<span data-ttu-id="29879-175">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="29879-175">4911-403C-98</span></span>|<span data-ttu-id="29879-176">3</span><span class="sxs-lookup"><span data-stu-id="29879-176">3</span></span>|<span data-ttu-id="29879-177">777</span><span class="sxs-lookup"><span data-stu-id="29879-177">777</span></span>|<span data-ttu-id="29879-178">...</span><span class="sxs-lookup"><span data-stu-id="29879-178">...</span></span>|  
|<span data-ttu-id="29879-179">...</span><span class="sxs-lookup"><span data-stu-id="29879-179">...</span></span>|<span data-ttu-id="29879-180">...</span><span class="sxs-lookup"><span data-stu-id="29879-180">...</span></span>|<span data-ttu-id="29879-181">...</span><span class="sxs-lookup"><span data-stu-id="29879-181">...</span></span>|<span data-ttu-id="29879-182">...</span><span class="sxs-lookup"><span data-stu-id="29879-182">...</span></span>|<span data-ttu-id="29879-183">...</span><span class="sxs-lookup"><span data-stu-id="29879-183">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="29879-184">Başvurular</span><span class="sxs-lookup"><span data-stu-id="29879-184">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="29879-185">REF</span><span class="sxs-lookup"><span data-stu-id="29879-185">REF</span></span>  

 <span data-ttu-id="29879-186">[Ref](ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29879-186">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="29879-187">Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir order varlığına başvuruları döndürür:</span><span class="sxs-lookup"><span data-stu-id="29879-187">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="29879-188">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-188">Output:</span></span>  
  
|<span data-ttu-id="29879-189">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-189">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-190">1</span><span class="sxs-lookup"><span data-stu-id="29879-190">1</span></span>|  
|<span data-ttu-id="29879-191">2</span><span class="sxs-lookup"><span data-stu-id="29879-191">2</span></span>|  
|<span data-ttu-id="29879-192">3</span><span class="sxs-lookup"><span data-stu-id="29879-192">3</span></span>|  
|<span data-ttu-id="29879-193">...</span><span class="sxs-lookup"><span data-stu-id="29879-193">...</span></span>|  
  
 <span data-ttu-id="29879-194">Aşağıdaki örnek, bir varlığın bir özelliğine erişmek için özellik ayıklama işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="29879-194">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="29879-195">Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="29879-195">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="29879-196">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-196">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="29879-197">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-197">Output:</span></span>  
  
|<span data-ttu-id="29879-198">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-198">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-199">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="29879-199">Adjustable Race</span></span>|  
|<span data-ttu-id="29879-200">All-Purpose bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="29879-200">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="29879-201">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="29879-201">AWC Logo Cap</span></span>|  
|<span data-ttu-id="29879-202">...</span><span class="sxs-lookup"><span data-stu-id="29879-202">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="29879-203">DEREF</span><span class="sxs-lookup"><span data-stu-id="29879-203">DEREF</span></span>  

 <span data-ttu-id="29879-204">[Deref](deref-entity-sql.md) bir başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="29879-204">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="29879-205">Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir sıra için sıra varlıklarını üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2` ..</span><span class="sxs-lookup"><span data-stu-id="29879-205">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="29879-206">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-206">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="29879-207">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-207">Output:</span></span>  
  
|<span data-ttu-id="29879-208">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-208">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-209">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="29879-209">Adjustable Race</span></span>|  
|<span data-ttu-id="29879-210">All-Purpose bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="29879-210">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="29879-211">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="29879-211">AWC Logo Cap</span></span>|  
|<span data-ttu-id="29879-212">...</span><span class="sxs-lookup"><span data-stu-id="29879-212">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="29879-213">CREATEREF VE ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="29879-213">CREATEREF AND KEY</span></span>  

 <span data-ttu-id="29879-214">[CreateRef](createref-entity-sql.md) anahtar geçirerek bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29879-214">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="29879-215">[Anahtar](key-entity-sql.md) , tür başvurusu olan bir ifadenin anahtar kısmını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="29879-215">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="29879-216">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-216">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="29879-217">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-217">Output:</span></span>  
  
|<span data-ttu-id="29879-218">ProductID</span><span class="sxs-lookup"><span data-stu-id="29879-218">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="29879-219">980</span><span class="sxs-lookup"><span data-stu-id="29879-219">980</span></span>|  
|<span data-ttu-id="29879-220">365</span><span class="sxs-lookup"><span data-stu-id="29879-220">365</span></span>|  
|<span data-ttu-id="29879-221">771</span><span class="sxs-lookup"><span data-stu-id="29879-221">771</span></span>|  
|<span data-ttu-id="29879-222">...</span><span class="sxs-lookup"><span data-stu-id="29879-222">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="29879-223">İşlevler</span><span class="sxs-lookup"><span data-stu-id="29879-223">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="29879-224">Canonical</span><span class="sxs-lookup"><span data-stu-id="29879-224">Canonical</span></span>  

 <span data-ttu-id="29879-225">[Kurallı işlevler](canonical-functions.md) için ad alanı, içinde olduğu gibi EDM 'dir `Edm.Length("string")` .</span><span class="sxs-lookup"><span data-stu-id="29879-225">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="29879-226">Kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmadığı sürece, ad alanını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="29879-226">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="29879-227">İki ad alanı aynı işleve sahip ise, Kullanıcı tam adı özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="29879-227">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="29879-228">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-228">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="29879-229">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-229">Output:</span></span>  
  
|<span data-ttu-id="29879-230">Ad uzunluğu</span><span class="sxs-lookup"><span data-stu-id="29879-230">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="29879-231">6</span><span class="sxs-lookup"><span data-stu-id="29879-231">6</span></span>|  
|<span data-ttu-id="29879-232">6</span><span class="sxs-lookup"><span data-stu-id="29879-232">6</span></span>|  
|<span data-ttu-id="29879-233">5</span><span class="sxs-lookup"><span data-stu-id="29879-233">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="29879-234">Microsoft Provider-Specific</span><span class="sxs-lookup"><span data-stu-id="29879-234">Microsoft Provider-Specific</span></span>  

 <span data-ttu-id="29879-235">[Microsoft sağlayıcıya özgü işlevler](../sqlclient-for-ef-functions.md) `SqlServer` ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="29879-235">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="29879-236">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-236">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="29879-237">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-237">Output:</span></span>  
  
|<span data-ttu-id="29879-238">EmailLen</span><span class="sxs-lookup"><span data-stu-id="29879-238">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="29879-239">27</span><span class="sxs-lookup"><span data-stu-id="29879-239">27</span></span>|  
|<span data-ttu-id="29879-240">27</span><span class="sxs-lookup"><span data-stu-id="29879-240">27</span></span>|  
|<span data-ttu-id="29879-241">26</span><span class="sxs-lookup"><span data-stu-id="29879-241">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="29879-242">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="29879-242">Namespaces</span></span>  

 <span data-ttu-id="29879-243">[USING](using-entity-sql.md) , bir sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29879-243">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="29879-244">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-244">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="29879-245">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-245">Output:</span></span>  
  
|<span data-ttu-id="29879-246">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-246">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-247">aa</span><span class="sxs-lookup"><span data-stu-id="29879-247">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="29879-248">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="29879-248">Paging</span></span>  

 <span data-ttu-id="29879-249">Sayfalama, bir [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümceleri [order by](order-by-entity-sql.md) yan tümcesine bildirerek ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="29879-249">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="29879-250">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-250">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="29879-251">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-251">Output:</span></span>  
  
|<span data-ttu-id="29879-252">ID</span><span class="sxs-lookup"><span data-stu-id="29879-252">ID</span></span>|<span data-ttu-id="29879-253">Name</span><span class="sxs-lookup"><span data-stu-id="29879-253">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="29879-254">10</span><span class="sxs-lookup"><span data-stu-id="29879-254">10</span></span>|<span data-ttu-id="29879-255">Adina</span><span class="sxs-lookup"><span data-stu-id="29879-255">Adina</span></span>|  
|<span data-ttu-id="29879-256">11</span><span class="sxs-lookup"><span data-stu-id="29879-256">11</span></span>|<span data-ttu-id="29879-257">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="29879-257">Agcaoili</span></span>|  
|<span data-ttu-id="29879-258">12</span><span class="sxs-lookup"><span data-stu-id="29879-258">12</span></span>|<span data-ttu-id="29879-259">Agular</span><span class="sxs-lookup"><span data-stu-id="29879-259">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="29879-260">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="29879-260">Grouping</span></span>  

 <span data-ttu-id="29879-261">[Gruplandırma ölçütü](group-by-entity-sql.md) , sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirler.</span><span class="sxs-lookup"><span data-stu-id="29879-261">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="29879-262">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-262">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="29879-263">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-263">Output:</span></span>  
  
|<span data-ttu-id="29879-264">name</span><span class="sxs-lookup"><span data-stu-id="29879-264">name</span></span>|  
|----------|  
|<span data-ttu-id="29879-265">LL Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="29879-265">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="29879-266">ML Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="29879-266">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="29879-267">HL Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="29879-267">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="29879-268">...</span><span class="sxs-lookup"><span data-stu-id="29879-268">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="29879-269">Gezinti</span><span class="sxs-lookup"><span data-stu-id="29879-269">Navigation</span></span>  

 <span data-ttu-id="29879-270">İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="29879-270">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="29879-271">[Git](navigate-entity-sql.md) , ilişki türünü olarak niteleyen \<namespace> . \<relationship type name> ..</span><span class="sxs-lookup"><span data-stu-id="29879-271">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="29879-272">\<T>To end 'in kardinalite değeri 1 ise, gezinin ref döndürür.</span><span class="sxs-lookup"><span data-stu-id="29879-272">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="29879-273">To end 'in kardinalite değeri n ise, koleksiyon<ref \<T>> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="29879-273">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="29879-274">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-274">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="29879-275">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-275">Output:</span></span>  
  
|<span data-ttu-id="29879-276">Adres SID 'si</span><span class="sxs-lookup"><span data-stu-id="29879-276">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="29879-277">1</span><span class="sxs-lookup"><span data-stu-id="29879-277">1</span></span>|  
|<span data-ttu-id="29879-278">2</span><span class="sxs-lookup"><span data-stu-id="29879-278">2</span></span>|  
|<span data-ttu-id="29879-279">3</span><span class="sxs-lookup"><span data-stu-id="29879-279">3</span></span>|  
|<span data-ttu-id="29879-280">...</span><span class="sxs-lookup"><span data-stu-id="29879-280">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="29879-281">DEĞER ' I SEÇIN VE</span><span class="sxs-lookup"><span data-stu-id="29879-281">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="29879-282">DEĞER SEÇIN</span><span class="sxs-lookup"><span data-stu-id="29879-282">SELECT VALUE</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="29879-283">örtük satır oluşturmayı atlamak için değer Seç yan tümcesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="29879-283">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="29879-284">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="29879-284">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="29879-285">Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin çevresinde bir satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretilebilinir, örneğin: `SELECT VALUE a` .</span><span class="sxs-lookup"><span data-stu-id="29879-285">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="29879-286">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-286">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="29879-287">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-287">Output:</span></span>  
  
|<span data-ttu-id="29879-288">Name</span><span class="sxs-lookup"><span data-stu-id="29879-288">Name</span></span>|  
|----------|  
|<span data-ttu-id="29879-289">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="29879-289">Adjustable Race</span></span>|  
|<span data-ttu-id="29879-290">All-Purpose bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="29879-290">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="29879-291">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="29879-291">AWC Logo Cap</span></span>|  
|<span data-ttu-id="29879-292">...</span><span class="sxs-lookup"><span data-stu-id="29879-292">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="29879-293">SELECT</span><span class="sxs-lookup"><span data-stu-id="29879-293">SELECT</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="29879-294">Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="29879-294">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="29879-295">Projeksiyde bir veya daha fazla öğe alır ve alanlar içeren bir veri kaydıyla sonuçlanır, örneğin: `SELECT a, b, c` .</span><span class="sxs-lookup"><span data-stu-id="29879-295">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="29879-296">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-296">Example:</span></span>  
  
 <span data-ttu-id="29879-297">AdventureWorksEntities. Product öğesinden p çıkışı olarak p.Name, p. ProductID 'yi SEÇIN:</span><span class="sxs-lookup"><span data-stu-id="29879-297">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="29879-298">Name</span><span class="sxs-lookup"><span data-stu-id="29879-298">Name</span></span>|<span data-ttu-id="29879-299">ProductID</span><span class="sxs-lookup"><span data-stu-id="29879-299">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="29879-300">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="29879-300">Adjustable Race</span></span>|<span data-ttu-id="29879-301">1</span><span class="sxs-lookup"><span data-stu-id="29879-301">1</span></span>|  
|<span data-ttu-id="29879-302">All-Purpose bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="29879-302">All-Purpose Bike Stand</span></span>|<span data-ttu-id="29879-303">879</span><span class="sxs-lookup"><span data-stu-id="29879-303">879</span></span>|  
|<span data-ttu-id="29879-304">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="29879-304">AWC Logo Cap</span></span>|<span data-ttu-id="29879-305">712</span><span class="sxs-lookup"><span data-stu-id="29879-305">712</span></span>|  
|<span data-ttu-id="29879-306">...</span><span class="sxs-lookup"><span data-stu-id="29879-306">...</span></span>|<span data-ttu-id="29879-307">...</span><span class="sxs-lookup"><span data-stu-id="29879-307">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="29879-308">CASE IFADESI</span><span class="sxs-lookup"><span data-stu-id="29879-308">CASE EXPRESSION</span></span>  

 <span data-ttu-id="29879-309">[Case ifadesi](case-entity-sql.md) sonucu belirleyecek bir dizi Boole ifadesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="29879-309">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="29879-310">Örnek:</span><span class="sxs-lookup"><span data-stu-id="29879-310">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="29879-311">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="29879-311">Output:</span></span>  
  
|<span data-ttu-id="29879-312">Değer</span><span class="sxs-lookup"><span data-stu-id="29879-312">Value</span></span>|  
|-----------|  
|<span data-ttu-id="29879-313">TRUE</span><span class="sxs-lookup"><span data-stu-id="29879-313">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29879-314">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29879-314">See also</span></span>

- [<span data-ttu-id="29879-315">Entity SQL Başvurusu</span><span class="sxs-lookup"><span data-stu-id="29879-315">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="29879-316">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="29879-316">Entity SQL Overview</span></span>](entity-sql-overview.md)
