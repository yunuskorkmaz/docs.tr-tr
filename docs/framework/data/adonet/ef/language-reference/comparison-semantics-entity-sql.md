---
description: 'Daha fazla bilgi edinin: karşılaştırma semantiği (Entity SQL)'
title: Karşılaştırma semantiği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: b1c832cb6f2903073b1c6be806c73823b1f4a220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786439"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="882a5-103">Karşılaştırma semantiği (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="882a5-103">Comparison Semantics (Entity SQL)</span></span>

<span data-ttu-id="882a5-104">Aşağıdaki işleçlerden herhangi birini gerçekleştirmek, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tür örneklerinin karşılaştırmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="882a5-104">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="882a5-105">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="882a5-105">Explicit comparison</span></span>  

 <span data-ttu-id="882a5-106">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="882a5-106">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="882a5-107">!=</span><span class="sxs-lookup"><span data-stu-id="882a5-107">!=</span></span>  
  
 <span data-ttu-id="882a5-108">Sıralama işlemleri:</span><span class="sxs-lookup"><span data-stu-id="882a5-108">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="882a5-109">Null değer alabilirlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="882a5-109">Nullability operations:</span></span>  
  
- <span data-ttu-id="882a5-110">NULL</span><span class="sxs-lookup"><span data-stu-id="882a5-110">IS NULL</span></span>  
  
- <span data-ttu-id="882a5-111">NULL DEĞIL</span><span class="sxs-lookup"><span data-stu-id="882a5-111">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="882a5-112">Açık ayrım</span><span class="sxs-lookup"><span data-stu-id="882a5-112">Explicit distinction</span></span>  

 <span data-ttu-id="882a5-113">Eşitlik ayrımı:</span><span class="sxs-lookup"><span data-stu-id="882a5-113">Equality distinction:</span></span>  
  
- <span data-ttu-id="882a5-114">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="882a5-114">DISTINCT</span></span>  
  
- <span data-ttu-id="882a5-115">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="882a5-115">GROUP BY</span></span>  
  
 <span data-ttu-id="882a5-116">Sıralama ayrımı:</span><span class="sxs-lookup"><span data-stu-id="882a5-116">Ordering distinction:</span></span>  
  
- <span data-ttu-id="882a5-117">SİPARİŞ VEREN</span><span class="sxs-lookup"><span data-stu-id="882a5-117">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="882a5-118">Örtük ayrım</span><span class="sxs-lookup"><span data-stu-id="882a5-118">Implicit distinction</span></span>  

 <span data-ttu-id="882a5-119">İşlemleri ve koşulları ayarlama (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="882a5-119">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="882a5-120">UNION</span><span class="sxs-lookup"><span data-stu-id="882a5-120">UNION</span></span>  
  
- <span data-ttu-id="882a5-121">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="882a5-121">INTERSECT</span></span>  
  
- <span data-ttu-id="882a5-122">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="882a5-122">EXCEPT</span></span>  
  
- <span data-ttu-id="882a5-123">SET</span><span class="sxs-lookup"><span data-stu-id="882a5-123">SET</span></span>  
  
- <span data-ttu-id="882a5-124">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="882a5-124">OVERLAPS</span></span>  
  
 <span data-ttu-id="882a5-125">Öğe doğrulamaları (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="882a5-125">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="882a5-126">IN</span><span class="sxs-lookup"><span data-stu-id="882a5-126">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="882a5-127">Desteklenen birleşimler</span><span class="sxs-lookup"><span data-stu-id="882a5-127">Supported Combinations</span></span>  

 <span data-ttu-id="882a5-128">Aşağıdaki tabloda her tür türü için karşılaştırma işleçleri 'nin desteklenen tüm birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="882a5-128">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="882a5-129">**Tür**</span><span class="sxs-lookup"><span data-stu-id="882a5-129">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="882a5-130">**!=**</span><span class="sxs-lookup"><span data-stu-id="882a5-130">**!=**</span></span>|<span data-ttu-id="882a5-131">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="882a5-131">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="882a5-132">**AYRı**</span><span class="sxs-lookup"><span data-stu-id="882a5-132">**DISTINCT**</span></span>|<span data-ttu-id="882a5-133">**UNION**</span><span class="sxs-lookup"><span data-stu-id="882a5-133">**UNION**</span></span><br /><br /> <span data-ttu-id="882a5-134">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="882a5-134">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="882a5-135">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="882a5-135">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="882a5-136">**SET**</span><span class="sxs-lookup"><span data-stu-id="882a5-136">**SET**</span></span><br /><br /> <span data-ttu-id="882a5-137">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="882a5-137">**OVERLAPS**</span></span>|<span data-ttu-id="882a5-138">**'NDAKI**</span><span class="sxs-lookup"><span data-stu-id="882a5-138">**IN**</span></span>|<span data-ttu-id="882a5-139">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="882a5-139">**<   <=**</span></span><br /><br /> <span data-ttu-id="882a5-140">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="882a5-140">**>   >=**</span></span>|<span data-ttu-id="882a5-141">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="882a5-141">**ORDER BY**</span></span>|<span data-ttu-id="882a5-142">**NULL**</span><span class="sxs-lookup"><span data-stu-id="882a5-142">**IS NULL**</span></span><br /><br /> <span data-ttu-id="882a5-143">**NULL DEĞIL**</span><span class="sxs-lookup"><span data-stu-id="882a5-143">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="882a5-144">Varlık türü</span><span class="sxs-lookup"><span data-stu-id="882a5-144">Entity type</span></span>|<span data-ttu-id="882a5-145">Başvuru<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-145">Ref<sup>1</sup></span></span>|<span data-ttu-id="882a5-146">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="882a5-147">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="882a5-148">Tüm Özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-148">All properties<sup>2</sup></span></span>|<span data-ttu-id="882a5-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-150">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-150">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-151">Başvuru<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-151">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="882a5-152">Karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="882a5-152">Complex type</span></span>|<span data-ttu-id="882a5-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-158">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-159">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-159">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="882a5-160">Satır</span><span class="sxs-lookup"><span data-stu-id="882a5-160">Row</span></span>|<span data-ttu-id="882a5-161">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="882a5-162">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="882a5-163">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-163">All properties<sup>4</sup></span></span>|<span data-ttu-id="882a5-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-165">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-165">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-166">Tüm Özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-166">All properties<sup>4</sup></span></span>|<span data-ttu-id="882a5-167">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-167">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="882a5-168">İlkel tür</span><span class="sxs-lookup"><span data-stu-id="882a5-168">Primitive type</span></span>|<span data-ttu-id="882a5-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-169">Provider-specific</span></span>|<span data-ttu-id="882a5-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-170">Provider-specific</span></span>|<span data-ttu-id="882a5-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-171">Provider-specific</span></span>|<span data-ttu-id="882a5-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-172">Provider-specific</span></span>|<span data-ttu-id="882a5-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-173">Provider-specific</span></span>|<span data-ttu-id="882a5-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-174">Provider-specific</span></span>|<span data-ttu-id="882a5-175">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="882a5-175">Provider-specific</span></span>|  
|<span data-ttu-id="882a5-176">Değerlerden</span><span class="sxs-lookup"><span data-stu-id="882a5-176">Multiset</span></span>|<span data-ttu-id="882a5-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-182">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-183">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-183">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="882a5-184">Ref</span><span class="sxs-lookup"><span data-stu-id="882a5-184">Ref</span></span>|<span data-ttu-id="882a5-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="882a5-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="882a5-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="882a5-188">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-188">Yes<sup>5</sup></span></span>|<span data-ttu-id="882a5-189">Throw</span><span class="sxs-lookup"><span data-stu-id="882a5-189">Throw</span></span>|<span data-ttu-id="882a5-190">Throw</span><span class="sxs-lookup"><span data-stu-id="882a5-190">Throw</span></span>|<span data-ttu-id="882a5-191">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-191">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="882a5-192">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="882a5-192">Association</span></span><br /><br /> <span data-ttu-id="882a5-193">tür</span><span class="sxs-lookup"><span data-stu-id="882a5-193">type</span></span>|<span data-ttu-id="882a5-194">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-194">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-195">Throw</span><span class="sxs-lookup"><span data-stu-id="882a5-195">Throw</span></span>|<span data-ttu-id="882a5-196">Throw</span><span class="sxs-lookup"><span data-stu-id="882a5-196">Throw</span></span>|<span data-ttu-id="882a5-197">Throw</span><span class="sxs-lookup"><span data-stu-id="882a5-197">Throw</span></span>|<span data-ttu-id="882a5-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-199">Throw<sup>3</sup></span></span>|<span data-ttu-id="882a5-200">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-200">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="882a5-201"><sup>1</sup> Aşağıdaki örnekte gösterildiği gibi, belirtilen varlık türü örneklerinin başvuruları örtük olarak karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="882a5-201"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="882a5-202">Bir varlık örneği açık bir başvuruyla karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="882a5-202">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="882a5-203">Bu denendiğinde, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="882a5-203">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="882a5-204">Örneğin, aşağıdaki sorgu bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="882a5-204">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="882a5-205"><sup>2</sup> Karmaşık türlerin özellikleri depoya gönderilmeden önce düzleştirilir, bu nedenle karşılaştırılabilir hale gelir (tüm özellikleri karşılaştırılabilir olduğu sürece).</span><span class="sxs-lookup"><span data-stu-id="882a5-205"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="882a5-206">Ayrıca bkz <sup>. 4.</sup></span><span class="sxs-lookup"><span data-stu-id="882a5-206">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="882a5-207"><sup>3</sup> Entity Framework çalışma zamanı, desteklenmeyen durumu algılar ve sağlayıcıyı/mağazayı bildirmeden anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="882a5-207"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="882a5-208"><sup>4</sup> Tüm özellikleri karşılaştırmak için bir girişimde bulunuldu.</span><span class="sxs-lookup"><span data-stu-id="882a5-208"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="882a5-209">Metin, n metin veya görüntü gibi karşılaştırılabilir olmayan bir türde bir özellik varsa sunucu özel durumu oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="882a5-209">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="882a5-210"><sup>5</sup> Başvuruların tüm ayrı öğeleri karşılaştırılır (Bu, varlık kümesi adını ve varlık türünün tüm anahtar özelliklerini içerir).</span><span class="sxs-lookup"><span data-stu-id="882a5-210"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882a5-211">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="882a5-211">See also</span></span>

- [<span data-ttu-id="882a5-212">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="882a5-212">Entity SQL Overview</span></span>](entity-sql-overview.md)
