---
title: Karşılaştırma semantiği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 2ca91861d4830321168e96fb200c4889dc33b04b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631712"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="531a3-102">Karşılaştırma semantiği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="531a3-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="531a3-103">Aşağıdakilerden herhangi birini gerçekleştiren [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri karşılaştırma türü örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="531a3-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="531a3-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="531a3-104">Explicit comparison</span></span>  
 <span data-ttu-id="531a3-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="531a3-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="531a3-106">!=</span><span class="sxs-lookup"><span data-stu-id="531a3-106">!=</span></span>  
  
 <span data-ttu-id="531a3-107">İşlem sırası:</span><span class="sxs-lookup"><span data-stu-id="531a3-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="531a3-108">Öğesinin işlemler:</span><span class="sxs-lookup"><span data-stu-id="531a3-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="531a3-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="531a3-109">IS NULL</span></span>  
  
- <span data-ttu-id="531a3-110">NULL DEĞİL</span><span class="sxs-lookup"><span data-stu-id="531a3-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="531a3-111">Açık ayrımı</span><span class="sxs-lookup"><span data-stu-id="531a3-111">Explicit distinction</span></span>  
 <span data-ttu-id="531a3-112">Eşitlik fark:</span><span class="sxs-lookup"><span data-stu-id="531a3-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="531a3-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="531a3-113">DISTINCT</span></span>  
  
- <span data-ttu-id="531a3-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="531a3-114">GROUP BY</span></span>  
  
 <span data-ttu-id="531a3-115">Ayrım sıralama:</span><span class="sxs-lookup"><span data-stu-id="531a3-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="531a3-116">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="531a3-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="531a3-117">Örtük ayrımı</span><span class="sxs-lookup"><span data-stu-id="531a3-117">Implicit distinction</span></span>  
 <span data-ttu-id="531a3-118">İşlemler ve koşullarına (eşitlik) ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="531a3-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="531a3-119">UNION</span><span class="sxs-lookup"><span data-stu-id="531a3-119">UNION</span></span>  
  
- <span data-ttu-id="531a3-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="531a3-120">INTERSECT</span></span>  
  
- <span data-ttu-id="531a3-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="531a3-121">EXCEPT</span></span>  
  
- <span data-ttu-id="531a3-122">SET</span><span class="sxs-lookup"><span data-stu-id="531a3-122">SET</span></span>  
  
- <span data-ttu-id="531a3-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="531a3-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="531a3-124">Öğe koşullarına (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="531a3-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="531a3-125">IN</span><span class="sxs-lookup"><span data-stu-id="531a3-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="531a3-126">Desteklenen kombinasyonlar</span><span class="sxs-lookup"><span data-stu-id="531a3-126">Supported Combinations</span></span>  
 <span data-ttu-id="531a3-127">Karşılaştırma işleçleri türü her türdeki tüm desteklenen birleşimleri aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="531a3-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="531a3-128">**Tür**</span><span class="sxs-lookup"><span data-stu-id="531a3-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="531a3-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="531a3-129">**!=**</span></span>|<span data-ttu-id="531a3-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="531a3-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="531a3-131">**FARKLI**</span><span class="sxs-lookup"><span data-stu-id="531a3-131">**DISTINCT**</span></span>|<span data-ttu-id="531a3-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="531a3-132">**UNION**</span></span><br /><br /> <span data-ttu-id="531a3-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="531a3-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="531a3-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="531a3-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="531a3-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="531a3-135">**SET**</span></span><br /><br /> <span data-ttu-id="531a3-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="531a3-136">**OVERLAPS**</span></span>|<span data-ttu-id="531a3-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="531a3-137">**IN**</span></span>|<span data-ttu-id="531a3-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="531a3-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="531a3-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="531a3-139">**>   >=**</span></span>|<span data-ttu-id="531a3-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="531a3-140">**ORDER BY**</span></span>|<span data-ttu-id="531a3-141">**NULL**</span><span class="sxs-lookup"><span data-stu-id="531a3-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="531a3-142">**NULL DEĞİL**</span><span class="sxs-lookup"><span data-stu-id="531a3-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="531a3-143">varlık türü</span><span class="sxs-lookup"><span data-stu-id="531a3-143">Entity type</span></span>|<span data-ttu-id="531a3-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="531a3-145">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="531a3-146">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="531a3-147">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="531a3-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="531a3-151">Karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="531a3-151">Complex type</span></span>|<span data-ttu-id="531a3-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="531a3-159">Satır</span><span class="sxs-lookup"><span data-stu-id="531a3-159">Row</span></span>|<span data-ttu-id="531a3-160">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="531a3-161">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="531a3-162">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="531a3-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-165">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="531a3-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="531a3-167">temel tür</span><span class="sxs-lookup"><span data-stu-id="531a3-167">Primitive type</span></span>|<span data-ttu-id="531a3-168">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-168">Provider-specific</span></span>|<span data-ttu-id="531a3-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-169">Provider-specific</span></span>|<span data-ttu-id="531a3-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-170">Provider-specific</span></span>|<span data-ttu-id="531a3-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-171">Provider-specific</span></span>|<span data-ttu-id="531a3-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-172">Provider-specific</span></span>|<span data-ttu-id="531a3-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-173">Provider-specific</span></span>|<span data-ttu-id="531a3-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="531a3-174">Provider-specific</span></span>|  
|<span data-ttu-id="531a3-175">multiset</span><span class="sxs-lookup"><span data-stu-id="531a3-175">Multiset</span></span>|<span data-ttu-id="531a3-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="531a3-183">başvuru</span><span class="sxs-lookup"><span data-stu-id="531a3-183">Ref</span></span>|<span data-ttu-id="531a3-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="531a3-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="531a3-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="531a3-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="531a3-188">throw</span><span class="sxs-lookup"><span data-stu-id="531a3-188">Throw</span></span>|<span data-ttu-id="531a3-189">throw</span><span class="sxs-lookup"><span data-stu-id="531a3-189">Throw</span></span>|<span data-ttu-id="531a3-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="531a3-191">İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="531a3-191">Association</span></span><br /><br /> <span data-ttu-id="531a3-192">türü</span><span class="sxs-lookup"><span data-stu-id="531a3-192">type</span></span>|<span data-ttu-id="531a3-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-194">throw</span><span class="sxs-lookup"><span data-stu-id="531a3-194">Throw</span></span>|<span data-ttu-id="531a3-195">throw</span><span class="sxs-lookup"><span data-stu-id="531a3-195">Throw</span></span>|<span data-ttu-id="531a3-196">throw</span><span class="sxs-lookup"><span data-stu-id="531a3-196">Throw</span></span>|<span data-ttu-id="531a3-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="531a3-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="531a3-200"><sup>1</sup>belirtilen varlık türü örnekleri başvurularına örtük olarak, aşağıdaki örnekte gösterildiği gibi karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="531a3-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="531a3-201">Bir varlık örneği için açık bir başvuru karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="531a3-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="531a3-202">Bu girişiminde bulunulursa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="531a3-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="531a3-203">Örneğin, aşağıdaki sorgu, bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="531a3-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="531a3-204"><sup>2</sup>karmaşık türler, Özellikler düzleştirilmiş Mağaza'ya (bunların tüm özelliklerini karşılaştırılabilir olduğu sürece) bunlar karşılaştırılabilir eşlenmelerine gönderilmeden önce.</span><span class="sxs-lookup"><span data-stu-id="531a3-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="531a3-205">Ayrıca bkz: <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="531a3-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="531a3-206"><sup>3</sup>Entity Framework çalışma zamanı desteklenmeyen durum algılar ve ilgi çekici sağlayıcısı depolama olmadan anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="531a3-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="531a3-207"><sup>4</sup>tüm özellikleri karşılaştırmak için bir girişimde.</span><span class="sxs-lookup"><span data-stu-id="531a3-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="531a3-208">Metin, n metin veya görüntü gibi benzer olmayan bir türde bir özellik yoksa, bir sunucu özel durum.</span><span class="sxs-lookup"><span data-stu-id="531a3-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="531a3-209"><sup>5</sup>başvuruları tüm tek tek öğelerine kıyasla (Bu varlık kümesinin adı ve varlık türü tüm anahtar özelliklerini içerir).</span><span class="sxs-lookup"><span data-stu-id="531a3-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="531a3-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="531a3-210">See also</span></span>

- [<span data-ttu-id="531a3-211">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="531a3-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
