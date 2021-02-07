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
ms.openlocfilehash: f0308bfb5f81d7305ab36acbb9144142232ef8c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705791"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="21dbe-103">ICorProfilerCallback::JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21dbe-103">ICorProfilerCallback::JITCompilationFinished Method</span></span>

<span data-ttu-id="21dbe-104">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemeyi tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="21dbe-104">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21dbe-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21dbe-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21dbe-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21dbe-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="21dbe-107">\[içinde] derlenen işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="21dbe-107">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="21dbe-108">\[' de] derlemenin başarılı olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="21dbe-108">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="21dbe-109">\[' de] bir profil oluşturucunun, engelleme çalışma zamanının işlemini etkilemesini isteyip olmayacağını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="21dbe-109">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="21dbe-110">Bu değer, `true` engelleme çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini, aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="21dbe-110">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="21dbe-111">Bir değeri `true` çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="21dbe-111">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="21dbe-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21dbe-112">Requirements</span></span>  

 <span data-ttu-id="21dbe-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21dbe-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21dbe-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="21dbe-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21dbe-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21dbe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21dbe-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21dbe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21dbe-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21dbe-117">See also</span></span>

- [<span data-ttu-id="21dbe-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21dbe-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="21dbe-119">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21dbe-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
