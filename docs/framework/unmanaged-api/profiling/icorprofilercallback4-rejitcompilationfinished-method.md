---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback4:: ReJITCompilationFinished yöntemi'
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
ms.openlocfilehash: 2d7270b5a8cf31fd81505c148429da5f7025319a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788728"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="5e088-103">ICorProfilerCallback4::ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e088-103">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="5e088-104">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derleme işlemi tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e088-104">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e088-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e088-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e088-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e088-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="5e088-107">'ndaki Yeniden derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5e088-107">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="5e088-108">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="5e088-108">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="5e088-109">'ndaki JıT yeniden derlemenin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="5e088-109">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="5e088-110">[in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false` engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="5e088-110">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="5e088-111">Bir değeri `true` çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5e088-111">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e088-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e088-112">Requirements</span></span>  

 <span data-ttu-id="5e088-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e088-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e088-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e088-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e088-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5e088-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e088-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e088-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e088-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e088-117">See also</span></span>

- [<span data-ttu-id="5e088-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e088-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5e088-119">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e088-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="5e088-120">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e088-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="5e088-121">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e088-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
