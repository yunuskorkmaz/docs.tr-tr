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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3e21d42340378c576bfc65750fba26a257b82cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457752"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="b3c55-102">ICorProfilerCallback4::ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3c55-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="b3c55-103">Profil Oluşturucu tam zamanında (JIT) derleyici işlevi yeniden derleyin başladıktan bildirir.</span><span class="sxs-lookup"><span data-stu-id="b3c55-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c55-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3c55-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3c55-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3c55-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b3c55-106">[in] JIT Derleyici yeniden derleyin başladıktan işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="b3c55-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="b3c55-107">[in] İşlev yeni sürümünü yeniden derlenmek kimliği.</span><span class="sxs-lookup"><span data-stu-id="b3c55-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="b3c55-108">[in] `true` engelleme bu geri aramasından; döndürülecek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir belirtmek için `false` engelleme işlemi çalışma zamanının etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b3c55-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="b3c55-109">Değerini `true` çalışma zamanı zarar değil, ancak profil sonuçları etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b3c55-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3c55-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3c55-110">Remarks</span></span>  
 <span data-ttu-id="b3c55-111">Birden fazla Çifti almak mümkündür `ReJITCompilationStarted` ve [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) yöntemini çağırır için her işlevi nedeniyle şekilde çalışma zamanı tanıtıcıları sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="b3c55-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="b3c55-112">Örneğin, çalışma zamanı yöntemi A derlenir başlar, ancak sınıf B sınıf oluşturucusu çalıştırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="b3c55-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="b3c55-113">Bu nedenle, çalışma zamanı Sınıf B Oluşturucusu yeniden derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b3c55-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="b3c55-114">Oluşturucusu çalışırken yeniden derlenmesi için bir yöntem neden olan bir yöntemine bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="b3c55-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="b3c55-115">Bu senaryoda, A yönteminin ilk yeniden derlenmek durdurulur.</span><span class="sxs-lookup"><span data-stu-id="b3c55-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="b3c55-116">Bununla birlikte, her ikisi de saldırılara JIT derleme olayları ile bir rapor yöntemi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="b3c55-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="b3c55-117">Profil oluşturucular JIT derleme geri aramalar dizisini iki iş parçacığı aynı anda yapıyor geri aramalar olduğu durumlarda desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3c55-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="b3c55-118">Örneğin, iş parçacığı A çağırır `ReJITCompilationStarted`; ancak, iş parçacığı A çağrıları önce [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) işlevi kimliği gelen `ReJITCompilationStarted` iş parçacığı A. için geri çağırma İşlev kimliği henüz geçerli olmamalıdır, görünebilir için yapılan bir çağrı [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) henüz Profil Oluşturucu tarafından almadı.</span><span class="sxs-lookup"><span data-stu-id="b3c55-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="b3c55-119">Ancak, bu durumda, işlev kimliği geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="b3c55-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c55-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3c55-120">Requirements</span></span>  
 <span data-ttu-id="b3c55-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3c55-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c55-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3c55-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3c55-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3c55-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3c55-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c55-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c55-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3c55-125">See Also</span></span>  
 [<span data-ttu-id="b3c55-126">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c55-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b3c55-127">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3c55-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="b3c55-128">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3c55-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="b3c55-129">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3c55-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
