---
title: "Karşılaştırma semantiği (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e20d47e0ae97067d2dcafcf929f717598d4e3e80
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="2970a-102">Karşılaştırma semantiği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="2970a-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="2970a-103">Aşağıdakilerden herhangi birini gerçekleştirme [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işleçleri karşılaştırma türü örnekleri içerir:</span><span class="sxs-lookup"><span data-stu-id="2970a-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="2970a-104">Açık karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="2970a-104">Explicit comparison</span></span>  
 <span data-ttu-id="2970a-105">Eşitlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="2970a-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="2970a-106">!=</span><span class="sxs-lookup"><span data-stu-id="2970a-106">!=</span></span>  
  
 <span data-ttu-id="2970a-107">Operations sıralama:</span><span class="sxs-lookup"><span data-stu-id="2970a-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   \>  
  
-   \>=  
  
 <span data-ttu-id="2970a-108">Null atanabilirlik işlemleri:</span><span class="sxs-lookup"><span data-stu-id="2970a-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="2970a-109">IS NULL</span><span class="sxs-lookup"><span data-stu-id="2970a-109">IS NULL</span></span>  
  
-   <span data-ttu-id="2970a-110">NULL OLMAYAN</span><span class="sxs-lookup"><span data-stu-id="2970a-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="2970a-111">Açık ayrım</span><span class="sxs-lookup"><span data-stu-id="2970a-111">Explicit distinction</span></span>  
 <span data-ttu-id="2970a-112">Eşitlik fark:</span><span class="sxs-lookup"><span data-stu-id="2970a-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="2970a-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="2970a-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="2970a-114">GRUPLANDIRMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="2970a-114">GROUP BY</span></span>  
  
 <span data-ttu-id="2970a-115">Ayrım sıralama:</span><span class="sxs-lookup"><span data-stu-id="2970a-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="2970a-116">SIRALAMA ÖLÇÜTÜ</span><span class="sxs-lookup"><span data-stu-id="2970a-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="2970a-117">Örtük ayrım</span><span class="sxs-lookup"><span data-stu-id="2970a-117">Implicit distinction</span></span>  
 <span data-ttu-id="2970a-118">İşlemler ve koşulları (eşitlik) ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="2970a-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="2970a-119">UNION</span><span class="sxs-lookup"><span data-stu-id="2970a-119">UNION</span></span>  
  
-   <span data-ttu-id="2970a-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="2970a-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="2970a-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="2970a-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="2970a-122">AYARLAMA</span><span class="sxs-lookup"><span data-stu-id="2970a-122">SET</span></span>  
  
-   <span data-ttu-id="2970a-123">ÇAKIŞIYOR</span><span class="sxs-lookup"><span data-stu-id="2970a-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="2970a-124">Öğe koşulları (eşitlik):</span><span class="sxs-lookup"><span data-stu-id="2970a-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="2970a-125">IN</span><span class="sxs-lookup"><span data-stu-id="2970a-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="2970a-126">Desteklenen birleşimleri</span><span class="sxs-lookup"><span data-stu-id="2970a-126">Supported Combinations</span></span>  
 <span data-ttu-id="2970a-127">Aşağıdaki tabloda her türde Karşılaştırma işleçleri tüm desteklenen birleşimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2970a-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="2970a-128">Türü</span><span class="sxs-lookup"><span data-stu-id="2970a-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="2970a-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="2970a-129">**!=**</span></span>|<span data-ttu-id="2970a-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="2970a-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="2970a-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="2970a-131">**DISTINCT**</span></span>|<span data-ttu-id="2970a-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="2970a-132">**UNION**</span></span><br /><br /> <span data-ttu-id="2970a-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="2970a-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="2970a-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="2970a-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="2970a-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="2970a-135">**SET**</span></span><br /><br /> <span data-ttu-id="2970a-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="2970a-136">**OVERLAPS**</span></span>|<span data-ttu-id="2970a-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="2970a-137">**IN**</span></span>|<span data-ttu-id="2970a-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="2970a-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="2970a-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="2970a-139">**>   >=**</span></span>|<span data-ttu-id="2970a-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="2970a-140">**ORDER BY**</span></span>|<span data-ttu-id="2970a-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="2970a-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="2970a-142">NULL OLMAYAN</span><span class="sxs-lookup"><span data-stu-id="2970a-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="2970a-143">Varlık türü</span><span class="sxs-lookup"><span data-stu-id="2970a-143">Entity type</span></span>|<span data-ttu-id="2970a-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="2970a-145">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="2970a-146">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="2970a-147">Tüm özellikleri<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="2970a-148">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-149">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="2970a-151">karmaşık türü</span><span class="sxs-lookup"><span data-stu-id="2970a-151">Complex type</span></span>|<span data-ttu-id="2970a-152">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-153">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-154">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-155">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-156">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-157">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-158">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2970a-159">Satır</span><span class="sxs-lookup"><span data-stu-id="2970a-159">Row</span></span>|<span data-ttu-id="2970a-160">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="2970a-161">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="2970a-162">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="2970a-163">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-164">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-165">Tüm özellikleri<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="2970a-166">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2970a-167">ilkel tür</span><span class="sxs-lookup"><span data-stu-id="2970a-167">Primitive type</span></span>|<span data-ttu-id="2970a-168">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-168">Provider-specific</span></span>|<span data-ttu-id="2970a-169">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-169">Provider-specific</span></span>|<span data-ttu-id="2970a-170">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-170">Provider-specific</span></span>|<span data-ttu-id="2970a-171">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-171">Provider-specific</span></span>|<span data-ttu-id="2970a-172">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-172">Provider-specific</span></span>|<span data-ttu-id="2970a-173">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-173">Provider-specific</span></span>|<span data-ttu-id="2970a-174">Sağlayıcıya özgü</span><span class="sxs-lookup"><span data-stu-id="2970a-174">Provider-specific</span></span>|  
|<span data-ttu-id="2970a-175">Multiset</span><span class="sxs-lookup"><span data-stu-id="2970a-175">Multiset</span></span>|<span data-ttu-id="2970a-176">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-177">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-178">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-179">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-180">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-181">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-182">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2970a-183">Ref</span><span class="sxs-lookup"><span data-stu-id="2970a-183">Ref</span></span>|<span data-ttu-id="2970a-184">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="2970a-185">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="2970a-186">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="2970a-187">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="2970a-188">Throw</span><span class="sxs-lookup"><span data-stu-id="2970a-188">Throw</span></span>|<span data-ttu-id="2970a-189">Throw</span><span class="sxs-lookup"><span data-stu-id="2970a-189">Throw</span></span>|<span data-ttu-id="2970a-190">Evet<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="2970a-191">İlişkilendirme</span><span class="sxs-lookup"><span data-stu-id="2970a-191">Association</span></span><br /><br /> <span data-ttu-id="2970a-192">türü</span><span class="sxs-lookup"><span data-stu-id="2970a-192">type</span></span>|<span data-ttu-id="2970a-193">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-194">Throw</span><span class="sxs-lookup"><span data-stu-id="2970a-194">Throw</span></span>|<span data-ttu-id="2970a-195">Throw</span><span class="sxs-lookup"><span data-stu-id="2970a-195">Throw</span></span>|<span data-ttu-id="2970a-196">Throw</span><span class="sxs-lookup"><span data-stu-id="2970a-196">Throw</span></span>|<span data-ttu-id="2970a-197">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-198">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="2970a-199">Throw<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="2970a-200"><sup>1</sup>belirtilen varlık türü örnekleri başvuruları örtük olarak, aşağıdaki örnekte gösterildiği gibi karşılaştırılır:</span><span class="sxs-lookup"><span data-stu-id="2970a-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="2970a-201">Bir varlık örneği için açık bir başvuru karşılaştırılamaz.</span><span class="sxs-lookup"><span data-stu-id="2970a-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="2970a-202">Bu denenirse özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="2970a-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="2970a-203">Örneğin, aşağıdaki sorguyu bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2970a-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="2970a-204"><sup>2</sup>karmaşık türlerin özellikleri düzleştirilmiş deposuna (tüm özelliklerini karşılaştırılabilir sürece) karşılaştırılabilir olduklarında şekilde gönderilmeden önce.</span><span class="sxs-lookup"><span data-stu-id="2970a-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="2970a-205">Ayrıca bkz. <sup>4.</sup></span><span class="sxs-lookup"><span data-stu-id="2970a-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="2970a-206"><sup>3</sup>Entity Framework çalışma zamanı desteklenmeyen durum algılar ve sağlayıcı/deposu çekici olmadan anlamlı bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2970a-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="2970a-207"><sup>4</sup>tüm özellikleri karşılaştırmak için bir girişimde.</span><span class="sxs-lookup"><span data-stu-id="2970a-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="2970a-208">Text, ntext veya image, gibi karşılaştırılabilir olmayan bir türde bir özellik varsa, bir sunucu özel durum.</span><span class="sxs-lookup"><span data-stu-id="2970a-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="2970a-209"><sup>5</sup>başvuruları tüm ayrı ayrı öğeler karşılaştırılır (Bu varlık kümesi adı ve varlık türünün tüm anahtar özellikleri içerir).</span><span class="sxs-lookup"><span data-stu-id="2970a-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2970a-210">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2970a-210">See Also</span></span>  
 [<span data-ttu-id="2970a-211">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2970a-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
