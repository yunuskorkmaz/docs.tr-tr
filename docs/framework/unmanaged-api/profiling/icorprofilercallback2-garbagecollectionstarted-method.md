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
ms.openlocfilehash: f025f4c0bc0ec8e11decddcdf64be50f68955266
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499811"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="b5838-102">ICorProfilerCallback2::GarbageCollectionStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5838-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="b5838-103">Çöp toplamanın başlattığı kod Profilcisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="b5838-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5838-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b5838-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5838-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5838-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="b5838-106">'ndaki Dizideki toplam girdi sayısı `generationCollected` .</span><span class="sxs-lookup"><span data-stu-id="b5838-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="b5838-107">'ndaki `true`Dizi dizinine karşılık gelen nesil bu çöp toplama tarafından toplanıyorsa bir Boole değeri dizisi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="b5838-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="b5838-108">Dizi, oluşturmayı gösteren [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) numaralandırması değeri ile dizinlenir.</span><span class="sxs-lookup"><span data-stu-id="b5838-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="b5838-109">'ndaki Çöp toplamanın oluşturulma nedenini gösteren [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="b5838-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5838-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5838-110">Remarks</span></span>  
 <span data-ttu-id="b5838-111">Bu çöp toplama ile ilgili tüm geri çağrılar, `GarbageCollectionStarted` geri çağırma ve karşılık gelen [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması arasında gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="b5838-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="b5838-112">Bu geri aramalar aynı iş parçacığında gerçekleşmemelidir.</span><span class="sxs-lookup"><span data-stu-id="b5838-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="b5838-113">Profil oluşturucunun geri çağırma sırasında özgün konumlarında nesneleri incelemesi güvenlidir `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="b5838-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="b5838-114">Çöp toplayıcı, öğesinden dönüşten sonra nesneleri taşımaya başlayacaktır `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="b5838-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="b5838-115">Profil Oluşturucu bu geri aramadan çağrıldıktan sonra, profil oluşturucu, bir geri arama alıncaya kadar tüm nesne kimliklerini geçersiz hale getirmelidir `ICorProfilerCallback2::GarbageCollectionFinished` .</span><span class="sxs-lookup"><span data-stu-id="b5838-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5838-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5838-116">Requirements</span></span>  
 <span data-ttu-id="b5838-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5838-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5838-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b5838-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5838-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b5838-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5838-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5838-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5838-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5838-121">See also</span></span>

- [<span data-ttu-id="b5838-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5838-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b5838-123">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5838-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
