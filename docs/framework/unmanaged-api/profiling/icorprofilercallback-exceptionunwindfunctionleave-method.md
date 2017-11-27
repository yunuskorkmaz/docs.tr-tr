---
title: "ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e420d27fa1bf122b794489b00853555a7005e69e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="b050c-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b050c-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="b050c-103">Profil Oluşturucu, özel durum işleme bırakma aşaması işlevi geriye doğru izleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="b050c-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b050c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b050c-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b050c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b050c-105">Remarks</span></span>  
 <span data-ttu-id="b050c-106">Zaman `ExceptionUnwindFunctionLeave` yöntemi çağrıldığında, işlev örneğini ve yığın verisini yığından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b050c-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="b050c-107">Çünkü yığın çöp toplama izin veren bir durumda olmayabilir profil oluşturucu bu çağrı sırasında engelleyin değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b050c-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b050c-108">Profil Oluşturucu blokları buraya ve çöp toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="b050c-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b050c-109">Ayrıca, bu çağrı sırasında profil oluşturucu yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalısınız değil.</span><span class="sxs-lookup"><span data-stu-id="b050c-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b050c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b050c-110">Requirements</span></span>  
 <span data-ttu-id="b050c-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b050c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b050c-112">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b050c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b050c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b050c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b050c-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b050c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b050c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b050c-115">See Also</span></span>  
 [<span data-ttu-id="b050c-116">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="b050c-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b050c-117">ExceptionUnwindFunctionEnter yöntemi</span><span class="sxs-lookup"><span data-stu-id="b050c-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
