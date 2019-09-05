---
title: Karşılaştırma semantiği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: da7b8f662d10376abd649e674701b43b7b740a6f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251190"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="0ecf7-102">Karşılaştırma semantiği (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0ecf7-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="0ecf7-103">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçlerden herhangi birini gerçekleştirmek, tür örneklerinin karşılaştırmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="0ecf7-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="0ecf7-104">Explicit comparison</span></span>  
 <span data-ttu-id="0ecf7-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="0ecf7-106">!=</span><span class="sxs-lookup"><span data-stu-id="0ecf7-106">!=</span></span>  
  
 <span data-ttu-id="0ecf7-107">Sıralama işlemleri:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="0ecf7-108">Null değer alabilirlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="0ecf7-109">NULL</span><span class="sxs-lookup"><span data-stu-id="0ecf7-109">IS NULL</span></span>  
  
- <span data-ttu-id="0ecf7-110">NULL DEĞIL</span><span class="sxs-lookup"><span data-stu-id="0ecf7-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="0ecf7-111">Açık ayrım</span><span class="sxs-lookup"><span data-stu-id="0ecf7-111">Explicit distinction</span></span>  
 <span data-ttu-id="0ecf7-112">Eşitlik ayrımı:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="0ecf7-113">AYRI</span><span class="sxs-lookup"><span data-stu-id="0ecf7-113">DISTINCT</span></span>  
  
- <span data-ttu-id="0ecf7-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="0ecf7-114">GROUP BY</span></span>  
  
 <span data-ttu-id="0ecf7-115">Sıralama ayrımı:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="0ecf7-116">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="0ecf7-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="0ecf7-117">Örtük ayrım</span><span class="sxs-lookup"><span data-stu-id="0ecf7-117">Implicit distinction</span></span>  
 <span data-ttu-id="0ecf7-118">İşlemleri ve koşulları ayarlama (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="0ecf7-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="0ecf7-119">UNION</span><span class="sxs-lookup"><span data-stu-id="0ecf7-119">UNION</span></span>  
  
- <span data-ttu-id="0ecf7-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="0ecf7-120">INTERSECT</span></span>  
  
- <span data-ttu-id="0ecf7-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="0ecf7-121">EXCEPT</span></span>  
  
- <span data-ttu-id="0ecf7-122">SET</span><span class="sxs-lookup"><span data-stu-id="0ecf7-122">SET</span></span>  
  
- <span data-ttu-id="0ecf7-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="0ecf7-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="0ecf7-124">Öğe doğrulamaları (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="0ecf7-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="0ecf7-125">IN</span><span class="sxs-lookup"><span data-stu-id="0ecf7-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="0ecf7-126">Desteklenen birleşimler</span><span class="sxs-lookup"><span data-stu-id="0ecf7-126">Supported Combinations</span></span>  
 <span data-ttu-id="0ecf7-127">Aşağıdaki tabloda her tür türü için karşılaştırma işleçleri 'nin desteklenen tüm birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="0ecf7-128">**Tür**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="0ecf7-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-129">**!=**</span></span>|<span data-ttu-id="0ecf7-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="0ecf7-131">**AYRI**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-131">**DISTINCT**</span></span>|<span data-ttu-id="0ecf7-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-132">**UNION**</span></span><br /><br /> <span data-ttu-id="0ecf7-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="0ecf7-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="0ecf7-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-135">**SET**</span></span><br /><br /> <span data-ttu-id="0ecf7-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-136">**OVERLAPS**</span></span>|<span data-ttu-id="0ecf7-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-137">**IN**</span></span>|<span data-ttu-id="0ecf7-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="0ecf7-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-139">**>   >=**</span></span>|<span data-ttu-id="0ecf7-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-140">**ORDER BY**</span></span>|<span data-ttu-id="0ecf7-141">**NULL**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="0ecf7-142">**NULL DEĞIL**</span><span class="sxs-lookup"><span data-stu-id="0ecf7-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="0ecf7-143">Varlık türü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-143">Entity type</span></span>|<span data-ttu-id="0ecf7-144">Başvuru<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="0ecf7-145">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="0ecf7-146">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="0ecf7-147">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="0ecf7-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-150">Başvuru<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="0ecf7-151">Karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="0ecf7-151">Complex type</span></span>|<span data-ttu-id="0ecf7-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0ecf7-159">Satır</span><span class="sxs-lookup"><span data-stu-id="0ecf7-159">Row</span></span>|<span data-ttu-id="0ecf7-160">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="0ecf7-161">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="0ecf7-162">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="0ecf7-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-165">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="0ecf7-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0ecf7-167">İlkel tür</span><span class="sxs-lookup"><span data-stu-id="0ecf7-167">Primitive type</span></span>|<span data-ttu-id="0ecf7-168">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-168">Provider-specific</span></span>|<span data-ttu-id="0ecf7-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-169">Provider-specific</span></span>|<span data-ttu-id="0ecf7-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-170">Provider-specific</span></span>|<span data-ttu-id="0ecf7-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-171">Provider-specific</span></span>|<span data-ttu-id="0ecf7-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-172">Provider-specific</span></span>|<span data-ttu-id="0ecf7-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-173">Provider-specific</span></span>|<span data-ttu-id="0ecf7-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-174">Provider-specific</span></span>|  
|<span data-ttu-id="0ecf7-175">Değerlerden</span><span class="sxs-lookup"><span data-stu-id="0ecf7-175">Multiset</span></span>|<span data-ttu-id="0ecf7-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="0ecf7-183">Ref</span><span class="sxs-lookup"><span data-stu-id="0ecf7-183">Ref</span></span>|<span data-ttu-id="0ecf7-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="0ecf7-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="0ecf7-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="0ecf7-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="0ecf7-188">Throw</span><span class="sxs-lookup"><span data-stu-id="0ecf7-188">Throw</span></span>|<span data-ttu-id="0ecf7-189">Throw</span><span class="sxs-lookup"><span data-stu-id="0ecf7-189">Throw</span></span>|<span data-ttu-id="0ecf7-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="0ecf7-191">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0ecf7-191">Association</span></span><br /><br /> <span data-ttu-id="0ecf7-192">türü</span><span class="sxs-lookup"><span data-stu-id="0ecf7-192">type</span></span>|<span data-ttu-id="0ecf7-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-194">Throw</span><span class="sxs-lookup"><span data-stu-id="0ecf7-194">Throw</span></span>|<span data-ttu-id="0ecf7-195">Throw</span><span class="sxs-lookup"><span data-stu-id="0ecf7-195">Throw</span></span>|<span data-ttu-id="0ecf7-196">Throw</span><span class="sxs-lookup"><span data-stu-id="0ecf7-196">Throw</span></span>|<span data-ttu-id="0ecf7-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="0ecf7-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="0ecf7-200"><sup>1</sup> Aşağıdaki örnekte gösterildiği gibi, belirtilen varlık türü örneklerinin başvuruları örtük olarak karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="0ecf7-201">Bir varlık örneği açık bir başvuruyla karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ecf7-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="0ecf7-202">Bu denendiğinde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0ecf7-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="0ecf7-203">Örneğin, aşağıdaki sorgu bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0ecf7-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="0ecf7-204"><sup>2</sup> Karmaşık türlerin özellikleri depoya gönderilmeden önce düzleştirilir, bu nedenle karşılaştırılabilir hale gelir (tüm özellikleri karşılaştırılabilir olduğu sürece).</span><span class="sxs-lookup"><span data-stu-id="0ecf7-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="0ecf7-205">Ayrıca bkz <sup>. 4.</sup></span><span class="sxs-lookup"><span data-stu-id="0ecf7-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="0ecf7-206"><sup>3</sup> Entity Framework çalışma zamanı, desteklenmeyen durumu algılar ve sağlayıcıyı/mağazayı bildirmeden anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ecf7-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="0ecf7-207"><sup>4</sup> Tüm özellikleri karşılaştırmak için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="0ecf7-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="0ecf7-208">Metin, n metin veya görüntü gibi karşılaştırılabilir olmayan bir türde bir özellik varsa sunucu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="0ecf7-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="0ecf7-209"><sup>5</sup> Başvuruların tüm ayrı öğeleri karşılaştırılır (Bu, varlık kümesi adını ve varlık türünün tüm anahtar özelliklerini içerir).</span><span class="sxs-lookup"><span data-stu-id="0ecf7-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ecf7-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ecf7-210">See also</span></span>

- [<span data-ttu-id="0ecf7-211">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ecf7-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
