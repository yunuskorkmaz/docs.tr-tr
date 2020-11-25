---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: e02716350aa2bf32bdd7c4b2e01841405de6dc14
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720405"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="8071c-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8071c-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>

<span data-ttu-id="8071c-103">Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının bir `finally` yan tümce kaldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="8071c-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8071c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8071c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8071c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8071c-105">Remarks</span></span>  

 <span data-ttu-id="8071c-106">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu çağrı sırasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8071c-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8071c-107">Profil Oluşturucu burada ve bir çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="8071c-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8071c-108">Ayrıca, bu çağrı sırasında profil oluşturucunun yönetilen koda çağrı olmaması veya herhangi bir şekilde yönetilen bellek ayırmaya neden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8071c-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8071c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8071c-109">Requirements</span></span>  

 <span data-ttu-id="8071c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8071c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8071c-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8071c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8071c-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8071c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8071c-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8071c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8071c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8071c-114">See also</span></span>

- [<span data-ttu-id="8071c-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8071c-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8071c-116">ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8071c-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
