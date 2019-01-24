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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d2e75d357b1f56df676163744015a1a3f77c17b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530764"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="8d235-102">ICorProfilerCallback::JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d235-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="8d235-103">Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi derleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="8d235-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d235-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d235-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d235-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d235-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8d235-106">[in] Derlenen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="8d235-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8d235-107">[in] Derleme başarılı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8d235-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="8d235-108">[in] Profil oluşturucuya engelleme olup olmadığını belirten bir değer çalışma zamanı işleyişini etkiler.</span><span class="sxs-lookup"><span data-stu-id="8d235-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="8d235-109">Değer `true` engelleme, bu geri çağrısından; döndürmek çağıran iş parçacığını beklemek çalışma zamanı neden olabilir, aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="8d235-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="8d235-110">Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarından eğriltilebilir.</span><span class="sxs-lookup"><span data-stu-id="8d235-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d235-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d235-111">Requirements</span></span>  
 <span data-ttu-id="8d235-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d235-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d235-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d235-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d235-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d235-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d235-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d235-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d235-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d235-116">See also</span></span>
- [<span data-ttu-id="8d235-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d235-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="8d235-118">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d235-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
