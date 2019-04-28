---
title: Karşılaştırma semantiği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
ms.openlocfilehash: 6b4c4177ebd6c45e00a1ac7774e40a43e0c14a74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605977"
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="4659f-102">Karşılaştırma semantiği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="4659f-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="4659f-103">Aşağıdakilerden herhangi birini gerçekleştiren [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri karşılaştırma türü örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="4659f-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="4659f-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="4659f-104">Explicit comparison</span></span>  
 <span data-ttu-id="4659f-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="4659f-105">Equality operations:</span></span>  
  
- =  
  
- <span data-ttu-id="4659f-106">!=</span><span class="sxs-lookup"><span data-stu-id="4659f-106">!=</span></span>  
  
 <span data-ttu-id="4659f-107">İşlem sırası:</span><span class="sxs-lookup"><span data-stu-id="4659f-107">Ordering operations:</span></span>  
  
- <  
  
- \<=  
  
- \>  
  
- \>=  
  
 <span data-ttu-id="4659f-108">Öğesinin işlemler:</span><span class="sxs-lookup"><span data-stu-id="4659f-108">Nullability operations:</span></span>  
  
- <span data-ttu-id="4659f-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="4659f-109">IS NULL</span></span>  
  
- <span data-ttu-id="4659f-110">NULL DEĞİL</span><span class="sxs-lookup"><span data-stu-id="4659f-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="4659f-111">Açık ayrımı</span><span class="sxs-lookup"><span data-stu-id="4659f-111">Explicit distinction</span></span>  
 <span data-ttu-id="4659f-112">Eşitlik fark:</span><span class="sxs-lookup"><span data-stu-id="4659f-112">Equality distinction:</span></span>  
  
- <span data-ttu-id="4659f-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="4659f-113">DISTINCT</span></span>  
  
- <span data-ttu-id="4659f-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="4659f-114">GROUP BY</span></span>  
  
 <span data-ttu-id="4659f-115">Ayrım sıralama:</span><span class="sxs-lookup"><span data-stu-id="4659f-115">Ordering distinction:</span></span>  
  
- <span data-ttu-id="4659f-116">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="4659f-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="4659f-117">Örtük ayrımı</span><span class="sxs-lookup"><span data-stu-id="4659f-117">Implicit distinction</span></span>  
 <span data-ttu-id="4659f-118">İşlemler ve koşullarına (eşitlik) ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="4659f-118">Set operations and predicates (equality):</span></span>  
  
- <span data-ttu-id="4659f-119">UNION</span><span class="sxs-lookup"><span data-stu-id="4659f-119">UNION</span></span>  
  
- <span data-ttu-id="4659f-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="4659f-120">INTERSECT</span></span>  
  
- <span data-ttu-id="4659f-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="4659f-121">EXCEPT</span></span>  
  
- <span data-ttu-id="4659f-122">SET</span><span class="sxs-lookup"><span data-stu-id="4659f-122">SET</span></span>  
  
- <span data-ttu-id="4659f-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="4659f-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="4659f-124">Öğe koşullarına (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="4659f-124">Item predicates (equality):</span></span>  
  
- <span data-ttu-id="4659f-125">IN</span><span class="sxs-lookup"><span data-stu-id="4659f-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="4659f-126">Desteklenen kombinasyonlar</span><span class="sxs-lookup"><span data-stu-id="4659f-126">Supported Combinations</span></span>  
 <span data-ttu-id="4659f-127">Karşılaştırma işleçleri türü her türdeki tüm desteklenen birleşimleri aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4659f-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="4659f-128">**Tür**</span><span class="sxs-lookup"><span data-stu-id="4659f-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="4659f-129">**\!=**</span><span class="sxs-lookup"><span data-stu-id="4659f-129">**!=**</span></span>|<span data-ttu-id="4659f-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="4659f-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="4659f-131">**FARKLI**</span><span class="sxs-lookup"><span data-stu-id="4659f-131">**DISTINCT**</span></span>|<span data-ttu-id="4659f-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="4659f-132">**UNION**</span></span><br /><br /> <span data-ttu-id="4659f-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="4659f-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="4659f-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="4659f-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="4659f-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="4659f-135">**SET**</span></span><br /><br /> <span data-ttu-id="4659f-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="4659f-136">**OVERLAPS**</span></span>|<span data-ttu-id="4659f-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="4659f-137">**IN**</span></span>|<span data-ttu-id="4659f-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="4659f-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="4659f-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="4659f-139">**>   >=**</span></span>|<span data-ttu-id="4659f-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="4659f-140">**ORDER BY**</span></span>|<span data-ttu-id="4659f-141">**NULL**</span><span class="sxs-lookup"><span data-stu-id="4659f-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="4659f-142">**NULL DEĞİL**</span><span class="sxs-lookup"><span data-stu-id="4659f-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="4659f-143">varlık türü</span><span class="sxs-lookup"><span data-stu-id="4659f-143">Entity type</span></span>|<span data-ttu-id="4659f-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="4659f-145">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="4659f-146">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="4659f-147">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="4659f-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="4659f-151">Karmaşık tür</span><span class="sxs-lookup"><span data-stu-id="4659f-151">Complex type</span></span>|<span data-ttu-id="4659f-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="4659f-159">Satır</span><span class="sxs-lookup"><span data-stu-id="4659f-159">Row</span></span>|<span data-ttu-id="4659f-160">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="4659f-161">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="4659f-162">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="4659f-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-165">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="4659f-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="4659f-167">temel tür</span><span class="sxs-lookup"><span data-stu-id="4659f-167">Primitive type</span></span>|<span data-ttu-id="4659f-168">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-168">Provider-specific</span></span>|<span data-ttu-id="4659f-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-169">Provider-specific</span></span>|<span data-ttu-id="4659f-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-170">Provider-specific</span></span>|<span data-ttu-id="4659f-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-171">Provider-specific</span></span>|<span data-ttu-id="4659f-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-172">Provider-specific</span></span>|<span data-ttu-id="4659f-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-173">Provider-specific</span></span>|<span data-ttu-id="4659f-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="4659f-174">Provider-specific</span></span>|  
|<span data-ttu-id="4659f-175">multiset</span><span class="sxs-lookup"><span data-stu-id="4659f-175">Multiset</span></span>|<span data-ttu-id="4659f-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="4659f-183">başvuru</span><span class="sxs-lookup"><span data-stu-id="4659f-183">Ref</span></span>|<span data-ttu-id="4659f-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="4659f-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="4659f-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="4659f-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="4659f-188">throw</span><span class="sxs-lookup"><span data-stu-id="4659f-188">Throw</span></span>|<span data-ttu-id="4659f-189">throw</span><span class="sxs-lookup"><span data-stu-id="4659f-189">Throw</span></span>|<span data-ttu-id="4659f-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="4659f-191">İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="4659f-191">Association</span></span><br /><br /> <span data-ttu-id="4659f-192">türü</span><span class="sxs-lookup"><span data-stu-id="4659f-192">type</span></span>|<span data-ttu-id="4659f-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-194">throw</span><span class="sxs-lookup"><span data-stu-id="4659f-194">Throw</span></span>|<span data-ttu-id="4659f-195">throw</span><span class="sxs-lookup"><span data-stu-id="4659f-195">Throw</span></span>|<span data-ttu-id="4659f-196">throw</span><span class="sxs-lookup"><span data-stu-id="4659f-196">Throw</span></span>|<span data-ttu-id="4659f-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="4659f-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="4659f-200"><sup>1</sup>belirtilen varlık türü örnekleri başvurularına örtük olarak, aşağıdaki örnekte gösterildiği gibi karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="4659f-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="4659f-201">Bir varlık örneği için açık bir başvuru karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="4659f-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="4659f-202">Bu girişiminde bulunulursa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4659f-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="4659f-203">Örneğin, aşağıdaki sorgu, bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="4659f-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="4659f-204"><sup>2</sup>karmaşık türler, Özellikler düzleştirilmiş Mağaza'ya (bunların tüm özelliklerini karşılaştırılabilir olduğu sürece) bunlar karşılaştırılabilir eşlenmelerine gönderilmeden önce.</span><span class="sxs-lookup"><span data-stu-id="4659f-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="4659f-205">Ayrıca bkz: <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="4659f-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="4659f-206"><sup>3</sup>Entity Framework çalışma zamanı desteklenmeyen durum algılar ve ilgi çekici sağlayıcısı depolama olmadan anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4659f-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="4659f-207"><sup>4</sup>tüm özellikleri karşılaştırmak için bir girişimde.</span><span class="sxs-lookup"><span data-stu-id="4659f-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="4659f-208">Metin, n metin veya görüntü gibi benzer olmayan bir türde bir özellik yoksa, bir sunucu özel durum.</span><span class="sxs-lookup"><span data-stu-id="4659f-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="4659f-209"><sup>5</sup>başvuruları tüm tek tek öğelerine kıyasla (Bu varlık kümesinin adı ve varlık türü tüm anahtar özelliklerini içerir).</span><span class="sxs-lookup"><span data-stu-id="4659f-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4659f-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4659f-210">See also</span></span>

- [<span data-ttu-id="4659f-211">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4659f-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
