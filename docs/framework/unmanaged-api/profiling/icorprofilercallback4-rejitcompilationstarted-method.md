---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback4:: ReJITCompilationStarted yöntemi'
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
ms.openlocfilehash: 7656f68ff6b10dcd58e48df212a036a590d0c3b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788715"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="9ac78-103">ICorProfilerCallback4::ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ac78-103">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>

<span data-ttu-id="9ac78-104">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="9ac78-104">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac78-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ac78-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac78-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ac78-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="9ac78-107">'ndaki JıT derleyicisinin yeniden derlenmeye başladığı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9ac78-107">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="9ac78-108">'ndaki İşlevin yeni sürümünün yeniden derlenmesi KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9ac78-108">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="9ac78-109">[in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false` engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="9ac78-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="9ac78-110">Bir değeri `true` çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9ac78-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac78-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ac78-111">Remarks</span></span>  

 <span data-ttu-id="9ac78-112">`ReJITCompilationStarted`Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla çift ve [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) Yöntem çağrısı almak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9ac78-112">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="9ac78-113">Örneğin, çalışma zamanı A metodunu yeniden dermaya başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ac78-113">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="9ac78-114">Bu nedenle, çalışma zamanı oluşturucuyu B sınıfı için yeniden derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9ac78-114">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="9ac78-115">Oluşturucu çalışırken, a yöntemine bir çağrı yapar, bu da Yöntem A 'nın yeniden derlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9ac78-115">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="9ac78-116">Bu senaryoda, A yönteminin ilk yeniden derlenmesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="9ac78-116">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="9ac78-117">Ancak, her iki yöntemi de derleme yeniden derleme olayları ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="9ac78-117">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="9ac78-118">Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT yeniden derleme geri çağırmaları dizisini desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="9ac78-118">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="9ac78-119">Örneğin, bir çağrı iş parçacığı `ReJITCompilationStarted` ; ancak, iş parçacığı a çağrısı [yeniden](icorprofilercallback4-rejitcompilationfinished-method.md)denemeden önce, iş parçacığı B, iş parçacığı a Için geri aramadan [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' ı çağırır `ReJITCompilationStarted` . Bir [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) çağrısı henüz profil oluşturucu tarafından alınmadığından, işlev kimliğinin henüz geçerli olmaması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="9ac78-119">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="9ac78-120">Ancak, bu durumda, işlev KIMLIĞI geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="9ac78-120">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac78-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ac78-121">Requirements</span></span>  

 <span data-ttu-id="9ac78-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac78-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac78-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9ac78-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ac78-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9ac78-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ac78-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac78-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac78-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ac78-126">See also</span></span>

- [<span data-ttu-id="9ac78-127">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ac78-127">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9ac78-128">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ac78-128">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="9ac78-129">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ac78-129">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="9ac78-130">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ac78-130">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
