---
title: "ICorProfilerCallback::MovedReferences Yöntemi"
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
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d62fbdf4b6dd2acbb67b0655938990d625f8df8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="07ffe-102">ICorProfilerCallback::MovedReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07ffe-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="07ffe-103">Yeni düzenini sıkıştırma çöp toplama sonucunda yığınındaki nesnelerin bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="07ffe-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07ffe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07ffe-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07ffe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07ffe-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="07ffe-106">[in] Sıkıştırma atık toplama sonucu olarak taşınmış bitişik nesnelerin bloğu sayısı.</span><span class="sxs-lookup"><span data-stu-id="07ffe-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="07ffe-107">Diğer bir deyişle, değeri `cMovedObjectIDRanges` toplam boyutu `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07ffe-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="07ffe-108">Sonraki üç bağımsız değişkenleri `MovedReferences` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="07ffe-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="07ffe-109">Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, ve `cObjectIDRangeLength[i]` tüm bitişik nesnelerinin tek bir blok ilgilendiren.</span><span class="sxs-lookup"><span data-stu-id="07ffe-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="07ffe-110">[in] Bir dizi `ObjectID` her biri başlangıç adresi bloğunun bitişik eski (ön çöp toplama) olduğunda, değerleri, bellekte nesneleri canlı.</span><span class="sxs-lookup"><span data-stu-id="07ffe-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="07ffe-111">[in] Bir dizi `ObjectID` her biri yeni (sonrası çöp toplama) başlangıç adresi bloğunun bitişik olduğunda, değerleri, bellekte nesneleri canlı.</span><span class="sxs-lookup"><span data-stu-id="07ffe-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="07ffe-112">[in] Her biri bir blok bellekte bitişik nesnelerin boyutudur dizisi.</span><span class="sxs-lookup"><span data-stu-id="07ffe-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="07ffe-113">Başvuru her blok için belirtilen bir boyutu `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07ffe-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07ffe-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07ffe-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07ffe-115">Bu yöntem olarak boyutlarını raporlar `MAX_ULONG` 64 bit platformlarda 4 GB'den büyük nesneler için.</span><span class="sxs-lookup"><span data-stu-id="07ffe-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="07ffe-116">4 GB'den büyük nesneleri boyutunu almak için [Icorprofilercallback4::movedreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="07ffe-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="07ffe-117">Sıkıştırma atık toplayıcı ölü nesneleri ve alan serbest sıkıştırır tarafından kapladığı bellek geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="07ffe-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="07ffe-118">Sonuç olarak, dinamik nesneler yığında taşınmış olabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerleri değişebilir.</span><span class="sxs-lookup"><span data-stu-id="07ffe-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="07ffe-119">Varsayımında varolan `ObjectID` değeri (`oldObjectID`) aşağıdaki aralık içinde yer:</span><span class="sxs-lookup"><span data-stu-id="07ffe-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="07ffe-120">Bu durumda, aralığın başlangıç uzaklığı nesneyi başlatmak için aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="07ffe-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="07ffe-121">Herhangi bir değer için `i` aşağıdaki aralıkta değil:</span><span class="sxs-lookup"><span data-stu-id="07ffe-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="07ffe-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="07ffe-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="07ffe-123">Yeni hesaplayabilirsiniz `ObjectID` gibi:</span><span class="sxs-lookup"><span data-stu-id="07ffe-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="07ffe-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="07ffe-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="07ffe-125">Hiçbiri `ObjectID` geçirilen değerlerinin `MovedReferences` çöp toplama için yeni konumlar eski konumlardan nesneleri taşıma ortasında olabileceği için geri çağırma sırasında kendisini geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07ffe-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="07ffe-126">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `MovedReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="07ffe-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="07ffe-127">A [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırma gösteren tüm nesneleri yeni konumlarına taşınmıştır ve İnceleme gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="07ffe-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ffe-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07ffe-128">Requirements</span></span>  
 <span data-ttu-id="07ffe-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ffe-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ffe-130">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07ffe-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07ffe-131">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07ffe-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07ffe-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ffe-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ffe-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07ffe-133">See Also</span></span>  
 [<span data-ttu-id="07ffe-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07ffe-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="07ffe-135">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07ffe-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [<span data-ttu-id="07ffe-136">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07ffe-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="07ffe-137">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="07ffe-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
