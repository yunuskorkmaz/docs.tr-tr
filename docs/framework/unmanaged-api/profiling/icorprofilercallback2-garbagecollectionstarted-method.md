---
title: ICorProfilerCallback2::GarbageCollectionStarted Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4f639f9794002748e1019821514c546e4f4429f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746875"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="1f6c2-102">ICorProfilerCallback2::GarbageCollectionStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f6c2-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="1f6c2-103">Kod profil oluşturucu, çöp toplama başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f6c2-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f6c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f6c2-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="1f6c2-106">[in] Giriş toplam sayısı `generationCollected` dizisi.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="1f6c2-107">[in] Bir dizi olan Boolean değerlerini `true` karşılık gelen dizi dizini oluşturma, bu çöp toplama tarafından toplanan; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="1f6c2-108">Dizi değeri tarafından dizinlenen [cor_prf_gc_generatıon](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) nesli belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="1f6c2-109">[in] Değerini [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) atık toplama nedeni belirten sabit listesi başlattığı.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f6c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f6c2-110">Remarks</span></span>  
 <span data-ttu-id="1f6c2-111">Bu atık koleksiyonuna ait tüm geri çağırmalar arasında gerçekleşir `GarbageCollectionStarted` geri çağırma ve karşılık gelen [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="1f6c2-112">Bu geri aramalarda aynı iş parçacığında ortaya değil.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="1f6c2-113">Nesneleri özgün konumlarına sırasında incelemek profil oluşturucu güvenlidir `GarbageCollectionStarted` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="1f6c2-114">Çöp toplayıcı, taşıma nesneleri dönüş sonra başlar `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="1f6c2-115">Profil Oluşturucu bu geri çağrısından döndürülen sonra Profil Oluşturucu aldığı kadar geçersiz olabilir. tüm nesne kimlikleri dikkate almanız gereken bir `ICorProfilerCallback2::GarbageCollectionFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f6c2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f6c2-116">Requirements</span></span>  
 <span data-ttu-id="1f6c2-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f6c2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f6c2-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f6c2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f6c2-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f6c2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f6c2-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6c2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6c2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f6c2-121">See also</span></span>

- [<span data-ttu-id="1f6c2-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f6c2-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1f6c2-123">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f6c2-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
