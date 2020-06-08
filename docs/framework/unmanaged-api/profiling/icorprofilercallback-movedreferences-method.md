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
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503347"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="3dc13-102">ICorProfilerCallback::MovedReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dc13-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="3dc13-103">Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3dc13-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc13-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3dc13-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dc13-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dc13-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="3dc13-106">'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="3dc13-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="3dc13-107">Diğer bir deyişle, değeri `cMovedObjectIDRanges` `oldObjectIDRangeStart` ,, `newObjectIDRangeStart` ve dizilerinin toplam boyutudur `cObjectIDRangeLength` .</span><span class="sxs-lookup"><span data-stu-id="3dc13-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="3dc13-108">Sonraki üç bağımsız değişkeni `MovedReferences` paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="3dc13-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="3dc13-109">Diğer bir deyişle, `oldObjectIDRangeStart[i]` , `newObjectIDRangeStart[i]` ve `cObjectIDRangeLength[i]` hepsi bitişik nesnelerin tek bir bloğuna sorun.</span><span class="sxs-lookup"><span data-stu-id="3dc13-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="3dc13-110">'ndaki `ObjectID`Her biri, bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan, her biri eski (çöp önden koleksiyon) olan bir değerler dizisi.</span><span class="sxs-lookup"><span data-stu-id="3dc13-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="3dc13-111">'ndaki `ObjectID`Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan yeni (çöp sonrası koleksiyon) olan bir değer dizisidir.</span><span class="sxs-lookup"><span data-stu-id="3dc13-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="3dc13-112">'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="3dc13-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="3dc13-113">Ve dizilerinde başvurulan her bir blok için bir boyut belirtilir `oldObjectIDRangeStart` `newObjectIDRangeStart` .</span><span class="sxs-lookup"><span data-stu-id="3dc13-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc13-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dc13-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3dc13-115">Bu yöntem `MAX_ULONG` , 64-bit platformlarda 4 GB 'den büyük nesneler için boyutları raporlar.</span><span class="sxs-lookup"><span data-stu-id="3dc13-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="3dc13-116">4 GB 'den büyük nesnelerin boyutunu almak için, bunun yerine [ICorProfilerCallback4:: MovedReferences2](icorprofilercallback4-movedreferences2-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3dc13-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="3dc13-117">Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır.</span><span class="sxs-lookup"><span data-stu-id="3dc13-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="3dc13-118">Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="3dc13-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="3dc13-119">Var olan bir `ObjectID` değerin ( `oldObjectID` ) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="3dc13-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="3dc13-120">Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3dc13-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="3dc13-121">Aşağıdaki aralıkta olan herhangi bir değeri için `i` :</span><span class="sxs-lookup"><span data-stu-id="3dc13-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="3dc13-122">0 <=`i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="3dc13-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="3dc13-123">Yeni ' ni `ObjectID` aşağıda gösterildiği gibi hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3dc13-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="3dc13-124">`newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )</span><span class="sxs-lookup"><span data-stu-id="3dc13-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="3dc13-125">`ObjectID` `MovedReferences` Çöp toplama nesneleri eski konumlardan yeni konumlara taşıma işleminin ortasında olabileceğinden, tarafından geçirilen değerlerin hiçbiri geri çağırma sırasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="3dc13-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="3dc13-126">Bu nedenle, profil oluşturucular bir çağrı sırasında nesneleri incelemeyi denememelidir `MovedReferences` .</span><span class="sxs-lookup"><span data-stu-id="3dc13-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="3dc13-127">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3dc13-127">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dc13-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dc13-128">Requirements</span></span>  
 <span data-ttu-id="3dc13-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dc13-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dc13-130">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3dc13-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3dc13-131">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3dc13-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dc13-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dc13-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc13-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dc13-133">See also</span></span>

- [<span data-ttu-id="3dc13-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dc13-134">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3dc13-135">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dc13-135">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="3dc13-136">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3dc13-136">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3dc13-137">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3dc13-137">Profiling</span></span>](index.md)
