---
title: ICorProfilerCallback::ExceptionCatcherLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7f1b2756dd180cb0a701429978a34ea80447a86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107646"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="570d9-102">ICorProfilerCallback::ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="570d9-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="570d9-103">Denetimi uygun dışında geçirilen profil oluşturucu bildirir `catch` blok.</span><span class="sxs-lookup"><span data-stu-id="570d9-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="570d9-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="570d9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="570d9-105">Remarks</span></span>  
 <span data-ttu-id="570d9-106">Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="570d9-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="570d9-107">Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="570d9-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="570d9-108">Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="570d9-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="570d9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="570d9-109">Requirements</span></span>  
 <span data-ttu-id="570d9-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="570d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="570d9-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="570d9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="570d9-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="570d9-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="570d9-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="570d9-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="570d9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="570d9-114">See also</span></span>

- [<span data-ttu-id="570d9-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="570d9-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="570d9-116">ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="570d9-116">ExceptionCatcherEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)
