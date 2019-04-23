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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ba62ab2c4df73b570fb1c76adaee44a2a2ce8c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117812"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="711b3-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="711b3-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="711b3-103">İşleme özel durumu geriye doğru izleme aşaması ayrıldı profil oluşturucu bildirir bir `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="711b3-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="711b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="711b3-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="711b3-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="711b3-105">Remarks</span></span>  
 <span data-ttu-id="711b3-106">Profil Oluşturucu bu çağrı sırasında engellemelisiniz, bu stack çöp toplama izin veren bir durumda olmayabilir çünkü değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="711b3-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="711b3-107">Profil Oluşturucu blokları burada ve çöp toplama denenir, çalışma zamanı bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="711b3-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="711b3-108">Ayrıca, yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden bu çağrı sırasında profil oluşturucu çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="711b3-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="711b3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="711b3-109">Requirements</span></span>  
 <span data-ttu-id="711b3-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="711b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="711b3-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="711b3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="711b3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="711b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="711b3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="711b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="711b3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="711b3-114">See also</span></span>

- [<span data-ttu-id="711b3-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="711b3-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="711b3-116">ExceptionUnwindFinallyEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="711b3-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
