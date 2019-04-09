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
ms.openlocfilehash: b8f2ada73686dfbe5629e21cfc6468becbd4ccc5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075905"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="c23c3-102">ICorProfilerCallback4::ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c23c3-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="c23c3-103">Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi yeniden derle başladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="c23c3-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c23c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c23c3-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c23c3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c23c3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c23c3-106">[in] JIT derleyicisi yeniden derle başladı işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="c23c3-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="c23c3-107">[in] İşlevi yeni sürümünü yeniden derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="c23c3-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="c23c3-108">[in] `true` engelleme bu geri çağrısından; döndürmek çağıran iş parçacığını beklemek çalışma zamanı neden olabileceğini göstermek için `false` engelleme zamanının işlemi etkilemez belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="c23c3-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="c23c3-109">Değerini `true` çalışma zamanı zarar değil, ancak profil oluşturma sonuçlarından etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c23c3-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c23c3-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c23c3-110">Remarks</span></span>  
 <span data-ttu-id="c23c3-111">Birden fazla çiftinin almak mümkündür `ReJITCompilationStarted` ve [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) yöntemini çağırır her işlev için şekli nedeniyle çalışma zamanı sınıf oluşturucuları işler.</span><span class="sxs-lookup"><span data-stu-id="c23c3-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="c23c3-112">Örneğin, bir yöntem yeniden derlemek çalışma zamanı başlatmaz, bunun Sınıf B sınıf oluşturucusu çalıştırılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="c23c3-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="c23c3-113">Bu nedenle, çalışma zamanı Sınıf B için oluşturucu yeniden derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c23c3-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="c23c3-114">Oluşturucu çalışırken yeniden derlenmesi için bir yöntem neden olan bir yönteme bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="c23c3-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="c23c3-115">Bu senaryoda, bir yöntemin ilk yeniden derleme işlemi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="c23c3-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="c23c3-116">Ancak, her ikisi de dener JIT yeniden derleme olayları ile bir rapor yöntemi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="c23c3-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="c23c3-117">Profil oluşturucular JIT yeniden derleme geri çağırmalar dizisi, burada iki iş parçacığı geri çağırmaları aynı anda çağırıyorsanız durumlarda desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c23c3-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="c23c3-118">Örneğin, bir iş parçacığı çağrı `ReJITCompilationStarted`; ancak, bir dizi çağrıları önce [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) işlevi kimliği gelen `ReJITCompilationStarted` A. iş parçacığı için geri çağırma İşlev kimliği henüz geçerli gerektiğini görünebilir çünkü bir çağrı [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) henüz Profil Oluşturucu tarafından almadı.</span><span class="sxs-lookup"><span data-stu-id="c23c3-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="c23c3-119">Ancak, bu durumda, işlev kimliği geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="c23c3-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c23c3-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c23c3-120">Requirements</span></span>  
 <span data-ttu-id="c23c3-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c23c3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c23c3-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c23c3-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c23c3-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c23c3-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c23c3-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c23c3-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c23c3-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c23c3-125">See also</span></span>

- [<span data-ttu-id="c23c3-126">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c23c3-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c23c3-127">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c23c3-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="c23c3-128">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c23c3-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="c23c3-129">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c23c3-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
