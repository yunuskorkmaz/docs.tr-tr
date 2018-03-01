---
title: "ICorProfilerCallback2::GarbageCollectionStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b721b990312f9acda5c9e0208f998793735d2cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="b1a86-102">ICorProfilerCallback2::GarbageCollectionStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1a86-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="b1a86-103">Kod profil oluşturucu çöp toplama başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="b1a86-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1a86-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1a86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1a86-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="b1a86-106">[in] Toplam sayısı giriş `generationCollected` dizi.</span><span class="sxs-lookup"><span data-stu-id="b1a86-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="b1a86-107">[in] Boole değerleri olan bir dizi `true` dizi dizini karşılık gelen oluşturma, bu atık toplama tarafından toplanan Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="b1a86-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b1a86-108">Dizi değeri tarafından dizine [cor_prf_gc_generatıon](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) nesli belirten numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="b1a86-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="b1a86-109">[in] Değerini [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) çöp toplama nedenini belirten numaralandırma kopyaladığınızda.</span><span class="sxs-lookup"><span data-stu-id="b1a86-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1a86-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1a86-110">Remarks</span></span>  
 <span data-ttu-id="b1a86-111">Bu çöp toplama ilgilidir tüm geri aramalar arasında gerçekleşecek `GarbageCollectionStarted` geri çağırma ve karşılık gelen [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="b1a86-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="b1a86-112">Bu geri aramalar aynı iş parçacığı üzerinde meydana değil.</span><span class="sxs-lookup"><span data-stu-id="b1a86-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="b1a86-113">Nesneleri özgün konumlarına sırasında incelemek profil oluşturucu güvenlidir `GarbageCollectionStarted` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="b1a86-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="b1a86-114">Çöp toplayıcı dönüş sonra taşıma nesneleri başlar `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="b1a86-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="b1a86-115">Profil Oluşturucu bu geri aramasından döndürdü sonra Profil Oluşturucu aldığı kadar geçersiz olduğu tüm nesne kimlikleri dikkate almanız gereken bir `ICorProfilerCallback2::GarbageCollectionFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="b1a86-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a86-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1a86-116">Requirements</span></span>  
 <span data-ttu-id="b1a86-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a86-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a86-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1a86-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1a86-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1a86-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1a86-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a86-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a86-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1a86-121">See Also</span></span>  
 [<span data-ttu-id="b1a86-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1a86-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b1a86-123">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1a86-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
