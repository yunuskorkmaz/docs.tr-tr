---
title: ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 6e340fa08800f31d36e6cfb280cac847a4fca548
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499356"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="48005-102">ICorProfilerCallback4::ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48005-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="48005-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="48005-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48005-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="48005-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48005-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48005-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="48005-106">'ndaki JıT derleyicisinin yeniden derlenmeye başladığı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="48005-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="48005-107">'ndaki İşlevin yeni sürümünün yeniden derlenmesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="48005-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="48005-108">[in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="48005-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="48005-109">Bir değeri `true` çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="48005-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48005-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48005-110">Remarks</span></span>  
 <span data-ttu-id="48005-111">`ReJITCompilationStarted`Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla çift ve [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) Yöntem çağrısı almak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="48005-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="48005-112">Örneğin, çalışma zamanı A metodunu yeniden dermaya başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48005-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="48005-113">Bu nedenle, çalışma zamanı oluşturucuyu B sınıfı için yeniden derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="48005-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="48005-114">Oluşturucu çalışırken, a yöntemine bir çağrı yapar, bu da Yöntem A 'nın yeniden derlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="48005-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="48005-115">Bu senaryoda, A yönteminin ilk yeniden derlenmesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="48005-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="48005-116">Ancak, her iki yöntemi de derleme yeniden derleme olayları ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="48005-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="48005-117">Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT yeniden derleme geri çağırmaları dizisini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="48005-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="48005-118">Örneğin, bir çağrı iş parçacığı `ReJITCompilationStarted` ; ancak, iş parçacığı a çağrısı [yeniden](icorprofilercallback4-rejitcompilationfinished-method.md)denemeden önce, iş parçacığı B, iş parçacığı a Için geri aramadan [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' ı çağırır `ReJITCompilationStarted` . Bir [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) çağrısı henüz profil oluşturucu tarafından alınmadığından, işlev kimliğinin henüz geçerli olmaması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="48005-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="48005-119">Ancak, bu durumda, işlev KIMLIĞI geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="48005-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48005-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48005-120">Requirements</span></span>  
 <span data-ttu-id="48005-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48005-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48005-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48005-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48005-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="48005-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48005-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48005-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48005-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48005-125">See also</span></span>

- [<span data-ttu-id="48005-126">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48005-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="48005-127">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48005-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="48005-128">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48005-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="48005-129">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48005-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
