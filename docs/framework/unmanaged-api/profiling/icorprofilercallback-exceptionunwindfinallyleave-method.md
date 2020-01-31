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
ms.openlocfilehash: f53d1d66eef0f745e1a0c51c3234ac66eec07315
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866370"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="191b5-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="191b5-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="191b5-103">Profil oluşturucuyu, özel durum işlemenin geriye doğru izleme aşamasının bir `finally` yan tümcesi bıraktı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="191b5-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="191b5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="191b5-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="191b5-105">Remarks</span></span>  
 <span data-ttu-id="191b5-106">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu çağrı sırasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="191b5-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="191b5-107">Profil Oluşturucu burada ve bir çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="191b5-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="191b5-108">Ayrıca, bu çağrı sırasında profil oluşturucunun yönetilen koda çağrı olmaması veya herhangi bir şekilde yönetilen bellek ayırmaya neden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="191b5-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="191b5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="191b5-109">Requirements</span></span>  
 <span data-ttu-id="191b5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="191b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="191b5-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="191b5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="191b5-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="191b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="191b5-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="191b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191b5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="191b5-114">See also</span></span>

- [<span data-ttu-id="191b5-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="191b5-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="191b5-116">ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="191b5-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
