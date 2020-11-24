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
ms.openlocfilehash: 46e1fccc40606e10d8ff4083c7fe51da711c039a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686130"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="9072f-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9072f-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>

<span data-ttu-id="9072f-103">Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının `finally` belirtilen işlevde içerilen bir yan tümce girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="9072f-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9072f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9072f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9072f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9072f-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9072f-106">\[içinde] yan tümcesini içeren işlevin KIMLIĞI `finally` .</span><span class="sxs-lookup"><span data-stu-id="9072f-106">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="9072f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9072f-107">Remarks</span></span>  

 <span data-ttu-id="9072f-108">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="9072f-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9072f-109">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="9072f-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9072f-110">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="9072f-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9072f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9072f-111">Requirements</span></span>  

 <span data-ttu-id="9072f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9072f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9072f-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9072f-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9072f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9072f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9072f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9072f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9072f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9072f-116">See also</span></span>

- [<span data-ttu-id="9072f-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9072f-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9072f-118">GetNotifiedExceptionClauseInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9072f-118">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="9072f-119">ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9072f-119">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
