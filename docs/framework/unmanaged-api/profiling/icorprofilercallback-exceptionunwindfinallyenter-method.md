---
title: "ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec1b05e67a10f5e7b22a950d1dec24528b5c4914
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="40a5c-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40a5c-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="40a5c-103">Özel durum geriye doğru izleme aşaması işleme girme profil oluşturucu bildirir bir `finally` belirtilen işlevinde yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="40a5c-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40a5c-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40a5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40a5c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="40a5c-106">[in] Kimliği içeren işlevinin `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="40a5c-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40a5c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40a5c-107">Remarks</span></span>  
 <span data-ttu-id="40a5c-108">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="40a5c-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="40a5c-109">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="40a5c-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="40a5c-110">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="40a5c-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40a5c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40a5c-111">Requirements</span></span>  
 <span data-ttu-id="40a5c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40a5c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40a5c-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="40a5c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40a5c-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40a5c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40a5c-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40a5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a5c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40a5c-116">See Also</span></span>  
 [<span data-ttu-id="40a5c-117">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="40a5c-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="40a5c-118">Getnotifiedexceptionclauseınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="40a5c-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [<span data-ttu-id="40a5c-119">ExceptionUnwindFinallyLeave yöntemi</span><span class="sxs-lookup"><span data-stu-id="40a5c-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
