---
title: "Karşılaştırma semantiği (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c6d22b72e05e6293a7fd3bcf7ddfba6e116e441f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="3b9d2-102">Karşılaştırma semantiği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="3b9d2-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="3b9d2-103">Aşağıdakilerden herhangi birini gerçekleştirme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri karşılaştırma türü örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="3b9d2-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="3b9d2-104">Explicit comparison</span></span>  
 <span data-ttu-id="3b9d2-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="3b9d2-106">!=</span><span class="sxs-lookup"><span data-stu-id="3b9d2-106">!=</span></span>  
  
 <span data-ttu-id="3b9d2-107">Operations sıralama:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="3b9d2-108">Null atanabilirlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="3b9d2-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="3b9d2-109">IS NULL</span></span>  
  
-   <span data-ttu-id="3b9d2-110">NULL OLMAYAN</span><span class="sxs-lookup"><span data-stu-id="3b9d2-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="3b9d2-111">Açık ayrım</span><span class="sxs-lookup"><span data-stu-id="3b9d2-111">Explicit distinction</span></span>  
 <span data-ttu-id="3b9d2-112">Eşitlik fark:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="3b9d2-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="3b9d2-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="3b9d2-114">GRUPLANDIRMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="3b9d2-114">GROUP BY</span></span>  
  
 <span data-ttu-id="3b9d2-115">Ayrım sıralama:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="3b9d2-116">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="3b9d2-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="3b9d2-117">Örtük ayrım</span><span class="sxs-lookup"><span data-stu-id="3b9d2-117">Implicit distinction</span></span>  
 <span data-ttu-id="3b9d2-118">İşlemler ve koşulları (eşitlik) ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="3b9d2-119">UNION</span><span class="sxs-lookup"><span data-stu-id="3b9d2-119">UNION</span></span>  
  
-   <span data-ttu-id="3b9d2-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="3b9d2-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="3b9d2-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="3b9d2-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="3b9d2-122">AYARLAMA</span><span class="sxs-lookup"><span data-stu-id="3b9d2-122">SET</span></span>  
  
-   <span data-ttu-id="3b9d2-123">ÇAKIŞIYOR</span><span class="sxs-lookup"><span data-stu-id="3b9d2-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="3b9d2-124">Öğe koşulları (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="3b9d2-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="3b9d2-125">IN</span><span class="sxs-lookup"><span data-stu-id="3b9d2-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="3b9d2-126">Desteklenen birleşimleri</span><span class="sxs-lookup"><span data-stu-id="3b9d2-126">Supported Combinations</span></span>  
 <span data-ttu-id="3b9d2-127">Aşağıdaki tabloda her türde Karşılaştırma işleçleri tüm desteklenen birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="3b9d2-128">**Türü**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="3b9d2-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-129">**!=**</span></span>|<span data-ttu-id="3b9d2-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="3b9d2-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-131">**DISTINCT**</span></span>|<span data-ttu-id="3b9d2-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-132">**UNION**</span></span><br /><br /> <span data-ttu-id="3b9d2-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="3b9d2-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="3b9d2-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-135">**SET**</span></span><br /><br /> <span data-ttu-id="3b9d2-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-136">**OVERLAPS**</span></span>|<span data-ttu-id="3b9d2-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-137">**IN**</span></span>|<span data-ttu-id="3b9d2-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="3b9d2-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-139">**>   >=**</span></span>|<span data-ttu-id="3b9d2-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-140">**ORDER BY**</span></span>|<span data-ttu-id="3b9d2-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="3b9d2-142">**NULL OLMAYAN**</span><span class="sxs-lookup"><span data-stu-id="3b9d2-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="3b9d2-143">Varlık türü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-143">Entity type</span></span>|<span data-ttu-id="3b9d2-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="3b9d2-145">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="3b9d2-146">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="3b9d2-147">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="3b9d2-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="3b9d2-151">karmaşık türü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-151">Complex type</span></span>|<span data-ttu-id="3b9d2-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="3b9d2-159">Satır</span><span class="sxs-lookup"><span data-stu-id="3b9d2-159">Row</span></span>|<span data-ttu-id="3b9d2-160">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="3b9d2-161">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="3b9d2-162">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="3b9d2-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-165">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="3b9d2-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="3b9d2-167">ilkel tür</span><span class="sxs-lookup"><span data-stu-id="3b9d2-167">Primitive type</span></span>|<span data-ttu-id="3b9d2-168">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-168">Provider-specific</span></span>|<span data-ttu-id="3b9d2-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-169">Provider-specific</span></span>|<span data-ttu-id="3b9d2-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-170">Provider-specific</span></span>|<span data-ttu-id="3b9d2-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-171">Provider-specific</span></span>|<span data-ttu-id="3b9d2-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-172">Provider-specific</span></span>|<span data-ttu-id="3b9d2-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-173">Provider-specific</span></span>|<span data-ttu-id="3b9d2-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-174">Provider-specific</span></span>|  
|<span data-ttu-id="3b9d2-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="3b9d2-175">Multiset</span></span>|<span data-ttu-id="3b9d2-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="3b9d2-183">Ref</span><span class="sxs-lookup"><span data-stu-id="3b9d2-183">Ref</span></span>|<span data-ttu-id="3b9d2-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="3b9d2-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="3b9d2-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="3b9d2-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="3b9d2-188">Throw</span><span class="sxs-lookup"><span data-stu-id="3b9d2-188">Throw</span></span>|<span data-ttu-id="3b9d2-189">Throw</span><span class="sxs-lookup"><span data-stu-id="3b9d2-189">Throw</span></span>|<span data-ttu-id="3b9d2-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="3b9d2-191">İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="3b9d2-191">Association</span></span><br /><br /> <span data-ttu-id="3b9d2-192">türü</span><span class="sxs-lookup"><span data-stu-id="3b9d2-192">type</span></span>|<span data-ttu-id="3b9d2-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-194">Throw</span><span class="sxs-lookup"><span data-stu-id="3b9d2-194">Throw</span></span>|<span data-ttu-id="3b9d2-195">Throw</span><span class="sxs-lookup"><span data-stu-id="3b9d2-195">Throw</span></span>|<span data-ttu-id="3b9d2-196">Throw</span><span class="sxs-lookup"><span data-stu-id="3b9d2-196">Throw</span></span>|<span data-ttu-id="3b9d2-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="3b9d2-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="3b9d2-200"><sup>1</sup>belirtilen varlık türü örnekleri başvuruları örtük olarak, aşağıdaki örnekte gösterildiği gibi karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="3b9d2-201">Bir varlık örneği için açık bir başvuru karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="3b9d2-202">Bu denenirse özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="3b9d2-203">Örneğin, aşağıdaki sorguyu bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3b9d2-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="3b9d2-204"><sup>2</sup>karmaşık türlerin özellikleri düzleştirilmiş deposuna (tüm özelliklerini karşılaştırılabilir sürece) karşılaştırılabilir olduklarında şekilde gönderilmeden önce.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="3b9d2-205">Ayrıca bkz. <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="3b9d2-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="3b9d2-206"><sup>3</sup>Entity Framework çalışma zamanı desteklenmeyen durum algılar ve sağlayıcı/deposu çekici olmadan anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="3b9d2-207"><sup>4</sup>tüm özellikleri karşılaştırmak için bir girişimde.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="3b9d2-208">Text, ntext veya image, gibi karşılaştırılabilir olmayan bir türde bir özellik varsa, bir sunucu özel durum.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="3b9d2-209"><sup>5</sup>başvuruları tüm ayrı ayrı öğeler karşılaştırılır (Bu varlık kümesi adı ve varlık türünün tüm anahtar özellikleri içerir).</span><span class="sxs-lookup"><span data-stu-id="3b9d2-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9d2-210">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9d2-210">See Also</span></span>  
 [<span data-ttu-id="3b9d2-211">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b9d2-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
