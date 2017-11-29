---
title: "ICorProfilerCallback::JITCompilationFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9719ce1474c2111692c6176655b75bd2d7edf923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="dd359-102">ICorProfilerCallback::JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd359-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="dd359-103">Profil Oluşturucu tam zamanında (JIT) derleyici bir işlev derleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dd359-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd359-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd359-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd359-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd359-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="dd359-106">[in] Derlenen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="dd359-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="dd359-107">[in] Derleme başarılı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="dd359-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="dd359-108">[in] Profil Oluşturucu için engelleme olup olmadığını belirten bir değer çalışma zamanının işlemi etkiler.</span><span class="sxs-lookup"><span data-stu-id="dd359-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="dd359-109">Değer `true` engelleme bu geri aramasından; döndürülecek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="dd359-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="dd359-110">Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarını eğme.</span><span class="sxs-lookup"><span data-stu-id="dd359-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd359-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd359-111">Requirements</span></span>  
 <span data-ttu-id="dd359-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd359-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd359-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd359-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd359-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd359-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd359-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd359-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd359-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd359-116">See Also</span></span>  
 [<span data-ttu-id="dd359-117">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd359-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dd359-118">Jıtcompilationstarted yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd359-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
