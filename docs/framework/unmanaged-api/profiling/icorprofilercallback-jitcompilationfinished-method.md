---
description: ': ICorProfilerCallback:: JITCompilationFinished yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 32a47860ae2e973d32ef12b2bd9002bb1de45ee9
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760333"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="28008-103">ICorProfilerCallback::JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28008-103">ICorProfilerCallback::JITCompilationFinished Method</span></span>

<span data-ttu-id="28008-104">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemeyi tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="28008-104">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28008-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28008-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28008-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28008-106">Parameters</span></span>

<span data-ttu-id="28008-107">`functionId` 'ndaki Derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="28008-107">`functionId` [in] The ID of the function that was compiled.</span></span>

<span data-ttu-id="28008-108">`hrStatus` 'ndaki Derlemenin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="28008-108">`hrStatus` [in] A value indicating whether compilation was successful.</span></span>

<span data-ttu-id="28008-109">`fIsSafeToBlock` 'ndaki Profiler 'ın çalışma zamanının işlemini etkilemesinin ne olmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="28008-109">`fIsSafeToBlock` [in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="28008-110">Bu değer, `true` engelleme çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini, aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="28008-110">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

<span data-ttu-id="28008-111">Bir değeri `true` çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="28008-111">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="28008-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28008-112">Requirements</span></span>  

 <span data-ttu-id="28008-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28008-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28008-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="28008-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28008-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="28008-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28008-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28008-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28008-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28008-117">See also</span></span>

- [<span data-ttu-id="28008-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28008-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="28008-119">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="28008-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
