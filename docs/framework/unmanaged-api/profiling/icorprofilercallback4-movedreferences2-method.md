---
title: ICorProfilerCallback4::MovedReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b6dd32d63fc856b67f8e7d64be31dcbf107b10b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531034"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="4df63-102">ICorProfilerCallback4::MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4df63-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="4df63-103">Yeni düzen sıkıştırma çöp toplama sonucu olarak yığındaki nesnelerin bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4df63-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="4df63-104">Profil Oluşturucu uygulanırsa, bu yöntem çağrılır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4df63-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="4df63-105">Bu geri çağırma değiştirir [Icorprofilercallback::movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yöntemi, daha büyük olan uzunluğu aşan bir ULONG ifade edilebilir nesne aralıklarını rapor edebilirsiniz çünkü.</span><span class="sxs-lookup"><span data-stu-id="4df63-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df63-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4df63-106">Syntax</span></span>  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4df63-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4df63-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="4df63-108">[in] Taşınabilir sıkıştırma çöp toplama işleminin sonucu olarak, bitişik nesnelerin blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="4df63-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="4df63-109">Diğer bir deyişle, değerini `cMovedObjectIDRanges` toplam boyutu `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizileri.</span><span class="sxs-lookup"><span data-stu-id="4df63-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="4df63-110">Sonraki üç bağımsız değişkenleri `MovedReferences2` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="4df63-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="4df63-111">Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, ve `cObjectIDRangeLength[i]` tüm bitişik nesnelerinin tek bir blok ilgilendiriyor.</span><span class="sxs-lookup"><span data-stu-id="4df63-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="4df63-112">[in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik eski (ön çöp toplamada) olduğunda, değerleri, Canlı nesneleri bellekte.</span><span class="sxs-lookup"><span data-stu-id="4df63-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="4df63-113">[in] Bir dizi `ObjectID` her biri yeni (sonrası çöp toplamada) başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.</span><span class="sxs-lookup"><span data-stu-id="4df63-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="4df63-114">[in] Her biri bellekte bitişik nesnelerin bir blok boyutu olan bir tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="4df63-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="4df63-115">Başvurulduğundan her blok için belirtilen bir boyutu `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri.</span><span class="sxs-lookup"><span data-stu-id="4df63-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df63-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4df63-116">Remarks</span></span>  
 <span data-ttu-id="4df63-117">Sıkıştırma atık Toplayıcıya alanı boşaltılana sıkıştırır ve ölü nesneleri ile kapladığı belleği geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="4df63-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="4df63-118">Sonuç olarak, Canlı nesneler yığında taşınmış olabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerleri değişebilir.</span><span class="sxs-lookup"><span data-stu-id="4df63-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="4df63-119">Varsayımında varolan `ObjectID` değeri (`oldObjectID`) aşağıdaki aralığında yer:</span><span class="sxs-lookup"><span data-stu-id="4df63-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="4df63-120">Bu durumda, nesnenin başlangıç aralığın başından uzaklık şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="4df63-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="4df63-121">İçin herhangi bir değerini `i` aşağıdaki aralığında olan:</span><span class="sxs-lookup"><span data-stu-id="4df63-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="4df63-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="4df63-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="4df63-123">Yeni hesaplayabilirsiniz `ObjectID` gibi:</span><span class="sxs-lookup"><span data-stu-id="4df63-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="4df63-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="4df63-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="4df63-125">Hiçbiri `ObjectID` geçirilen değerler `MovedReferences2` geri çağırma sırasındaki kendisi, çöp toplayıcının nesneleri eski konumlardan yeni konumlara taşımak ortasında olabileceğinden geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="4df63-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="4df63-126">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `MovedReferences2` çağırın.</span><span class="sxs-lookup"><span data-stu-id="4df63-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="4df63-127">A [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) tüm nesnelerin yeni konumlarına taşınmıştır ve İnceleme gerçekleştirilebilir geri çağırma işlemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4df63-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="4df63-128">Profil Oluşturucu hem de uyguluyorsa [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimleri `MovedReferences2` önce yöntemi çağrıldığında [Icorprofilercallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yöntemi, ancak yalnızca `MovedReferences2` yöntemi başarıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="4df63-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="4df63-129">Profil oluşturucular hatasından gösteren HRESULT döndürebilir `MovedReferences2` ikinci yöntem çağırma önlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4df63-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df63-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4df63-130">Requirements</span></span>  
 <span data-ttu-id="4df63-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df63-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df63-132">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4df63-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4df63-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4df63-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4df63-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df63-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df63-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4df63-135">See also</span></span>
- [<span data-ttu-id="4df63-136">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4df63-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4df63-137">MovedReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4df63-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="4df63-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4df63-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="4df63-139">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4df63-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4df63-140">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4df63-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
