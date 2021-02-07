---
description: ': ICorProfilerCallback:: Exceptioncatch Erleave yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 402a622dc949ef6f93c0ca5916a0690c6e734bd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706363"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="3f202-103">ICorProfilerCallback::ExceptionCatcherLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f202-103">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>

<span data-ttu-id="3f202-104">Profil oluşturucuyu denetimin uygun bloktan geçirilmekte olduğunu bildirir `catch` .</span><span class="sxs-lookup"><span data-stu-id="3f202-104">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f202-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3f202-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3f202-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f202-106">Remarks</span></span>  

 <span data-ttu-id="3f202-107">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="3f202-107">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="3f202-108">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="3f202-108">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="3f202-109">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="3f202-109">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f202-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f202-110">Requirements</span></span>  

 <span data-ttu-id="3f202-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f202-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f202-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3f202-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f202-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f202-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f202-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f202-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f202-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f202-115">See also</span></span>

- [<span data-ttu-id="3f202-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f202-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3f202-117">ExceptionCatcherEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f202-117">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
