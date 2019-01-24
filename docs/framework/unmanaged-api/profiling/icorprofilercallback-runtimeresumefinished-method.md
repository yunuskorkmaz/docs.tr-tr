---
title: ICorProfilerCallback::RuntimeResumeFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2cf80c7e02d706b0b00ea87aa62986107cdd6a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689750"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="a88e8-102">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a88e8-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="a88e8-103">Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacığı devam ediyor ve normal çalışmasına geri döndürdü bildirir.</span><span class="sxs-lookup"><span data-stu-id="a88e8-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a88e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a88e8-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a88e8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a88e8-105">Remarks</span></span>  
 <span data-ttu-id="a88e8-106">`RuntimeResumeFinished` Geri arama aynı iş parçacığı üzerinde gerçekleşmesi için garanti edilmez [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="a88e8-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="a88e8-107">Ancak, aynı iş parçacığında gerçekleşecek şekilde sağlanır [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="a88e8-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a88e8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a88e8-108">Requirements</span></span>  
 <span data-ttu-id="a88e8-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a88e8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a88e8-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a88e8-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a88e8-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a88e8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a88e8-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a88e8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a88e8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a88e8-113">See also</span></span>
- [<span data-ttu-id="a88e8-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a88e8-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
