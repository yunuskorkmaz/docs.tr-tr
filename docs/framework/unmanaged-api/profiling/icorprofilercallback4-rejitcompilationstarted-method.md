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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177090"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="d5a6d-102">ICorProfilerCallback4::ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5a6d-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="d5a6d-103">Profil oluşturucuya, tam zamanında (JIT) derleyicinin bir işlevi yeniden derlemeye başladığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5a6d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5a6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5a6d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d5a6d-106">[içinde] JIT derleyicisinin yeniden derlemeye başladığı işlevin kimliği.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="d5a6d-107">[içinde] İşlevin yeni sürümünün derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="d5a6d-108">[içinde] `true` engellemenin çalışma zamanının arama iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini belirtmek için; `false` engellemenin çalışma zamanının çalışmasını etkilemeyeceğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="d5a6d-109">Bir değer `true` çalışma süresine zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5a6d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5a6d-110">Remarks</span></span>  
 <span data-ttu-id="d5a6d-111">Çalışma zamanı sınıf oluşturucuları `ReJITCompilationStarted` işleme yolu nedeniyle birden fazla çift ve [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) yöntemi her işlev için çağrı almak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="d5a6d-112">Örneğin, çalışma zamanı Yöntem A'yı yeniden derlemeye başlar, ancak B sınıfının sınıf oluşturucusu çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="d5a6d-113">Bu nedenle, çalışma zamanı B sınıfı için oluşturucuyu yeniden derler ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="d5a6d-114">Oluşturucu çalışırken, A yönteminin yeniden derlenmesine neden olan A yöntemini arar.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="d5a6d-115">Bu senaryoda, A yönteminin ilk derlemesi durdurulur.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="d5a6d-116">Ancak, her iki yöntem A yeniden derlemek için JIT yeniden derleme olayları ile bildirilir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="d5a6d-117">Profilciler, iki iş parçacığının aynı anda geri arama yaptığı durumlarda JIT yeniden derleme geri aramalarının sırasını desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="d5a6d-118">Örneğin, iş parçacığı `ReJITCompilationStarted`A çağırır; ancak, iş parçacığı Önce Bir aramaları [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), iş parçacığı B aramaları [ICorProfilerCallback çağırır::ExceptionSearchSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) iş parçacığı a için `ReJITCompilationStarted` geri arama işlev kimliği ile. [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) için bir çağrı henüz profiloluşturucu tarafından alınmamıştı, çünkü işlev kimliği henüz geçerli olmamalıdır görünebilir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="d5a6d-119">Ancak, bu durumda, işlev kimliği geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5a6d-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5a6d-120">Requirements</span></span>  
 <span data-ttu-id="d5a6d-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a6d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a6d-122">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5a6d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5a6d-123">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5a6d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5a6d-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a6d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a6d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a6d-125">See also</span></span>

- [<span data-ttu-id="d5a6d-126">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a6d-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d5a6d-127">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5a6d-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="d5a6d-128">JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5a6d-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="d5a6d-129">ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5a6d-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
