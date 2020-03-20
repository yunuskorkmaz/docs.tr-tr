---
title: Karşılaştırma Semantik (Varlık SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 57d81d4b581df76a4382ad5e1d72fe8250b10d43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150460"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="ce81c-102">Karşılaştırma Semantik (Varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="ce81c-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="ce81c-103">Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçlerden herhangi birinin gerçekleştirimi, tür örneklerinin karşılaştırmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="ce81c-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="ce81c-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="ce81c-104">Explicit comparison</span></span>  
 <span data-ttu-id="ce81c-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="ce81c-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="ce81c-106">!=</span><span class="sxs-lookup"><span data-stu-id="ce81c-106">!=</span></span>  
  
 <span data-ttu-id="ce81c-107">Sipariş işlemleri:</span><span class="sxs-lookup"><span data-stu-id="ce81c-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="ce81c-108">Nullability işlemleri:</span><span class="sxs-lookup"><span data-stu-id="ce81c-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="ce81c-109">NULL MU</span><span class="sxs-lookup"><span data-stu-id="ce81c-109">IS NULL</span></span>  
  
- <span data-ttu-id="ce81c-110">NULL Değİl</span><span class="sxs-lookup"><span data-stu-id="ce81c-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="ce81c-111">Açık ayrım</span><span class="sxs-lookup"><span data-stu-id="ce81c-111">Explicit distinction</span></span>  
 <span data-ttu-id="ce81c-112">Eşitlik ayrımı:</span><span class="sxs-lookup"><span data-stu-id="ce81c-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="ce81c-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="ce81c-113">DISTINCT</span></span>  
  
- <span data-ttu-id="ce81c-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="ce81c-114">GROUP BY</span></span>  
  
 <span data-ttu-id="ce81c-115">Sıralama ayrımı:</span><span class="sxs-lookup"><span data-stu-id="ce81c-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="ce81c-116">SİPARİŞ VEREN</span><span class="sxs-lookup"><span data-stu-id="ce81c-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="ce81c-117">Örtük ayrım</span><span class="sxs-lookup"><span data-stu-id="ce81c-117">Implicit distinction</span></span>  
 <span data-ttu-id="ce81c-118">İşlemleri ve yüklemleri (eşitlik) ayarlama:</span><span class="sxs-lookup"><span data-stu-id="ce81c-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="ce81c-119">UNION</span><span class="sxs-lookup"><span data-stu-id="ce81c-119">UNION</span></span>  
  
- <span data-ttu-id="ce81c-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="ce81c-120">INTERSECT</span></span>  
  
- <span data-ttu-id="ce81c-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="ce81c-121">EXCEPT</span></span>  
  
- <span data-ttu-id="ce81c-122">SET</span><span class="sxs-lookup"><span data-stu-id="ce81c-122">SET</span></span>  
  
- <span data-ttu-id="ce81c-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="ce81c-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="ce81c-124">Madde yüklemleri (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="ce81c-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="ce81c-125">IN</span><span class="sxs-lookup"><span data-stu-id="ce81c-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="ce81c-126">Desteklenen Kombinasyonlar</span><span class="sxs-lookup"><span data-stu-id="ce81c-126">Supported Combinations</span></span>  
 <span data-ttu-id="ce81c-127">Aşağıdaki tablo, her tür için karşılaştırma işleçlerinin desteklenen tüm birleşimlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="ce81c-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="ce81c-128">**Tür**</span><span class="sxs-lookup"><span data-stu-id="ce81c-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="ce81c-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="ce81c-129">**!=**</span></span>|<span data-ttu-id="ce81c-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="ce81c-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="ce81c-131">**Farklı**</span><span class="sxs-lookup"><span data-stu-id="ce81c-131">**DISTINCT**</span></span>|<span data-ttu-id="ce81c-132">**Birliği**</span><span class="sxs-lookup"><span data-stu-id="ce81c-132">**UNION**</span></span><br /><br /> <span data-ttu-id="ce81c-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="ce81c-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="ce81c-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="ce81c-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="ce81c-135">**Ayarlamak**</span><span class="sxs-lookup"><span data-stu-id="ce81c-135">**SET**</span></span><br /><br /> <span data-ttu-id="ce81c-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="ce81c-136">**OVERLAPS**</span></span>|<span data-ttu-id="ce81c-137">**Inç**</span><span class="sxs-lookup"><span data-stu-id="ce81c-137">**IN**</span></span>|<span data-ttu-id="ce81c-138">**< <=**</span><span class="sxs-lookup"><span data-stu-id="ce81c-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="ce81c-139">**> >=**</span><span class="sxs-lookup"><span data-stu-id="ce81c-139">**>   >=**</span></span>|<span data-ttu-id="ce81c-140">**SİPARİŞ VEREN**</span><span class="sxs-lookup"><span data-stu-id="ce81c-140">**ORDER BY**</span></span>|<span data-ttu-id="ce81c-141">**NULL MU**</span><span class="sxs-lookup"><span data-stu-id="ce81c-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="ce81c-142">**NULL Değİl**</span><span class="sxs-lookup"><span data-stu-id="ce81c-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="ce81c-143">Varlık türü</span><span class="sxs-lookup"><span data-stu-id="ce81c-143">Entity type</span></span>|<span data-ttu-id="ce81c-144">Hakem<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="ce81c-145">Tüm özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="ce81c-146">Tüm özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="ce81c-147">Tüm özellikler<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="ce81c-148"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-149"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-150">Hakem<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="ce81c-151">Karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="ce81c-151">Complex type</span></span>|<span data-ttu-id="ce81c-152"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-153"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-154"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-155"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-156"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-157"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-158"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="ce81c-159">Satır</span><span class="sxs-lookup"><span data-stu-id="ce81c-159">Row</span></span>|<span data-ttu-id="ce81c-160">Tüm özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="ce81c-161">Tüm özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="ce81c-162">Tüm özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="ce81c-163"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-164"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-165">Tüm özellikler<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="ce81c-166"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="ce81c-167">İlkel tip</span><span class="sxs-lookup"><span data-stu-id="ce81c-167">Primitive type</span></span>|<span data-ttu-id="ce81c-168">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-168">Provider-specific</span></span>|<span data-ttu-id="ce81c-169">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-169">Provider-specific</span></span>|<span data-ttu-id="ce81c-170">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-170">Provider-specific</span></span>|<span data-ttu-id="ce81c-171">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-171">Provider-specific</span></span>|<span data-ttu-id="ce81c-172">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-172">Provider-specific</span></span>|<span data-ttu-id="ce81c-173">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-173">Provider-specific</span></span>|<span data-ttu-id="ce81c-174">Sağlayıcıya özel</span><span class="sxs-lookup"><span data-stu-id="ce81c-174">Provider-specific</span></span>|  
|<span data-ttu-id="ce81c-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="ce81c-175">Multiset</span></span>|<span data-ttu-id="ce81c-176"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-177"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-178"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-179"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-180"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-181"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-182"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="ce81c-183">Referans</span><span class="sxs-lookup"><span data-stu-id="ce81c-183">Ref</span></span>|<span data-ttu-id="ce81c-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="ce81c-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="ce81c-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="ce81c-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="ce81c-188">Throw</span><span class="sxs-lookup"><span data-stu-id="ce81c-188">Throw</span></span>|<span data-ttu-id="ce81c-189">Throw</span><span class="sxs-lookup"><span data-stu-id="ce81c-189">Throw</span></span>|<span data-ttu-id="ce81c-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="ce81c-191">Derneği</span><span class="sxs-lookup"><span data-stu-id="ce81c-191">Association</span></span><br /><br /> <span data-ttu-id="ce81c-192">type</span><span class="sxs-lookup"><span data-stu-id="ce81c-192">type</span></span>|<span data-ttu-id="ce81c-193"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-194">Throw</span><span class="sxs-lookup"><span data-stu-id="ce81c-194">Throw</span></span>|<span data-ttu-id="ce81c-195">Throw</span><span class="sxs-lookup"><span data-stu-id="ce81c-195">Throw</span></span>|<span data-ttu-id="ce81c-196">Throw</span><span class="sxs-lookup"><span data-stu-id="ce81c-196">Throw</span></span>|<span data-ttu-id="ce81c-197"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-198"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="ce81c-199"><sup>3'e</sup> at</span><span class="sxs-lookup"><span data-stu-id="ce81c-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="ce81c-200"><sup>1.1.2</sup> Verilen varlık türü örneklerinin başvuruları, aşağıdaki örnekte gösterildiği gibi örtülü olarak karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="ce81c-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="ce81c-201">Varlık örneği açık bir başvuruyla karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="ce81c-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="ce81c-202">Bu denenirse, bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="ce81c-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="ce81c-203">Örneğin, aşağıdaki sorgu bir özel durum atar:</span><span class="sxs-lookup"><span data-stu-id="ce81c-203">For example, the following query will throw an exception:</span></span>  
  
```sql  
SELECT p1, p2
FROM AdventureWorksEntities.Product AS p1
     JOIN AdventureWorksEntities.Product AS p2
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="ce81c-204"><sup>2.000</sup> Karmaşık türlerin özellikleri mağazaya gönderilmeden önce düzleşir, böylece karşılaştırılabilir hale gelir (tüm özellikleri karşılaştırılabilir olduğu sürece).</span><span class="sxs-lookup"><span data-stu-id="ce81c-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="ce81c-205">Ayrıca <sup>bkz. 4.</sup></span><span class="sxs-lookup"><span data-stu-id="ce81c-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="ce81c-206"><sup>3.2.2</sup> Varlık Çerçevesi çalışma zamanı, desteklenmeyen servis talebialgılar ve sağlayıcı/mağazayla etkileşime girmeden anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce81c-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="ce81c-207"><sup>4.2.2</sup> Tüm özellikleri karşılaştırmak için bir girişimde bulunulr.</span><span class="sxs-lookup"><span data-stu-id="ce81c-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="ce81c-208">Metin, metin veya resim gibi karşılaştırılabilir olmayan bir türde bir özellik varsa, sunucu özel durumu atılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce81c-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="ce81c-209"><sup>5.000</sup> Başvuruların tüm bireysel öğeleri karşılaştırılır (bu varlık kümesi adını ve varlık türünün tüm temel özelliklerini içerir).</span><span class="sxs-lookup"><span data-stu-id="ce81c-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce81c-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce81c-210">See also</span></span>

- [<span data-ttu-id="ce81c-211">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ce81c-211">Entity SQL Overview</span></span>](entity-sql-overview.md)
