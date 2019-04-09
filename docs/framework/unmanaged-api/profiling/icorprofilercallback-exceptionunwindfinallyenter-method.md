---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aebfc0d763fa1ea14c55a0c61fbf63db65fefe02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137871"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="6727e-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6727e-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="6727e-103">İşleme özel durumu geriye doğru izleme aşamasına giriyor profil oluşturucu bildirir bir `finally` belirtilen işlevinde yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6727e-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6727e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6727e-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6727e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6727e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6727e-106">[in] İçeren işlev kimliği `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6727e-106">[in] The ID of the function that contains the `finally` clause.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6727e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6727e-107">Remarks</span></span>  
 <span data-ttu-id="6727e-108">Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6727e-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="6727e-109">Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="6727e-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="6727e-110">Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="6727e-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6727e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6727e-111">Requirements</span></span>  
 <span data-ttu-id="6727e-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6727e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6727e-113">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6727e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6727e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6727e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6727e-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6727e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6727e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6727e-116">See also</span></span>

- [<span data-ttu-id="6727e-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6727e-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="6727e-118">GetNotifiedExceptionClauseInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6727e-118">GetNotifiedExceptionClauseInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="6727e-119">ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6727e-119">ExceptionUnwindFinallyLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
