---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback2:: GarbageCollectionStarted yöntemi'
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
ms.openlocfilehash: 2b57a21dc3a1751b5d4767ea940f64df61af4318
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647888"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="563e5-103">ICorProfilerCallback2::GarbageCollectionStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="563e5-103">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>

<span data-ttu-id="563e5-104">Çöp toplamanın başlattığı kod Profilcisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="563e5-104">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="563e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="563e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="563e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="563e5-106">Parameters</span></span>  

 `cGenerations`  
 <span data-ttu-id="563e5-107">'ndaki Dizideki toplam girdi sayısı `generationCollected` .</span><span class="sxs-lookup"><span data-stu-id="563e5-107">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="563e5-108">'ndaki `true` Dizi dizinine karşılık gelen nesil bu çöp toplama tarafından toplanıyorsa bir Boole değeri dizisi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="563e5-108">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="563e5-109">Dizi, oluşturmayı gösteren [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) numaralandırması değeri ile dizinlenir.</span><span class="sxs-lookup"><span data-stu-id="563e5-109">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="563e5-110">'ndaki Çöp toplamanın oluşturulma nedenini gösteren [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="563e5-110">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="563e5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="563e5-111">Remarks</span></span>  

 <span data-ttu-id="563e5-112">Bu çöp toplama ile ilgili tüm geri çağrılar, `GarbageCollectionStarted` geri çağırma ve karşılık gelen [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) geri çağırması arasında gerçekleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="563e5-112">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="563e5-113">Bu geri aramalar aynı iş parçacığında gerçekleşmemelidir.</span><span class="sxs-lookup"><span data-stu-id="563e5-113">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="563e5-114">Profil oluşturucunun geri çağırma sırasında özgün konumlarında nesneleri incelemesi güvenlidir `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="563e5-114">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="563e5-115">Çöp toplayıcı, öğesinden dönüşten sonra nesneleri taşımaya başlayacaktır `GarbageCollectionStarted` .</span><span class="sxs-lookup"><span data-stu-id="563e5-115">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="563e5-116">Profil Oluşturucu bu geri aramadan çağrıldıktan sonra, profil oluşturucu, bir geri arama alıncaya kadar tüm nesne kimliklerini geçersiz hale getirmelidir `ICorProfilerCallback2::GarbageCollectionFinished` .</span><span class="sxs-lookup"><span data-stu-id="563e5-116">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="563e5-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="563e5-117">Requirements</span></span>  

 <span data-ttu-id="563e5-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="563e5-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="563e5-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="563e5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="563e5-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="563e5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="563e5-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="563e5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563e5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="563e5-122">See also</span></span>

- [<span data-ttu-id="563e5-123">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="563e5-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="563e5-124">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="563e5-124">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
