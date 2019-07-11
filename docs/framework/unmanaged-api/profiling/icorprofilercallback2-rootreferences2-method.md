---
title: ICorProfilerCallback2::RootReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 563a2e19c9c254870b3e767253a276a201e631a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779310"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="cda11-102">ICorProfilerCallback2::RootReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cda11-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="cda11-103">Bir çöp toplama işlemi gerçekleştirildikten sonra Profil Oluşturucu kök başvurular hakkında bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="cda11-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="cda11-104">Bu yöntem bir uzantısıdır [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cda11-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda11-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cda11-105">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda11-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cda11-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="cda11-107">[in] İçindeki öğelerin sayısını `rootRefIds`, `rootKinds`, `rootFlags`, ve `rootIds` dizileri.</span><span class="sxs-lookup"><span data-stu-id="cda11-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="cda11-108">[in] Statik nesne veya bir nesne yığını üzerindeki her biri başvuran nesne kimlikleri, bir dizi.</span><span class="sxs-lookup"><span data-stu-id="cda11-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="cda11-109">Öğeleri `rootKinds` dizisi karşılık gelen öğeleri sınıflandırmak için bilgi sağlayın `rootRefIds` dizisi.</span><span class="sxs-lookup"><span data-stu-id="cda11-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="cda11-110">[in] Bir dizi [cor_prf_gc_root_kınd](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) çöp toplama kök türünü gösteren değerleri.</span><span class="sxs-lookup"><span data-stu-id="cda11-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="cda11-111">[in] Bir dizi [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) bir çöp toplama kök özelliklerini açıklayan değerleri.</span><span class="sxs-lookup"><span data-stu-id="cda11-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="cda11-112">[in] Bir dizi UINT_PTR o noktaya değerine bağlı olarak, atık toplama kök hakkında ek bilgi içeren bir tamsayı değerleri `rootKinds` parametresi.</span><span class="sxs-lookup"><span data-stu-id="cda11-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="cda11-113">Bir yığın kökünün türü ise kök değişken içeren işlevi kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="cda11-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="cda11-114">Bu kök kimliği 0 ise, CLR iç adlandırılmamış bir işlev işlevdir.</span><span class="sxs-lookup"><span data-stu-id="cda11-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="cda11-115">Kök türü bir tanıtıcı ise kök çöp toplama tanıtıcılarını kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="cda11-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="cda11-116">Diğer kök türleri için kimliği belirsiz bir değerdir ve yoksayılacak.</span><span class="sxs-lookup"><span data-stu-id="cda11-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cda11-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cda11-117">Remarks</span></span>  
 <span data-ttu-id="cda11-118">`rootRefIds`, `rootKinds`, `rootFlags`, Ve `rootIds` paralel diziler dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="cda11-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="cda11-119">Diğer bir deyişle, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, ve `rootIds[i]` tümü aynı kök ilgilendiriyor.</span><span class="sxs-lookup"><span data-stu-id="cda11-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="cda11-120">Her ikisi de `RootReferences` ve `RootReferences2` profil oluşturucu bildirmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cda11-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="cda11-121">Profil oluşturucular tarafından normalde uygulanır bir yöntem veya diğer, ikisi, bilgi geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="cda11-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="cda11-122">Girdileri mümkündür `rootRefIds` , karşılık gelen kök başvuru null ve yönetilen yığındaki bir nesneye başvurmuyor anlamına gelir ve sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cda11-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="cda11-123">Tarafından döndürülen nesne kimlikleri `RootReferences2` çöp toplama nesneleri eski adreslerinden yeni adreslerine taşıma ortasında olabileceğinden geri kendisini sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="cda11-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="cda11-124">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="cda11-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="cda11-125">Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesnelerin yeni konumlarına taşınır ve güvenli bir şekilde inceledi.</span><span class="sxs-lookup"><span data-stu-id="cda11-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda11-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cda11-126">Requirements</span></span>  
 <span data-ttu-id="cda11-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda11-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda11-128">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cda11-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cda11-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cda11-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda11-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda11-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda11-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cda11-131">See also</span></span>

- [<span data-ttu-id="cda11-132">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cda11-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cda11-133">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cda11-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
