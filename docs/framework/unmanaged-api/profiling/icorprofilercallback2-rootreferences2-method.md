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
ms.openlocfilehash: abf92749e1139a85ea2f49fb5d5caff69ce39c24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458467"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="a8ea8-102">ICorProfilerCallback2::RootReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8ea8-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="a8ea8-103">Çöp toplama gerçekleştikten sonra Profil Oluşturucu kök başvurular hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="a8ea8-104">Bu yöntem uzantısıdır [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8ea8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8ea8-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8ea8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8ea8-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="a8ea8-107">[in] Öğe sayısı `rootRefIds`, `rootKinds`, `rootFlags`, ve `rootIds` dizileri.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="a8ea8-108">[in] Nesne kimlikleri, her biri bir statik nesnesinin ya da nesneyi yığında başvuruda bulunan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="a8ea8-109">Öğeleri `rootKinds` dizi karşılık gelen öğelerinde sınıflandırmak için bilgiler sağlar `rootRefIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="a8ea8-110">[in] Bir dizi [cor_prf_gc_root_kınd](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) atık toplama kök türünü gösteren değerler.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="a8ea8-111">[in] Bir dizi [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) bir atık toplama kök özelliklerini açıklayan değerleri.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="a8ea8-112">[in] Çöp toplama kök değerine bağlı olarak ilgili ek bilgileri içeren bir tamsayı o noktaya UINT_PTR dizisi değerleri `rootKinds` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="a8ea8-113">Kök türü bir yığın ise, kök değişkenini içeren işlevi için kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="a8ea8-114">Bu kök kimliği 0 ise, CLR iç bir adlandırılmamış işlevi işlevdir.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="a8ea8-115">Kök türü bir tanıtıcı ise, kök atık toplama tanıtıcısını kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="a8ea8-116">Diğer kök türleri kimliği belirsiz bir değerdir ve yoksayılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8ea8-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8ea8-117">Remarks</span></span>  
 <span data-ttu-id="a8ea8-118">`rootRefIds`, `rootKinds`, `rootFlags`, Ve `rootIds` paralel diziler dizidir.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="a8ea8-119">Diğer bir deyişle, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, ve `rootIds[i]` tüm aynı kök ilgilendiren.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="a8ea8-120">Her ikisi de `RootReferences` ve `RootReferences2` profil oluşturucu bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="a8ea8-121">Profil oluşturucular normalde uygulamak bir yöntemi veya diğer, ancak ikisini birlikte, bilgilerin geçirilen çünkü `RootReferences2` geçirilen bir üst kümesidir `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="a8ea8-122">Girdileri mümkündür `rootRefIds` karşılık gelen kök başvurusu null ve yönetilen yığında bir nesneye başvurmuyor anlamına gelir. sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="a8ea8-123">Tarafından döndürülen nesne kimlikleri `RootReferences2` çöp toplama nesneleri eski adreslerinden yeni adreslere taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="a8ea8-124">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `RootReferences2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="a8ea8-125">Zaman [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) olan çağrılır, tüm nesneleri yeni konumlarına taşınır ve güvenli bir şekilde Denetlenmekte.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8ea8-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8ea8-126">Requirements</span></span>  
 <span data-ttu-id="a8ea8-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8ea8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8ea8-128">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8ea8-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8ea8-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8ea8-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8ea8-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8ea8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ea8-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8ea8-131">See Also</span></span>  
 [<span data-ttu-id="a8ea8-132">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8ea8-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="a8ea8-133">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8ea8-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
