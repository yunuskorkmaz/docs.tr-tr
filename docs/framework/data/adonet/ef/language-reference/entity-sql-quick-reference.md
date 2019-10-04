---
title: Entity SQL hızlı başvuru
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833868"
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="2ab4a-102">Entity SQL hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="2ab4a-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="2ab4a-103">Bu konu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgularına hızlı bir başvuru sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="2ab4a-104">Bu konudaki sorgular AdventureWorks Sales Model ' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="2ab4a-105">Leri</span><span class="sxs-lookup"><span data-stu-id="2ab4a-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="2ab4a-106">Dize</span><span class="sxs-lookup"><span data-stu-id="2ab4a-106">String</span></span>  
 <span data-ttu-id="2ab4a-107">Unicode ve Unicode olmayan karakter dizesi değişmez değerleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="2ab4a-108">Unicode dizeleri, N ile sona erer. Örneğin, `N'hello'`.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="2ab4a-109">Aşağıda Unicode olmayan bir dize sabit değeri örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="2ab4a-110">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-110">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-111">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-112">Herkese</span><span class="sxs-lookup"><span data-stu-id="2ab4a-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="2ab4a-113">Tarih Saat</span><span class="sxs-lookup"><span data-stu-id="2ab4a-113">DateTime</span></span>  
 <span data-ttu-id="2ab4a-114">DateTime değişmez değerlerinde hem tarih hem de saat kısımları zorunludur.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="2ab4a-115">Varsayılan değer yok.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-115">There are no default values.</span></span>  
  
 <span data-ttu-id="2ab4a-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-116">Example:</span></span>  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="2ab4a-117">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-117">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-118">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-119">12/25/2006 1:01:00</span><span class="sxs-lookup"><span data-stu-id="2ab4a-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="2ab4a-120">Tamsayı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-120">Integer</span></span>  
 <span data-ttu-id="2ab4a-121">Tamsayı sabit değerleri Int32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünde olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="2ab4a-122">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-122">Example:</span></span>  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="2ab4a-123">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-123">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-124">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-125">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-125">1</span></span>|  
|<span data-ttu-id="2ab4a-126">2</span><span class="sxs-lookup"><span data-stu-id="2ab4a-126">2</span></span>|  
|<span data-ttu-id="2ab4a-127">3</span><span class="sxs-lookup"><span data-stu-id="2ab4a-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="2ab4a-128">Diğer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-128">Other</span></span>  
 <span data-ttu-id="2ab4a-129">@No__t-0 tarafından desteklenen diğer sabit değerler GUID, Ikili, float/double, Decimal ve `null` ' dir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="2ab4a-130">@No__t-0 ' daki null sabit değerler kavramsal modeldeki diğer her türle uyumlu olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="2ab4a-131">Tür oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="2ab4a-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="2ab4a-132">SıRADA</span><span class="sxs-lookup"><span data-stu-id="2ab4a-132">ROW</span></span>  
 <span data-ttu-id="2ab4a-133">[Satır](row-entity-sql.md) , şu şekilde bir anonim, yapısal olarak yazılmış (kayıt) değeri oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="2ab4a-133">[ROW](row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="2ab4a-134">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-134">Example:</span></span>  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 <span data-ttu-id="2ab4a-135">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-135">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="2ab4a-136">ProductID</span></span>|<span data-ttu-id="2ab4a-137">Adı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="2ab4a-138">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-138">1</span></span>|<span data-ttu-id="2ab4a-139">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="2ab4a-139">Adjustable Race</span></span>|  
|<span data-ttu-id="2ab4a-140">879</span><span class="sxs-lookup"><span data-stu-id="2ab4a-140">879</span></span>|<span data-ttu-id="2ab4a-141">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="2ab4a-142">712</span><span class="sxs-lookup"><span data-stu-id="2ab4a-142">712</span></span>|<span data-ttu-id="2ab4a-143">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="2ab4a-144">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-144">...</span></span>|<span data-ttu-id="2ab4a-145">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="2ab4a-146">DEĞERLERDEN</span><span class="sxs-lookup"><span data-stu-id="2ab4a-146">MULTISET</span></span>  
 <span data-ttu-id="2ab4a-147">[Çoklu küme](multiset-entity-sql.md) yapıları, örneğin:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-147">[MULTISET](multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="2ab4a-148">`MULTISET(1,2,2,3)` `--same as` @ no__t-2 @ no__t-3</span><span class="sxs-lookup"><span data-stu-id="2ab4a-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="2ab4a-149">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-149">Example:</span></span>  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="2ab4a-150">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-150">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="2ab4a-151">ProductID</span></span>|<span data-ttu-id="2ab4a-152">Adı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-152">Name</span></span>|<span data-ttu-id="2ab4a-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="2ab4a-153">ProductNumber</span></span>|<span data-ttu-id="2ab4a-154">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="2ab4a-155">842</span><span class="sxs-lookup"><span data-stu-id="2ab4a-155">842</span></span>|<span data-ttu-id="2ab4a-156">Touring-Panniler, büyük</span><span class="sxs-lookup"><span data-stu-id="2ab4a-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="2ab4a-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="2ab4a-157">PA-T100</span></span>|<span data-ttu-id="2ab4a-158">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="2ab4a-159">Nesne</span><span class="sxs-lookup"><span data-stu-id="2ab4a-159">Object</span></span>  
 <span data-ttu-id="2ab4a-160">[Adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md) yapıları (adlandırılmış) `person("abc", 12)` gibi Kullanıcı tanımlı nesneler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-160">[Named Type Constructor](named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="2ab4a-161">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-161">Example:</span></span>  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="2ab4a-162">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-162">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-163">Salesorderdetailıd</span><span class="sxs-lookup"><span data-stu-id="2ab4a-163">SalesOrderDetailID</span></span>|<span data-ttu-id="2ab4a-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="2ab4a-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="2ab4a-165">Ordermik</span><span class="sxs-lookup"><span data-stu-id="2ab4a-165">OrderQty</span></span>|<span data-ttu-id="2ab4a-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="2ab4a-166">ProductID</span></span>|<span data-ttu-id="2ab4a-167">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="2ab4a-168">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-168">1</span></span>|<span data-ttu-id="2ab4a-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="2ab4a-169">4911-403C-98</span></span>|<span data-ttu-id="2ab4a-170">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-170">1</span></span>|<span data-ttu-id="2ab4a-171">776</span><span class="sxs-lookup"><span data-stu-id="2ab4a-171">776</span></span>|<span data-ttu-id="2ab4a-172">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-172">...</span></span>|  
|<span data-ttu-id="2ab4a-173">2</span><span class="sxs-lookup"><span data-stu-id="2ab4a-173">2</span></span>|<span data-ttu-id="2ab4a-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="2ab4a-174">4911-403C-98</span></span>|<span data-ttu-id="2ab4a-175">3</span><span class="sxs-lookup"><span data-stu-id="2ab4a-175">3</span></span>|<span data-ttu-id="2ab4a-176">777</span><span class="sxs-lookup"><span data-stu-id="2ab4a-176">777</span></span>|<span data-ttu-id="2ab4a-177">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-177">...</span></span>|  
|<span data-ttu-id="2ab4a-178">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-178">...</span></span>|<span data-ttu-id="2ab4a-179">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-179">...</span></span>|<span data-ttu-id="2ab4a-180">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-180">...</span></span>|<span data-ttu-id="2ab4a-181">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-181">...</span></span>|<span data-ttu-id="2ab4a-182">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="2ab4a-183">Başvurular</span><span class="sxs-lookup"><span data-stu-id="2ab4a-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="2ab4a-184">REF</span><span class="sxs-lookup"><span data-stu-id="2ab4a-184">REF</span></span>  
 <span data-ttu-id="2ab4a-185">[Ref](ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-185">[REF](ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="2ab4a-186">Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir order varlığına başvuruları döndürür:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="2ab4a-187">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-187">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-188">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-189">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-189">1</span></span>|  
|<span data-ttu-id="2ab4a-190">2</span><span class="sxs-lookup"><span data-stu-id="2ab4a-190">2</span></span>|  
|<span data-ttu-id="2ab4a-191">3</span><span class="sxs-lookup"><span data-stu-id="2ab4a-191">3</span></span>|  
|<span data-ttu-id="2ab4a-192">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-192">...</span></span>|  
  
 <span data-ttu-id="2ab4a-193">Aşağıdaki örnek, bir varlığın bir özelliğine erişmek için özellik ayıklama işleci (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="2ab4a-194">Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvuru yapılır.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="2ab4a-195">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-195">Example:</span></span>  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="2ab4a-196">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-196">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-197">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-198">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="2ab4a-198">Adjustable Race</span></span>|  
|<span data-ttu-id="2ab4a-199">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="2ab4a-200">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="2ab4a-201">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="2ab4a-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="2ab4a-202">DEREF</span></span>  
 <span data-ttu-id="2ab4a-203">[Deref](deref-entity-sql.md) bir başvuru değerine başvurur ve başvurunun sonucunu üretir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-203">[DEREF](deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="2ab4a-204">Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir sıra için sıralama varlıklarını üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span><span class="sxs-lookup"><span data-stu-id="2ab4a-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="2ab4a-205">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-205">Example:</span></span>  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="2ab4a-206">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-206">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-207">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-208">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="2ab4a-208">Adjustable Race</span></span>|  
|<span data-ttu-id="2ab4a-209">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="2ab4a-210">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="2ab4a-211">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="2ab4a-212">CREATEREF VE ANAHTAR</span><span class="sxs-lookup"><span data-stu-id="2ab4a-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="2ab4a-213">[CreateRef](createref-entity-sql.md) anahtar geçirerek bir başvuru oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-213">[CREATEREF](createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="2ab4a-214">[Anahtar](key-entity-sql.md) , tür başvurusu olan bir ifadenin anahtar kısmını ayıklar.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-214">[KEY](key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="2ab4a-215">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-215">Example:</span></span>  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="2ab4a-216">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-216">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="2ab4a-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="2ab4a-218">980</span><span class="sxs-lookup"><span data-stu-id="2ab4a-218">980</span></span>|  
|<span data-ttu-id="2ab4a-219">365</span><span class="sxs-lookup"><span data-stu-id="2ab4a-219">365</span></span>|  
|<span data-ttu-id="2ab4a-220">771</span><span class="sxs-lookup"><span data-stu-id="2ab4a-220">771</span></span>|  
|<span data-ttu-id="2ab4a-221">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="2ab4a-222">İşlevler</span><span class="sxs-lookup"><span data-stu-id="2ab4a-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="2ab4a-223">Canonical</span><span class="sxs-lookup"><span data-stu-id="2ab4a-223">Canonical</span></span>  
 <span data-ttu-id="2ab4a-224">[Kurallı işlevler](canonical-functions.md) için ad alanı, `Edm.Length("string")` ' de olduğu gibi EDM ' dir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-224">The namespace for [canonical functions](canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="2ab4a-225">Kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmadığı sürece, ad alanını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="2ab4a-226">İki ad alanı aynı işleve sahip ise, Kullanıcı tam adı özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="2ab4a-227">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-227">Example:</span></span>  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="2ab4a-228">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-228">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-229">Ad uzunluğu</span><span class="sxs-lookup"><span data-stu-id="2ab4a-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="2ab4a-230">6</span><span class="sxs-lookup"><span data-stu-id="2ab4a-230">6</span></span>|  
|<span data-ttu-id="2ab4a-231">6</span><span class="sxs-lookup"><span data-stu-id="2ab4a-231">6</span></span>|  
|<span data-ttu-id="2ab4a-232">5</span><span class="sxs-lookup"><span data-stu-id="2ab4a-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="2ab4a-233">Microsoft sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2ab4a-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="2ab4a-234">[Microsoft sağlayıcıya özgü işlevler](../sqlclient-for-ef-functions.md) `SqlServer` ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-234">[Microsoft provider-specific functions](../sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="2ab4a-235">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-235">Example:</span></span>  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="2ab4a-236">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-236">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="2ab4a-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="2ab4a-238">27</span><span class="sxs-lookup"><span data-stu-id="2ab4a-238">27</span></span>|  
|<span data-ttu-id="2ab4a-239">27</span><span class="sxs-lookup"><span data-stu-id="2ab4a-239">27</span></span>|  
|<span data-ttu-id="2ab4a-240">26</span><span class="sxs-lookup"><span data-stu-id="2ab4a-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="2ab4a-241">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="2ab4a-241">Namespaces</span></span>  
 <span data-ttu-id="2ab4a-242">[USING](using-entity-sql.md) , bir sorgu ifadesinde kullanılan ad alanlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-242">[USING](using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="2ab4a-243">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-243">Example:</span></span>  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="2ab4a-244">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-244">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-245">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-246">aa</span><span class="sxs-lookup"><span data-stu-id="2ab4a-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="2ab4a-247">Sayfalama</span><span class="sxs-lookup"><span data-stu-id="2ab4a-247">Paging</span></span>  
 <span data-ttu-id="2ab4a-248">Sayfalama, bir [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümceleri [order by](order-by-entity-sql.md) yan tümcesine bildirerek ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-248">Paging can be expressed by declaring a [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses to the [ORDER BY](order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="2ab4a-249">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-249">Example:</span></span>  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="2ab4a-250">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-250">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-251">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2ab4a-251">ID</span></span>|<span data-ttu-id="2ab4a-252">Adı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="2ab4a-253">10</span><span class="sxs-lookup"><span data-stu-id="2ab4a-253">10</span></span>|<span data-ttu-id="2ab4a-254">Adina</span><span class="sxs-lookup"><span data-stu-id="2ab4a-254">Adina</span></span>|  
|<span data-ttu-id="2ab4a-255">11</span><span class="sxs-lookup"><span data-stu-id="2ab4a-255">11</span></span>|<span data-ttu-id="2ab4a-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="2ab4a-256">Agcaoili</span></span>|  
|<span data-ttu-id="2ab4a-257">12</span><span class="sxs-lookup"><span data-stu-id="2ab4a-257">12</span></span>|<span data-ttu-id="2ab4a-258">Agular</span><span class="sxs-lookup"><span data-stu-id="2ab4a-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="2ab4a-259">Gruplama</span><span class="sxs-lookup"><span data-stu-id="2ab4a-259">Grouping</span></span>  
 <span data-ttu-id="2ab4a-260">[Gruplandırma ölçütü](group-by-entity-sql.md) , sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirler.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-260">[GROUPING BY](group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="2ab4a-261">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-261">Example:</span></span>  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="2ab4a-262">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-262">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-263">ad</span><span class="sxs-lookup"><span data-stu-id="2ab4a-263">name</span></span>|  
|----------|  
|<span data-ttu-id="2ab4a-264">LL Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="2ab4a-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="2ab4a-265">ML Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="2ab4a-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="2ab4a-266">HL Sıradağlar koltuk derlemesi</span><span class="sxs-lookup"><span data-stu-id="2ab4a-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="2ab4a-267">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="2ab4a-268">Gezinme</span><span class="sxs-lookup"><span data-stu-id="2ab4a-268">Navigation</span></span>  
 <span data-ttu-id="2ab4a-269">İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="2ab4a-270">[Git](navigate-entity-sql.md) , \<AD alanı > olarak nitelenmiş ilişki türünü alır. \<ilişki türü adı >.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-270">[NAVIGATE](navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="2ab4a-271">Git, to end 'in kardinalitei 1 ise ref @ no__t-0T > döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="2ab4a-272">To end 'in kardinalite değeri n ise, koleksiyon < ref @ no__t-0T > > döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="2ab4a-273">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-273">Example:</span></span>  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="2ab4a-274">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-274">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-275">Adres SID 'si</span><span class="sxs-lookup"><span data-stu-id="2ab4a-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="2ab4a-276">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-276">1</span></span>|  
|<span data-ttu-id="2ab4a-277">2</span><span class="sxs-lookup"><span data-stu-id="2ab4a-277">2</span></span>|  
|<span data-ttu-id="2ab4a-278">3</span><span class="sxs-lookup"><span data-stu-id="2ab4a-278">3</span></span>|  
|<span data-ttu-id="2ab4a-279">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="2ab4a-280">DEĞER ' I SEÇIN VE</span><span class="sxs-lookup"><span data-stu-id="2ab4a-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="2ab4a-281">DEĞER SEÇIN</span><span class="sxs-lookup"><span data-stu-id="2ab4a-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="2ab4a-282">, örtük satır oluşturmayı atlamak için SELECT VALUE yan tümcesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-282">provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="2ab4a-283">SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="2ab4a-284">Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin çevresine satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretile, örneğin: `SELECT VALUE a`.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="2ab4a-285">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-285">Example:</span></span>  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 <span data-ttu-id="2ab4a-286">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-286">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-287">Adı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="2ab4a-288">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="2ab4a-288">Adjustable Race</span></span>|  
|<span data-ttu-id="2ab4a-289">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="2ab4a-290">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="2ab4a-291">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="2ab4a-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="2ab4a-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2ab4a-293">Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-293">also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="2ab4a-294">Projeksiyde bir veya daha fazla öğe alır ve alanlar içeren bir veri kaydıyla sonuçlanır, örneğin: `SELECT a, b, c`.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="2ab4a-295">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-295">Example:</span></span>  
  
 <span data-ttu-id="2ab4a-296">AdventureWorksEntities. Product öğesinden p çıkışı olarak p.Name, p. ProductID 'yi SEÇIN:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="2ab4a-297">Adı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-297">Name</span></span>|<span data-ttu-id="2ab4a-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="2ab4a-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="2ab4a-299">Ayarlanabilir yarış</span><span class="sxs-lookup"><span data-stu-id="2ab4a-299">Adjustable Race</span></span>|<span data-ttu-id="2ab4a-300">1</span><span class="sxs-lookup"><span data-stu-id="2ab4a-300">1</span></span>|  
|<span data-ttu-id="2ab4a-301">Tüm amaç bisiklet Standı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="2ab4a-302">879</span><span class="sxs-lookup"><span data-stu-id="2ab4a-302">879</span></span>|  
|<span data-ttu-id="2ab4a-303">AWC logosu üst sınırı</span><span class="sxs-lookup"><span data-stu-id="2ab4a-303">AWC Logo Cap</span></span>|<span data-ttu-id="2ab4a-304">712</span><span class="sxs-lookup"><span data-stu-id="2ab4a-304">712</span></span>|  
|<span data-ttu-id="2ab4a-305">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-305">...</span></span>|<span data-ttu-id="2ab4a-306">...</span><span class="sxs-lookup"><span data-stu-id="2ab4a-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="2ab4a-307">CASE IFADESI</span><span class="sxs-lookup"><span data-stu-id="2ab4a-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="2ab4a-308">[Case ifadesi](case-entity-sql.md) sonucu belirleyecek bir dizi Boole ifadesi değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-308">The [case expression](case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="2ab4a-309">Örnek:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-309">Example:</span></span>  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="2ab4a-310">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="2ab4a-310">Output:</span></span>  
  
|<span data-ttu-id="2ab4a-311">Değer</span><span class="sxs-lookup"><span data-stu-id="2ab4a-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="2ab4a-312">DEĞERI</span><span class="sxs-lookup"><span data-stu-id="2ab4a-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ab4a-313">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab4a-313">See also</span></span>

- [<span data-ttu-id="2ab4a-314">Entity SQL başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ab4a-314">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2ab4a-315">Entity SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="2ab4a-315">Entity SQL Overview</span></span>](entity-sql-overview.md)
