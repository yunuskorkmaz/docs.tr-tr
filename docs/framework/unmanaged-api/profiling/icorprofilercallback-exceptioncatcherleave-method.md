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
ms.openlocfilehash: 6b7aa7c60b5e861787d7a115d90a00d67cc48db0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866539"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="74b22-102">ICorProfilerCallback::ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74b22-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>
<span data-ttu-id="74b22-103">Profil oluşturucuyu denetimin uygun `catch` bloğundan geçirilmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="74b22-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74b22-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="74b22-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74b22-105">Remarks</span></span>  
 <span data-ttu-id="74b22-106">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="74b22-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="74b22-107">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="74b22-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="74b22-108">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="74b22-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b22-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74b22-109">Requirements</span></span>  
 <span data-ttu-id="74b22-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74b22-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b22-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="74b22-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74b22-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74b22-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74b22-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b22-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b22-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74b22-114">See also</span></span>

- [<span data-ttu-id="74b22-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74b22-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="74b22-116">ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74b22-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
