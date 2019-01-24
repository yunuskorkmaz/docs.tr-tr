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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1e945cad9080d14fff0b0a95c4e4d5f13981b1b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582291"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="34c18-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c18-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>
<span data-ttu-id="34c18-103">Profil Oluşturucu, özel durum işleme geriye doğru izleme aşaması bir işlevi geriye doğru izleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="34c18-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34c18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34c18-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="34c18-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34c18-105">Remarks</span></span>  
 <span data-ttu-id="34c18-106">Zaman `ExceptionUnwindFunctionLeave` yöntemi çağrıldığında, işlev örneği ve yığın verisini yığından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="34c18-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="34c18-107">Profil Oluşturucu bu çağrı sırasında engellemelisiniz, bu stack çöp toplama izin veren bir durumda olmayabilir çünkü değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="34c18-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="34c18-108">Profil Oluşturucu blokları burada ve çöp toplama denenir, çalışma zamanı bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="34c18-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="34c18-109">Ayrıca, yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden bu çağrı sırasında profil oluşturucu çağırmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="34c18-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34c18-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34c18-110">Requirements</span></span>  
 <span data-ttu-id="34c18-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34c18-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34c18-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34c18-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34c18-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34c18-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34c18-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34c18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34c18-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34c18-115">See also</span></span>
- [<span data-ttu-id="34c18-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34c18-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="34c18-117">ExceptionUnwindFunctionEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34c18-117">ExceptionUnwindFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)
