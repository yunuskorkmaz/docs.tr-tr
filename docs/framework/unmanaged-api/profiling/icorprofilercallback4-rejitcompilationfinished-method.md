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
ms.openlocfilehash: e010a49dabd3b44602136e70b4c5524a68bdd9e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865213"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="a7e6a-102">ICorProfilerCallback4::ReJITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7e6a-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>
<span data-ttu-id="a7e6a-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derleme işlemi tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e6a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7e6a-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7e6a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7e6a-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a7e6a-106">'ndaki Yeniden derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="a7e6a-107">'ndaki JıT-yeniden derleme işlevinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a7e6a-108">'ndaki JıT yeniden derlemenin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="a7e6a-109">[in] engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini sağlamak için `true`; engellemenin çalışma zamanının işlemini etkilemeyeceğini belirten `false`.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="a7e6a-110">`true` değeri çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e6a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7e6a-111">Requirements</span></span>  
 <span data-ttu-id="a7e6a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7e6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e6a-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7e6a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7e6a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7e6a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7e6a-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e6a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7e6a-116">See also</span></span>

- [<span data-ttu-id="a7e6a-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e6a-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a7e6a-118">ICorProfilerCallback4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7e6a-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="a7e6a-119">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7e6a-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="a7e6a-120">ReJITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7e6a-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
