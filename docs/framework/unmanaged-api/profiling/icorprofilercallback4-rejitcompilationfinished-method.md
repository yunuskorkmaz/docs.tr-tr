---
title: ICorProfilerCallback4::ReJITCompilationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: a6c2209433a652523fd8e3a7cc2db1272600e1bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730272"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="6d6f7-102">ICorProfilerCallback4::ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d6f7-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="6d6f7-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derleme işlemi tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6f7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d6f7-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d6f7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d6f7-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="6d6f7-106">'ndaki Yeniden derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="6d6f7-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6d6f7-108">'ndaki JıT yeniden derlemenin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="6d6f7-109">[in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false` engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="6d6f7-110">Bir değeri `true` çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d6f7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d6f7-111">Requirements</span></span>  

 <span data-ttu-id="6d6f7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d6f7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6f7-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6d6f7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d6f7-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d6f7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d6f7-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d6f7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6f7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d6f7-116">See also</span></span>

- [<span data-ttu-id="6d6f7-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d6f7-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6d6f7-118">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d6f7-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="6d6f7-119">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d6f7-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="6d6f7-120">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d6f7-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
