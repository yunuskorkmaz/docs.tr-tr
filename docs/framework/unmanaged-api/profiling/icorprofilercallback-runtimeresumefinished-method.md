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
ms.openlocfilehash: f6b983db7da258fb94f941d01914ece0f7b1359f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453313"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="41bdb-102">ICorProfilerCallback::RuntimeResumeFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41bdb-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="41bdb-103">Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını sürdürdü ve normal çalışmasına geri döndü bildirir.</span><span class="sxs-lookup"><span data-stu-id="41bdb-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bdb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41bdb-104">Syntax</span></span>  
  
```  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="41bdb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41bdb-105">Remarks</span></span>  
 <span data-ttu-id="41bdb-106">`RuntimeResumeFinished` Geri çağırma aynı iş parçacığı üzerinde gerçekleşmesi için garanti edilmez [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="41bdb-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="41bdb-107">Ancak, iş parçacığı gerçekleşecek şekilde sağlanır [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="41bdb-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41bdb-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41bdb-108">Requirements</span></span>  
 <span data-ttu-id="41bdb-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41bdb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41bdb-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41bdb-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41bdb-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41bdb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41bdb-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41bdb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bdb-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41bdb-113">See Also</span></span>  
 [<span data-ttu-id="41bdb-114">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41bdb-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
