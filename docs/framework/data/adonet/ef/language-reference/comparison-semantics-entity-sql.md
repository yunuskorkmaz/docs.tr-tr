---
title: Karşılaştırma semantiği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 8d7868b0166f0a18824ec25e6cdf639deec665ac
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833940"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="b6ede-102">Karşılaştırma semantiği (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6ede-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="b6ede-103">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçlerinden herhangi birini gerçekleştirmek, tür örneklerinin karşılaştırmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="b6ede-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="b6ede-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="b6ede-104">Explicit comparison</span></span>  
 <span data-ttu-id="b6ede-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="b6ede-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="b6ede-106">!=</span><span class="sxs-lookup"><span data-stu-id="b6ede-106">!=</span></span>  
  
 <span data-ttu-id="b6ede-107">Sıralama işlemleri:</span><span class="sxs-lookup"><span data-stu-id="b6ede-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="b6ede-108">Null değer alabilirlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="b6ede-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="b6ede-109">NULL</span><span class="sxs-lookup"><span data-stu-id="b6ede-109">IS NULL</span></span>  
  
- <span data-ttu-id="b6ede-110">NULL DEĞIL</span><span class="sxs-lookup"><span data-stu-id="b6ede-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="b6ede-111">Açık ayrım</span><span class="sxs-lookup"><span data-stu-id="b6ede-111">Explicit distinction</span></span>  
 <span data-ttu-id="b6ede-112">Eşitlik ayrımı:</span><span class="sxs-lookup"><span data-stu-id="b6ede-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="b6ede-113">AYRı</span><span class="sxs-lookup"><span data-stu-id="b6ede-113">DISTINCT</span></span>  
  
- <span data-ttu-id="b6ede-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="b6ede-114">GROUP BY</span></span>  
  
 <span data-ttu-id="b6ede-115">Sıralama ayrımı:</span><span class="sxs-lookup"><span data-stu-id="b6ede-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="b6ede-116">SİPARİŞ VEREN</span><span class="sxs-lookup"><span data-stu-id="b6ede-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="b6ede-117">Örtük ayrım</span><span class="sxs-lookup"><span data-stu-id="b6ede-117">Implicit distinction</span></span>  
 <span data-ttu-id="b6ede-118">İşlemleri ve koşulları ayarlama (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="b6ede-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="b6ede-119">UNION</span><span class="sxs-lookup"><span data-stu-id="b6ede-119">UNION</span></span>  
  
- <span data-ttu-id="b6ede-120">KESIŞ</span><span class="sxs-lookup"><span data-stu-id="b6ede-120">INTERSECT</span></span>  
  
- <span data-ttu-id="b6ede-121">KULLANıLDıKLARı</span><span class="sxs-lookup"><span data-stu-id="b6ede-121">EXCEPT</span></span>  
  
- <span data-ttu-id="b6ede-122">KURMAK</span><span class="sxs-lookup"><span data-stu-id="b6ede-122">SET</span></span>  
  
- <span data-ttu-id="b6ede-123">ÇAKıŞ</span><span class="sxs-lookup"><span data-stu-id="b6ede-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="b6ede-124">Öğe doğrulamaları (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="b6ede-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="b6ede-125">IN</span><span class="sxs-lookup"><span data-stu-id="b6ede-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="b6ede-126">Desteklenen birleşimler</span><span class="sxs-lookup"><span data-stu-id="b6ede-126">Supported Combinations</span></span>  
 <span data-ttu-id="b6ede-127">Aşağıdaki tabloda her tür türü için karşılaştırma işleçleri 'nin desteklenen tüm birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b6ede-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="b6ede-128">**Tür**</span><span class="sxs-lookup"><span data-stu-id="b6ede-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="b6ede-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="b6ede-129">**!=**</span></span>|<span data-ttu-id="b6ede-130">**GRUPLANDıRMA ÖLÇÜTÜ**</span><span class="sxs-lookup"><span data-stu-id="b6ede-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="b6ede-131">**AYRı**</span><span class="sxs-lookup"><span data-stu-id="b6ede-131">**DISTINCT**</span></span>|<span data-ttu-id="b6ede-132">**BIRLEŞIM**</span><span class="sxs-lookup"><span data-stu-id="b6ede-132">**UNION**</span></span><br /><br /> <span data-ttu-id="b6ede-133">**KESIŞ**</span><span class="sxs-lookup"><span data-stu-id="b6ede-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="b6ede-134">**KULLANıLDıKLARı**</span><span class="sxs-lookup"><span data-stu-id="b6ede-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="b6ede-135">**KURMAK**</span><span class="sxs-lookup"><span data-stu-id="b6ede-135">**SET**</span></span><br /><br /> <span data-ttu-id="b6ede-136">**ÇAKıŞ**</span><span class="sxs-lookup"><span data-stu-id="b6ede-136">**OVERLAPS**</span></span>|<span data-ttu-id="b6ede-137">**'NDAKI**</span><span class="sxs-lookup"><span data-stu-id="b6ede-137">**IN**</span></span>|<span data-ttu-id="b6ede-138">**< < =**</span><span class="sxs-lookup"><span data-stu-id="b6ede-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="b6ede-139">**> > =**</span><span class="sxs-lookup"><span data-stu-id="b6ede-139">**>   >=**</span></span>|<span data-ttu-id="b6ede-140">**SıRALAMA ÖLÇÜTÜ**</span><span class="sxs-lookup"><span data-stu-id="b6ede-140">**ORDER BY**</span></span>|<span data-ttu-id="b6ede-141">**NULL**</span><span class="sxs-lookup"><span data-stu-id="b6ede-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="b6ede-142">**NULL DEĞIL**</span><span class="sxs-lookup"><span data-stu-id="b6ede-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="b6ede-143">varlık türü</span><span class="sxs-lookup"><span data-stu-id="b6ede-143">Entity type</span></span>|<span data-ttu-id="b6ede-144">Başvuru<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="b6ede-145">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="b6ede-146">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="b6ede-147">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="b6ede-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-150">Başvuru<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="b6ede-151">karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="b6ede-151">Complex type</span></span>|<span data-ttu-id="b6ede-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="b6ede-159">Sırada</span><span class="sxs-lookup"><span data-stu-id="b6ede-159">Row</span></span>|<span data-ttu-id="b6ede-160">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="b6ede-161">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="b6ede-162">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="b6ede-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-165">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="b6ede-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="b6ede-167">İlkel tür</span><span class="sxs-lookup"><span data-stu-id="b6ede-167">Primitive type</span></span>|<span data-ttu-id="b6ede-168">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-168">Provider-specific</span></span>|<span data-ttu-id="b6ede-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-169">Provider-specific</span></span>|<span data-ttu-id="b6ede-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-170">Provider-specific</span></span>|<span data-ttu-id="b6ede-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-171">Provider-specific</span></span>|<span data-ttu-id="b6ede-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-172">Provider-specific</span></span>|<span data-ttu-id="b6ede-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-173">Provider-specific</span></span>|<span data-ttu-id="b6ede-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="b6ede-174">Provider-specific</span></span>|  
|<span data-ttu-id="b6ede-175">Değerlerden</span><span class="sxs-lookup"><span data-stu-id="b6ede-175">Multiset</span></span>|<span data-ttu-id="b6ede-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="b6ede-183">ref</span><span class="sxs-lookup"><span data-stu-id="b6ede-183">Ref</span></span>|<span data-ttu-id="b6ede-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="b6ede-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="b6ede-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="b6ede-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="b6ede-188">yaratır</span><span class="sxs-lookup"><span data-stu-id="b6ede-188">Throw</span></span>|<span data-ttu-id="b6ede-189">yaratır</span><span class="sxs-lookup"><span data-stu-id="b6ede-189">Throw</span></span>|<span data-ttu-id="b6ede-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="b6ede-191">kaldırma</span><span class="sxs-lookup"><span data-stu-id="b6ede-191">Association</span></span><br /><br /> <span data-ttu-id="b6ede-192">type</span><span class="sxs-lookup"><span data-stu-id="b6ede-192">type</span></span>|<span data-ttu-id="b6ede-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-194">yaratır</span><span class="sxs-lookup"><span data-stu-id="b6ede-194">Throw</span></span>|<span data-ttu-id="b6ede-195">yaratır</span><span class="sxs-lookup"><span data-stu-id="b6ede-195">Throw</span></span>|<span data-ttu-id="b6ede-196">yaratır</span><span class="sxs-lookup"><span data-stu-id="b6ede-196">Throw</span></span>|<span data-ttu-id="b6ede-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="b6ede-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="b6ede-200"><sup>1</sup> Aşağıdaki örnekte gösterildiği gibi, belirtilen varlık türü örneklerinin başvuruları örtük olarak karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="b6ede-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="b6ede-201">Bir varlık örneği açık bir başvuruyla karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="b6ede-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="b6ede-202">Bu denendiğinde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b6ede-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="b6ede-203">Örneğin, aşağıdaki sorgu bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b6ede-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="b6ede-204"><sup>2</sup> Karmaşık türlerin özellikleri depoya gönderilmeden önce düzleştirilir, bu nedenle karşılaştırılabilir hale gelir (tüm özellikleri karşılaştırılabilir olduğu sürece).</span><span class="sxs-lookup"><span data-stu-id="b6ede-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="b6ede-205">Ayrıca bkz <sup>. 4.</sup></span><span class="sxs-lookup"><span data-stu-id="b6ede-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="b6ede-206"><sup>3</sup> Entity Framework çalışma zamanı, desteklenmeyen durumu algılar ve sağlayıcıyı/mağazayı bildirmeden anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b6ede-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="b6ede-207"><sup>4</sup> Tüm özellikleri karşılaştırmak için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="b6ede-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="b6ede-208">Metin, n metin veya görüntü gibi karşılaştırılabilir olmayan bir türde bir özellik varsa sunucu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="b6ede-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="b6ede-209"><sup>5</sup> Başvuruların tüm ayrı öğeleri karşılaştırılır (Bu, varlık kümesi adını ve varlık türünün tüm anahtar özelliklerini içerir).</span><span class="sxs-lookup"><span data-stu-id="b6ede-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ede-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6ede-210">See also</span></span>

- [<span data-ttu-id="b6ede-211">Entity SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="b6ede-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
