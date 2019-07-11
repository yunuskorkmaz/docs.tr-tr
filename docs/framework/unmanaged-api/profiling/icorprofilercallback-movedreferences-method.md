---
title: ICorProfilerCallback::MovedReferences Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c037f2509aaa0a5e4c3f7a844614742b6f21bec3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769143"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="9740c-102">ICorProfilerCallback::MovedReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9740c-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="9740c-103">Yeni düzen sıkıştırma çöp toplama sonucu olarak yığındaki nesnelerin bildirmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9740c-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9740c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9740c-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9740c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9740c-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="9740c-106">[in] Taşınabilir sıkıştırma çöp toplama işleminin sonucu olarak, bitişik nesnelerin blokların sayısı.</span><span class="sxs-lookup"><span data-stu-id="9740c-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="9740c-107">Diğer bir deyişle, değerini `cMovedObjectIDRanges` toplam boyutu `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizileri.</span><span class="sxs-lookup"><span data-stu-id="9740c-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="9740c-108">Sonraki üç bağımsız değişkenleri `MovedReferences` paralel dizidir.</span><span class="sxs-lookup"><span data-stu-id="9740c-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="9740c-109">Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, ve `cObjectIDRangeLength[i]` tüm bitişik nesnelerinin tek bir blok ilgilendiriyor.</span><span class="sxs-lookup"><span data-stu-id="9740c-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="9740c-110">[in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik eski (ön çöp toplamada) olduğunda, değerleri, Canlı nesneleri bellekte.</span><span class="sxs-lookup"><span data-stu-id="9740c-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="9740c-111">[in] Bir dizi `ObjectID` her biri yeni (sonrası çöp toplamada) başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.</span><span class="sxs-lookup"><span data-stu-id="9740c-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="9740c-112">[in] Her biri bellekte bitişik nesnelerin bir blok boyutu olan bir tamsayı dizisi.</span><span class="sxs-lookup"><span data-stu-id="9740c-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="9740c-113">Başvurulduğundan her blok için belirtilen bir boyutu `oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri.</span><span class="sxs-lookup"><span data-stu-id="9740c-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9740c-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9740c-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9740c-115">Bu yöntem boyutları olarak raporlar `MAX_ULONG` 64-bit platformlarda 4 GB'den büyük olan nesneler için.</span><span class="sxs-lookup"><span data-stu-id="9740c-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="9740c-116">4 GB'den daha büyük nesnelerin boyutunu almak için kullanın [Icorprofilercallback4::movedreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="9740c-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="9740c-117">Sıkıştırma atık Toplayıcıya alanı boşaltılana sıkıştırır ve ölü nesneleri ile kapladığı belleği geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="9740c-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="9740c-118">Sonuç olarak, Canlı nesneler yığında taşınmış olabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerleri değişebilir.</span><span class="sxs-lookup"><span data-stu-id="9740c-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="9740c-119">Varsayımında varolan `ObjectID` değeri (`oldObjectID`) aşağıdaki aralığında yer:</span><span class="sxs-lookup"><span data-stu-id="9740c-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="9740c-120">Bu durumda, nesnenin başlangıç aralığın başından uzaklık şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="9740c-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="9740c-121">İçin herhangi bir değerini `i` aşağıdaki aralığında olan:</span><span class="sxs-lookup"><span data-stu-id="9740c-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="9740c-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="9740c-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="9740c-123">Yeni hesaplayabilirsiniz `ObjectID` gibi:</span><span class="sxs-lookup"><span data-stu-id="9740c-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="9740c-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="9740c-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="9740c-125">Hiçbiri `ObjectID` geçirilen değerler `MovedReferences` geri çağırma sırasındaki kendisi, çöp toplama nesneleri eski konumlardan yeni konumlara taşımak ortasında olabileceği için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9740c-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="9740c-126">Bu nedenle, profil oluşturucular sırasında nesneleri incelemek çalışmamalısınız bir `MovedReferences` çağırın.</span><span class="sxs-lookup"><span data-stu-id="9740c-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="9740c-127">A [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) tüm nesnelerin yeni konumlarına taşınmıştır ve İnceleme gerçekleştirilebilir geri çağırma işlemini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9740c-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9740c-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9740c-128">Requirements</span></span>  
 <span data-ttu-id="9740c-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9740c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9740c-130">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9740c-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9740c-131">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9740c-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9740c-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9740c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9740c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9740c-133">See also</span></span>

- [<span data-ttu-id="9740c-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9740c-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9740c-135">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9740c-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="9740c-136">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9740c-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="9740c-137">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9740c-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
