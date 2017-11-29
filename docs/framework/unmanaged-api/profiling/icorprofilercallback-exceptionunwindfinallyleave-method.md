---
title: "ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf373872ada8364fe755162597dc9baf5c527f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="2a6d7-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a6d7-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>
<span data-ttu-id="2a6d7-103">Özel durum geriye doğru izleme aşaması işleme ayrıldı profil oluşturucu bildirir bir `finally` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2a6d7-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a6d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a6d7-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a6d7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a6d7-105">Remarks</span></span>  
 <span data-ttu-id="2a6d7-106">Çünkü yığın çöp toplama izin veren bir durumda olmayabilir profil oluşturucu bu çağrı sırasında engelleyin değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2a6d7-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="2a6d7-107">Profil Oluşturucu blokları buraya ve çöp toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="2a6d7-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="2a6d7-108">Ayrıca, bu çağrı sırasında profil oluşturucu yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalısınız değil.</span><span class="sxs-lookup"><span data-stu-id="2a6d7-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a6d7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a6d7-109">Requirements</span></span>  
 <span data-ttu-id="2a6d7-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a6d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a6d7-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a6d7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a6d7-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a6d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a6d7-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a6d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a6d7-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a6d7-114">See Also</span></span>  
 [<span data-ttu-id="2a6d7-115">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a6d7-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2a6d7-116">ExceptionUnwindFinallyEnter yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a6d7-116">ExceptionUnwindFinallyEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)
