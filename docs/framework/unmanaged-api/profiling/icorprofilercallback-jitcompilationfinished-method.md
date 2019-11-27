---
title: ICorProfilerCallback::JITCompilationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 1bbdfa93913b9fdf8aa164c8ca6c35cd33a228df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449920"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="af1b6-102">ICorProfilerCallback::JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af1b6-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="af1b6-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemeyi tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="af1b6-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af1b6-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af1b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af1b6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="af1b6-106">'ndaki Derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="af1b6-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="af1b6-107">'ndaki Derlemenin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="af1b6-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="af1b6-108">'ndaki Profiler 'ın çalışma zamanının işlemini etkilemesinin ne olmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="af1b6-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="af1b6-109">Engelleme, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini neden olabileceğinden `true`. Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="af1b6-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="af1b6-110">`true` değeri çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="af1b6-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af1b6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af1b6-111">Requirements</span></span>  
 <span data-ttu-id="af1b6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af1b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af1b6-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="af1b6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af1b6-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="af1b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af1b6-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af1b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1b6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af1b6-116">See also</span></span>

- [<span data-ttu-id="af1b6-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af1b6-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="af1b6-118">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af1b6-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
