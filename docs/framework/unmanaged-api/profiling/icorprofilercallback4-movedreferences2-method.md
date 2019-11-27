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
ms.openlocfilehash: 37d5f5e8294bb87a8796d6dcae046864904b096b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439378"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="d89a0-102">ICorProfilerCallback4::MovedReferences2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a0-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="d89a0-103">Bir sıkıştırma atık toplama işleminin sonucu olarak yığında nesnelerin yeni yerleşimini raporlamak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d89a0-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="d89a0-104">Profil Oluşturucu [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d89a0-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="d89a0-105">Bu geri çağırma [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda neyin ifade edileceği daha büyük nesneler raporlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89a0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d89a0-106">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d89a0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d89a0-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="d89a0-108">'ndaki Sıkıştırma atık toplamanın sonucu olarak taşınan bitişik nesne bloklarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="d89a0-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="d89a0-109">Diğer bir deyişle, `cMovedObjectIDRanges` değeri `oldObjectIDRangeStart`, `newObjectIDRangeStart`ve `cObjectIDRangeLength` dizilerinin toplam boyutudur.</span><span class="sxs-lookup"><span data-stu-id="d89a0-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="d89a0-110">`MovedReferences2` sonraki üç bağımsız değişkeni paralel dizilerdir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="d89a0-111">Diğer bir deyişle, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`ve `cObjectIDRangeLength[i]` hepsi de tek bir bitişik nesne bloğuna sorun.</span><span class="sxs-lookup"><span data-stu-id="d89a0-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="d89a0-112">'ndaki Her biri, bellekte bulunan bir bitişik ve canlı nesneler bloğunun başlangıç adresi olan `ObjectID` değerlerden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="d89a0-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="d89a0-113">'ndaki Her biri, bellekte bir bitişik ve canlı nesneler bloğunun başlangıç adresinden yeni (çöp sonrası koleksiyon) olan `ObjectID` değerlerden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="d89a0-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="d89a0-114">'ndaki Her biri bellekteki bir bitişik nesne bloğunun boyutu olan tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="d89a0-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="d89a0-115">`oldObjectIDRangeStart` ve `newObjectIDRangeStart` dizileri içinde başvurulan her bir blok için bir boyut belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d89a0-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d89a0-116">Remarks</span></span>  
 <span data-ttu-id="d89a0-117">Bir sıkıştırma atık toplayıcısı, ölü nesneler tarafından kullanılan belleği geri kazanır ve serbest bırakılan alanı sıkıştırır.</span><span class="sxs-lookup"><span data-stu-id="d89a0-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="d89a0-118">Sonuç olarak, canlı nesneler yığın içinde taşınabilir ve önceki bildirimler tarafından dağıtılan `ObjectID` değerleri değişebilir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="d89a0-119">Mevcut bir `ObjectID` değerinin (`oldObjectID`) aşağıdaki aralıkta olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="d89a0-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="d89a0-120">Bu durumda, aralığın başlangıcından nesnenin başlangıcına kadar olan fark aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d89a0-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="d89a0-121">Aşağıdaki aralıktaki `i` herhangi bir değeri için:</span><span class="sxs-lookup"><span data-stu-id="d89a0-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="d89a0-122">0 < = `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="d89a0-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="d89a0-123">Yeni `ObjectID` aşağıdaki gibi hesaplayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d89a0-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="d89a0-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID`-`oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="d89a0-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="d89a0-125">Çöp toplayıcı nesneleri eski konumlardan yeni konumlara taşıma işleminin ortasında olabileceğinden, geri çağırma sırasında `MovedReferences2` tarafından geçirilen `ObjectID` değerlerinden hiçbiri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="d89a0-126">Bu nedenle, profil oluşturucular `MovedReferences2` çağrısı sırasında nesneleri incelemeyi denememelidir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="d89a0-127">[ICorProfilerCallback2:: GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması, tüm nesnelerin yeni konumlarına taşındığını ve incelemesinin gerçekleştirilebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="d89a0-128">Profiler hem [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimlerini uygularsa, `MovedReferences2` yöntemi [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `MovedReferences2` yöntemi başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d89a0-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="d89a0-129">Profil oluşturucular, ikinci yöntemi çağırmayı önlemek için `MovedReferences2` yönteminden hata belirten bir HRESULT döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d89a0-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89a0-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d89a0-130">Requirements</span></span>  
 <span data-ttu-id="d89a0-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d89a0-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d89a0-132">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d89a0-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d89a0-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d89a0-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d89a0-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89a0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89a0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d89a0-135">See also</span></span>

- [<span data-ttu-id="d89a0-136">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89a0-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d89a0-137">MovedReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89a0-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="d89a0-138">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89a0-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="d89a0-139">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d89a0-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d89a0-140">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d89a0-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
