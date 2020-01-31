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
ms.openlocfilehash: ab7c8cbc41967af04c4c9a8813f32b9b1f01c6a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866357"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="6f6c1-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f6c1-102">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>
<span data-ttu-id="6f6c1-103">Profil oluşturucuyu, özel durum işlemenin geriye doğru izleme aşamasının belirtilen işlevde içerilen bir `finally` yan tümcesi girdiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f6c1-103">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f6c1-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f6c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f6c1-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="6f6c1-106">\[içinde] `finally` yan tümcesini içeren işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6f6c1-106">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f6c1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f6c1-107">Remarks</span></span>  
 <span data-ttu-id="6f6c1-108">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6f6c1-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="6f6c1-109">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="6f6c1-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="6f6c1-110">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="6f6c1-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f6c1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f6c1-111">Requirements</span></span>  
 <span data-ttu-id="6f6c1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f6c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f6c1-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6f6c1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f6c1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f6c1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f6c1-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f6c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f6c1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f6c1-116">See also</span></span>

- [<span data-ttu-id="6f6c1-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f6c1-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6f6c1-118">GetNotifiedExceptionClauseInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f6c1-118">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="6f6c1-119">ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f6c1-119">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
