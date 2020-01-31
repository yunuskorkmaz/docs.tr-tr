---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 9d3e39cd910240b965896f1b866b0c21de616a57
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866344"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="b435d-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b435d-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="b435d-103">Profil oluşturucuyu, özel durum işlemenin geri sarma aşamasının bir işlevi geriye doğru izlemeyi tamamladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b435d-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b435d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b435d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b435d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b435d-105">Remarks</span></span>  
 <span data-ttu-id="b435d-106">`ExceptionUnwindFunctionLeave` yöntemi çağrıldığında, işlev örneği ve yığın verileri yığından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b435d-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="b435d-107">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu çağrı sırasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b435d-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b435d-108">Profil Oluşturucu burada ve bir çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="b435d-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b435d-109">Ayrıca, bu çağrı sırasında profil oluşturucunun yönetilen koda çağrı olmaması veya herhangi bir şekilde yönetilen bellek ayırmaya neden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b435d-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b435d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b435d-110">Requirements</span></span>  
 <span data-ttu-id="b435d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b435d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b435d-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b435d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b435d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b435d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b435d-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b435d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b435d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b435d-115">See also</span></span>

- [<span data-ttu-id="b435d-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b435d-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b435d-117">ExceptionUnwindFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b435d-117">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
