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
ms.openlocfilehash: f86c4388fd633c72e846c227d45eff09bb66cf44
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951115"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="e1bc0-102">ICorProfilerCallback::MovedReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1bc0-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="e1bc0-103">Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bc0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1bc0-104">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1bc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1bc0-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="e1bc0-106">'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="e1bc0-107">Diğer `cMovedObjectIDRanges` bir deyişle, değeri `oldObjectIDRangeStart`, `newObjectIDRangeStart`, ve `cObjectIDRangeLength` dizilerinin toplam boyutudur.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="e1bc0-108">Sonraki üç bağımsız değişkeni `MovedReferences` paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="e1bc0-109">Diğer bir deyişle `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]`,, ve `cObjectIDRangeLength[i]` hepsi bitişik nesnelerin tek bir bloğuna sorun.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="e1bc0-110">'ndaki Her biri, `ObjectID` bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan, her biri eski (çöp önden koleksiyon) olan bir değerler dizisi.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="e1bc0-111">'ndaki Her biri, `ObjectID` bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan yeni (çöp sonrası koleksiyon) olan bir değer dizisidir.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="e1bc0-112">'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="e1bc0-113">`oldObjectIDRangeStart` Ve`newObjectIDRangeStart` dizilerinde başvurulan her bir blok için bir boyut belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1bc0-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1bc0-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e1bc0-115">Bu yöntem, 64- `MAX_ULONG` bit platformlarda 4 GB 'den büyük nesneler için boyutları raporlar.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="e1bc0-116">4 GB 'den büyük nesnelerin boyutunu almak için, bunun yerine [ICorProfilerCallback4:: MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="e1bc0-117">Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="e1bc0-118">Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve `ObjectID` önceki bildirimler tarafından dağıtılan değerler değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="e1bc0-119">Var olan `ObjectID` bir değerin (`oldObjectID`) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="e1bc0-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="e1bc0-120">Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e1bc0-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="e1bc0-121">Aşağıdaki aralıkta `i` olan herhangi bir değeri için:</span><span class="sxs-lookup"><span data-stu-id="e1bc0-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="e1bc0-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="e1bc0-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="e1bc0-123">Yeni ' ni `ObjectID` aşağıda gösterildiği gibi hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1bc0-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="e1bc0-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="e1bc0-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="e1bc0-125">Çöp toplama nesneleri eski konumlardan yeni `MovedReferences` konumlara taşıma işleminin ortasında olabileceğinden, tarafından geçirilen değerlerinhiçbirigeriçağırmasırasındageçerlideğildir.`ObjectID`</span><span class="sxs-lookup"><span data-stu-id="e1bc0-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="e1bc0-126">Bu nedenle, profil oluşturucular bir `MovedReferences` çağrı sırasında nesneleri incelemeyi denememelidir.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="e1bc0-127">[ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1bc0-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1bc0-128">Requirements</span></span>  
 <span data-ttu-id="e1bc0-129">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1bc0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1bc0-130">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e1bc0-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1bc0-131">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1bc0-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1bc0-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1bc0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1bc0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1bc0-133">See also</span></span>

- [<span data-ttu-id="e1bc0-134">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1bc0-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e1bc0-135">MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1bc0-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="e1bc0-136">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e1bc0-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e1bc0-137">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1bc0-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
